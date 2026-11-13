# POSIX & BSD System Headers (`include/sys`)

## Overview
Provides the standard POSIX, System V, and BSD `<sys/*.h>` system call, data structure, and kernel interface headers for NuttX, covering fundamental system types (`types.h`), sockets (`socket.h`, `un.h`, `sockio.h`, `vm_sockets.h`), VFS/file operations (`stat.h`, `statfs.h`, `statvfs.h`, `vfs.h`, `fcntl.h`, `file.h`, `ioctl.h`, `mount.h`, `uio.h`, `sendfile.h`, `inotify.h`, `custom_file.h`), event multiplexing (`select.h`, `poll.h`, `epoll.h`, `eventfd.h`, `timerfd.h`, `signalfd.h`), process/resource control (`wait.h`, `resource.h`, `prctl.h`, `utsname.h`, `sysinfo.h`, `gmon.h`), memory management (`mman.h`, `shm.h`, `ipc.h`, `msg.h`, `sem.h`), timekeeping (`time.h`, `times.h`, `timex.h`), Video4Linux2 (`videoio.h`, `video_controls.h`), board/PCI control (`boardctl.h`, `pciio.h`), syscall tables (`syscall.h`, `syscall_lookup.h`), and intrusive data structures (`queue.h`, `tree.h`, `tree_type.h`).

## Interface
- Fundamental Types & Macros: `types.h:size_t`, `types.h:ssize_t`, `types.h:pid_t`, `types.h:off_t`, `types.h:mode_t`, `types.h:uid_t`, `types.h:gid_t`, `types.h:dev_t`, `endian.h:htobe16`, `endian.h:htole32`, `endian.h:be64toh`, `param.h:MIN`, `param.h:MAX`, `param.h:CLAMP`, `param.h:nitems`, `sysmacros.h:major`, `sysmacros.h:minor`, `sysmacros.h:makedev`.
- Sockets & Networking: `socket.h:sockaddr`, `socket.h:sockaddr_storage`, `socket.h:msghdr`, `socket.h:cmsghdr`, `socket.h:socket`, `socket.h:bind`, `socket.h:connect`, `socket.h:listen`, `socket.h:accept`, `socket.h:send`, `socket.h:recv`, `socket.h:setsockopt`, `socket.h:getsockopt`, `un.h:sockaddr_un`, `sockio.h:IMSFNAMSIZ`, `vm_sockets.h:sockaddr_vm`, `vm_sockets.h:VMADDR_CID_ANY`, `vm_sockets.h:VMADDR_CID_HOST`, `vm_sockets.h:VMADDR_CID_LOCAL`.
- Filesystem & I/O: `stat.h:stat`, `stat.h:mkdir`, `stat.h:mkfifo`, `stat.h:mknod`, `stat.h:chmod`, `stat.h:fstat`, `statfs.h:statfs`, `statvfs.h:statvfs`, `mount.h:mount`, `mount.h:umount2`, `uio.h:iovec`, `uio.h:readv`, `uio.h:writev`, `sendfile.h:sendfile`, `ioctl.h:ioctl`, `file.h:flock`, `inotify.h:inotify_init`, `inotify.h:inotify_add_watch`.
- Multiplexed I/O & Event Descriptors: `select.h:fd_set`, `select.h:select`, `select.h:pselect`, `poll.h:pollfd`, `poll.h:poll`, `poll.h:ppoll`, `epoll.h:epoll_event`, `epoll.h:epoll_create1`, `epoll.h:epoll_ctl`, `epoll.h:epoll_wait`, `eventfd.h:eventfd`, `timerfd.h:timerfd_create`, `timerfd.h:timerfd_settime`, `signalfd.h:signalfd`.
- Memory, IPC & Processes: `mman.h:mmap`, `mman.h:munmap`, `mman.h:mprotect`, `mman.h:shm_open`, `mman.h:shm_unlink`, `shm.h:shmget`, `shm.h:shmat`, `msg.h:msgget`, `msg.h:msgsnd`, `ipc.h:ftok`, `wait.h:waitpid`, `wait.h:waitid`, `resource.h:rlimit`, `resource.h:getrlimit`, `resource.h:setrlimit`, `prctl.h:prctl`, `utsname.h:uname`, `sysinfo.h:sysinfo`, `random.h:getrandom`.
- Timekeeping: `time.h:timeval`, `time.h:itimerval`, `time.h:gettimeofday`, `time.h:settimeofday`, `time.h:setitimer`, `times.h:tms`, `times.h:times`, `timex.h:timex`, `timex.h:clock_adjtime`.
- Video4Linux2 (`V4L2`): `videoio.h:v4l2_capability`, `videoio.h:v4l2_format`, `videoio.h:v4l2_buffer`, `videoio.h:v4l2_requestbuffers`, `videoio.h:VIDIOC_QUERYCAP`, `videoio.h:VIDIOC_S_FMT`, `videoio.h:VIDIOC_QBUF`, `videoio.h:VIDIOC_DQBUF`, `video_controls.h:V4L2_CID_BRIGHTNESS`.
- Board Control, Syscalls & Containers: `boardctl.h:boardctl`, `boardctl.h:BOARDIOC_INIT`, `boardctl.h:BOARDIOC_RESET`, `boardctl.h:BOARDIOC_POWEROFF`, `pciio.h:pci_io`, `pciio.h:PCIOCREAD`, `syscall.h:SYS_nsyscalls`, `queue.h:SLIST_HEAD`, `queue.h:LIST_HEAD`, `queue.h:TAILQ_HEAD`, `queue.h:CIRCLEQ_HEAD`, `tree.h:SPLAY_PROTOTYPE`, `tree.h:RB_PROTOTYPE`, `tree_type.h:RB_HEAD`.

## Invariants
- File descriptor sets manipulated via `select.h:FD_SET`, `select.h:FD_CLR`, and `select.h:FD_ISSET` require descriptor numbers in the range `0 <= fd < FD_SETSIZE`.
- `syscall.h` and `syscall_lookup.h` must keep kernel/user syscall indices (`SYS_*`) synchronized with the order of `SYSCALL_LOOKUP` entries when `CONFIG_LIB_SYSCALL` is enabled.

## Side Effects
- System call declarations in `include/sys` (`socket.h:socket`, `mman.h:mmap`, `mount.h:mount`, `boardctl.h:boardctl`, `ioctl.h:ioctl`, `wait.h:waitpid`, `time.h:settimeofday`) trap into kernel mode (in protected/kernel builds) or invoke kernel services that mutate process descriptors, virtual memory mappings, filesystem mounts, network sockets, and hardware state.

## Verification
- Run: `make test`
