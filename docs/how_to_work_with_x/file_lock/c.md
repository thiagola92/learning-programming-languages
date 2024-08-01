# C

## Exclusive Lock

### flock

```C
#include <sys/file.h>

int main() {
    int fd = open("example.txt", O_RDWR);
    flock(fd, LOCK_EX);
    // ...
    flock(fd, LOCK_UN);
}
```

### lockf

```C
#include <sys/file.h>

int main() {
    int fd = open("example.txt", O_RDWR);
    lockf(fd, F_LOCK, 0);
    // ...
    lockf(fd, F_ULOCK, 0);
}
```

### fcntl "Advisory record locking"

```C
#include <sys/file.h>

int main() {
    int fd = open("example.txt", O_RDWR);
    struct flock fl;

    fl.l_whence = SEEK_SET;
    fl.l_start = 0;
    fl.l_len = 0;
    fl.l_type = F_WRLCK;

    fcntl(fd, F_SETLKW, &fl);
    // ...
    fl.l_type = F_UNLCK;
    fcntl(fd, F_SETLKW, &fl);
}
```

### fcntl "Open file description locks (non-POSIX)"

```C title="WIP"
#include <sys/file.h>

int main() {
    int fd = open("example.txt", O_RDWR);
    struct flock fl;

    fl.l_whence = SEEK_SET;
    fl.l_start = 0;
    fl.l_len = 0;
    fl.l_type = F_WRLCK;

    fcntl(fd, F_OFD_SETLKW, &fl);
    // ...
    fl.l_type = F_UNLCK;
    fcntl(fd, F_OFD_SETLKW, &fl);
}
```