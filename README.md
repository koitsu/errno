# errno

`errno` is a Perl-based error code lookup utility very similar to
MySQL's
[perror](https://dev.mysql.com/doc/refman/5.7/en/perror.html)
utility, or FreeBSD 8.0-and-newer's
[perror](https://www.freebsd.org/cgi/man.cgi?perror)
utility, but with some added features.

It has no dependencies, instead relying on error codes and names
provided entirely from the built-in Perl
[Errno](https://perldoc.perl.org/Errno.html)
module.

If your OS offers some error codes which are not shown, then the
issue is with Perl/Errno and not this utility.

# Usage

Provide one or more error codes as arguments to the utility.
Invalid syntax or unknown error codes will emit an error to stdout
and will exit with a status of 1.

The `-l` (lowercase-ELL) or `--list` flag can be used to list all
known error codes and descriptions, including names (ex. ENOENT).
This flag 

The `-s` or `--short` flag can be used to omit `Error code XXX` and
error code names from output, making it behave similar to FreeBSD's
perror utility.

The `-h`, `--help`, or `-?` flag will display usage syntax.

# Examples

```
$ errno 9 4 13
Error code   9: Bad file descriptor (EBADF)
Error code   4: Interrupted system call (EINTR)
Error code  13: Permission denied (EACCES)

$ errno --short 4
Interrupted system call

$ errno --list | head -5
Error code   1: Operation not permitted (EPERM)
Error code   2: No such file or directory (ENOENT)
Error code   3: No such process (ESRCH)
Error code   4: Interrupted system call (EINTR)
Error code   5: Input/output error (EIO)

$ errno 12345 ; echo $?
ERROR: Error code 12345 unknown. Try using --list.
1
```

# License
errno is released under the 2-clause BSD license ("FreeBSD License") per [LICENSE](LICENSE).
