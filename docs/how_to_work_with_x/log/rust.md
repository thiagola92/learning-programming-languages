# Rust

??? info "Official"

    Esta biblioteca é mantida pelos criadores oficiais da linguagem.

A biblioteca segue parcialmente o padrão [syslog](https://en.wikipedia.org/wiki/Syslog).  

A biblioteca é uma [facade](https://en.wikipedia.org/wiki/Facade_pattern), ou seja, apenas providência o front-end do logging. É necessária a implementação concreta do logger.  

## File

```rust
use log::{info, Log};
use std::{fs::OpenOptions, io::Write};

struct Logger;

impl Log for Logger {
    fn enabled(&self, metadata: &log::Metadata) -> bool {
        return true;
    }

    fn log(&self, record: &log::Record) {
        let msg: String = format!("{} - {}\n", record.level(), record.args());
        let mut file = OpenOptions::new()
            .create(true)
            .append(true)
            .open("example.log")
            .unwrap();

        file.write(msg.as_bytes()).unwrap();
    }

    fn flush(&self) {
        //
    }
}

fn main() {
    _ = log::set_logger(&Logger);
    log::set_max_level(log::LevelFilter::Info);
    info!("Example");
}
```

```
INFO - Example
```

!!! note

    Está implementação não é recomendada pois irá abrir o arquivo sempre que for escrever.  
    Uma recomendação seria abrir apenas uma vez e sempre ir adicionando texto ao arquivo.  

## Stderr

```rust
use log::info;

struct Logger;

impl log::Log for Logger {
    fn enabled(&self, metadata: &log::Metadata) -> bool {
        return true;
    }

    fn log(&self, record: &log::Record) {
        eprintln!("{} - {}", record.level(), record.args());
    }

    fn flush(&self) {
        //
    }
}

fn main() {
    _ = log::set_logger(&Logger);
    log::set_max_level(log::LevelFilter::Info);
    info!("Example");
}
```

```
INFO - Example
```