# C

??? info "Third Party"
    
    Está linguagem não inclue uma biblioteca de log oficial.  

## Syslog

Em sistemas operacionais que seguem os padrões POSIX, existe uma biblioteca para mandar mensagens ao logger do seus sistema operacional: [`syslog.h`](https://en.wikipedia.org/wiki/C_POSIX_library).  

!!! warning

    Estes logs ficaram misturados com logs de outros programas que usarem está biblioteca.  

### File

```C
#include <stdio.h>
#include <sys/syslog.h>

int main() {
  openlog(NULL, LOG_CONS, LOG_USER);
  syslog(LOG_INFO, "example");
  closelog();
}
```

```
2024-09-22T19:15:03.375012-03:00 username main.out: example
```

!!! note

    Em Linux, irá adicionar o log a um dos arquivos:  

    - `/var/log/syslog`
    - `/var/log/messages`

### Stderr

Opcionalmente podemos também mandar para `stderr` se utilizarmos `LOG_PERROR`.  

```C
#include <stdio.h>
#include <sys/syslog.h>

int main() {
  openlog(NULL, LOG_PERROR, LOG_USER);
  syslog(LOG_INFO, "example");
  closelog();
}
```

```
main.out: example
```

!!! note

    Não deixará de loggar em `/var/log/syslog` ou `/var/log/messages`.