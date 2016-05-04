## Troubleshooting

### Time synchronization issues

```
==> default: Makefile:599: recipe for target 'AtomicEditor' failed
==> default: jake aborted.
==> default: Error: make[3]: Warning: File 'Source/AtomicNET/NETJS/CMakeFiles/AtomicNETJS.dir/depend.make' has modification time 0.035 s in the future
==> default: make[3]: warning:  Clock skew detected.  Your build may be incomplete.
==> default: make[3]: Warning: File 'Source/AtomicPlayer/CMakeFiles/AtomicPlayerLib.dir/depend.make' has modification time 0.02 s in the future
==> default: (See full trace by running task with --trace)
```

One possible cause of this error may be that the host machine and guest machine clocks are not in sync:

```
$ vagrant ssh -- echo Guest:\;date; echo Host:;date
Guest:
Wed May  4 05:45:30 UTC 2016
Host:
Wed May  4 01:45:31 EDT 2016
```
A possible fix would be to install NTP on the host. The provisioning faze should have resulted in NTP being installed on the guest.

Arch Linux host: `pacman -Sy ntp`
Debian or Ubuntu host: `apt-get install ntpd`
