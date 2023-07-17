# Python3 OS file/directory method

**The os** module provides a very rich set of methods for working with files and directories. The commonly used methods are shown in the table below:

| serial number | Method and description                                       |
| :------------ | :----------------------------------------------------------- |
| 1             | [os. access(path, mode)](https://www.runoob.com/python3/python3-os-access.html) Check permission mode |
| 2             | [os. chdir(path)](https://www.runoob.com/python3/python3-os-chdir.html) change current working directory |
| 3             | [os. chflags(path, flags)](https://www.runoob.com/python3/python3-os-chflags.html) Sets the path's marker to a numeric marker. |
| 4             | [os.chmod(path, mode)](https://www.runoob.com/python3/python3-os-chmod.html) change permissions |
| 5             | [os. chown(path, uid, gid)](https://www.runoob.com/python3/python3-os-chown.html) change file owner |
| 6             | [os. chroot(path)](https://www.runoob.com/python3/python3-os-chroot.html) Change the root directory of the current process |
| 7             | [os. close(fd)](https://www.runoob.com/python3/python3-os-close.html) close file descriptor fd |
| 8             | [os.closerange(fd_low, fd_high)](https://www.runoob.com/python3/python3-os-closerange.html) close all file descriptors from fd_low (inclusive) to fd_high (exclusive), errors are ignored |
| 9             | [os.dup(fd)](https://www.runoob.com/python3/python3-os-dup.html) copy file descriptor fd |
| 10            | [os.dup2(fd, fd2)](https://www.runoob.com/python3/python3-os-dup2.html) copy a file descriptor fd to another fd2 |
| 11            | [os. fchdir(fd)](https://www.runoob.com/python3/python3-os-fchdir.html) Change the current working directory via a file descriptor |
| 12            | [os.fchmod(fd, mode)](https://www.runoob.com/python3/python3-os-fchmod.html) Change the access permission of a file specified by the parameter fd, and the parameter mode is the file access permission under Unix. |
| 13            | [os. fchown(fd, uid, gid)](https://www.runoob.com/python3/python3-os-fchown.html) Modify the ownership of a file, this function modifies the user ID and user group ID of a file specified by the file descriptor fd. |
| 14            | [os. fdatasync(fd)](https://www.runoob.com/python3/python3-os-fdatasync.html) Force the file to be written to disk, the file specified by the file descriptor fd, but do not force the state information of the file to be updated. |
| 15            | [os.fdopen(fd[, mode[, bufsize\]])](https://www.runoob.com/python3/python3-os-fdopen.html) Create a file object through the file descriptor fd and return this file object |
| 16            | [os.fpathconf(fd, name)](https://www.runoob.com/python3/python3-os-fpathconf.html) Returns system configuration information for an open file. name is the retrieved system configuration value, which may be a string defining the system value, these names are specified in many standards (POSIX.1, Unix 95, Unix 98, and others). |
| 17            | [os. fstat(fd)](https://www.runoob.com/python3/python3-os-fstat.html) Return the status of the file descriptor fd, like stat(). |
| 18            | [os.fstatvfs(fd)](https://www.runoob.com/python3/python3-os-fstatvfs.html) Returns information about the filesystem of the file containing file descriptor fd, Python 3.3 equivalent to statvfs(). |
| 19            | [os. fsync(fd)](https://www.runoob.com/python3/python3-os-fsync.html) Force the file with file descriptor fd to be written to disk. |
| 20            | [os. ftruncate(fd, length)](https://www.runoob.com/python3/python3-os-ftruncate.html) Crop the file corresponding to the file descriptor fd, so it cannot exceed the maximum file size. |
| twenty one    | [os. getcwd()](https://www.runoob.com/python3/python3-os-getcwd.html) return current working directory |
| twenty two    | [os. getcwdb()](https://www.runoob.com/python3/python3-os-getcwdb.html) Returns a Unicode object of the current working directory |
| twenty three  | [os.isatty(fd)](https://www.runoob.com/python3/python3-os-isatty.html) Returns true if the file descriptor fd is open and connected to a tty (-like) device, otherwise False. |
| twenty four   | [os. lchflags(path, flags)](https://www.runoob.com/python3/python3-os-lchflags.html) Set the flag of the path to a digital flag, similar to chflags(), but without soft links |
| 25            | [os.lchmod(path, mode)](https://www.runoob.com/python3/python3-os-lchmod.html) Modify connection file permissions |
| 26            | [os.lchown(path, uid, gid)](https://www.runoob.com/python3/python3-os-lchown.html) Change file owner, like chown, but does not follow links. |
| 27            | [os. link(src, dst)](https://www.runoob.com/python3/python3-os-link.html) Create a hard link, named parameter dst, pointing to parameter src |
| 28            | [os.listdir(path)](https://www.runoob.com/python3/python3-os-listdir.html) Returns a list of the names of the files or folders contained in the folder specified by path. |
| 29            | [os. lseek(fd, pos, how)](https://www.runoob.com/python3/python3-os-lseek.html) Set the current position of the file descriptor fd to pos, how to modify: SEEK_SET or 0 sets the calculated pos from the beginning of the file; SEEK_CUR or 1 calculates from the current position; os.SEEK_END or 2 starts from the end of the file. On Unix, Windows effective in |
| 30            | [os.lstat(path)](https://www.runoob.com/python3/python3-os-lstat.html) Like stat(), but without soft links |
| 31            | [os. major(device)](https://www.runoob.com/python3/python3-os-major.html) Extract the device major number from the original device number (using the st_dev or st_rdev field in stat). |
| 32            | [os.makedev(major, minor)](https://www.runoob.com/python3/python3-os-makedev.html) A raw device number is composed of major and minor device numbers |
| 33            | [os.makedirs(path[, mode\])](https://www.runoob.com/python3/python3-os-makedirs.html) Recursive folder creation function. Like mkdir(), but creates all intermediate-level folders that need to contain subfolders. |
| 34            | [os.minor(device)](https://www.runoob.com/python3/python3-os-minor.html) Extract the device minor number from the raw device number (using the st_dev or st_rdev field in stat). |
| 35            | [os.mkdir(path[, mode\])](https://www.runoob.com/python3/python3-os-mkdir.html) Create a folder named path in numeric mode. The default mode is 0777 (octal). |
| 36            | [os.mkfifo(path[, mode\])](https://www.runoob.com/python3/python3-os-mkfifo.html) Create a named pipe, the mode is a number, the default is 0666 (octal) |
| 37            | [os.mknod(filename[, mode=0600, device\])](https://www.runoob.com/python3/python3-os-mknod.html) Create a filesystem node (file, device special file or named pipe) named filename. |
| 38            | [os. open(file, flags[, mode\])](https://www.runoob.com/python3/python3-os-open.html) Open a file and set the required open options, the mode parameter is optional |
| 39            | [os. openpty()](https://www.runoob.com/python3/python3-os-openpty.html) Open a new pseudo-terminal pair. Return the file descriptors for pty and tty. |
| 40            | [os. pathconf(path, name)¶](https://www.runoob.com/python3/python3-os-pathconf.html) Returns system configuration information for the associated file. |
| 41            | [os. pipe()](https://www.runoob.com/python3/python3-os-pipe.html) Create a pipe. Return a pair of file descriptors (r, w) for reading and writing respectively |
| 42            | [os. popen(command[, mode[, bufsize\]])](https://www.runoob.com/python3/python3-os-popen.html) Open a pipe from a command |
| 43            | [os. read(fd, n)](https://www.runoob.com/python3/python3-os-read.html) Read up to n bytes from the file descriptor fd, return a string containing the read bytes, and return an empty string if the file descriptor fd corresponds to the end of the file. |
| 44            | [os. readlink(path)](https://www.runoob.com/python3/python3-os-readlink.html) Returns the file pointed to by the soft link |
| 45            | [os. remove(path)](https://www.runoob.com/python3/python3-os-remove.html) Delete the file with path path. If path is a directory, OSError will be thrown; see rmdir() below to delete a directory. |
| 46            | [os. removedirs(path)](https://www.runoob.com/python3/python3-os-removedirs.html) Delete directories recursively. |
| 47            | [os. rename(src, dst)](https://www.runoob.com/python3/python3-os-rename.html) Rename a file or directory from src to dst |
| 48            | [os.renames(old, new)](https://www.runoob.com/python3/python3-os-renames.html) Recursively rename directories and optionally files. |
| 49            | [os.rmdir(path)](https://www.runoob.com/python3/python3-os-rmdir.html) Delete the empty directory specified by path, or throw an OSError exception if the directory is not empty. |
| 50            | [os.stat(path)](https://www.runoob.com/python3/python3-os-stat.html) Get the information of the path specified by path, the function is equivalent to the stat() system call in the C API. |
| 51            | [os.stat_float_times([newvalue\])](https://www.runoob.com/python3/python3-os-stat_float_times.html) determines whether stat_result displays timestamps in float objects |
| 52            | [os.statvfs(path)](https://www.runoob.com/python3/python3-os-statvfs.html) Get the file system statistics information of the specified path |
| 53            | [os. symlink(src, dst)](https://www.runoob.com/python3/python3-os-symlink.html) Create a soft link |
| 54            | [os.tcgetpgrp(fd)](https://www.runoob.com/python3/python3-os-tcgetpgrp.html) Returns the process group associated with terminal fd (an open file descriptor returned by os.open()) |
| 55            | [os.tcsetpgrp(fd, pg)](https://www.runoob.com/python3/python3-os-tcsetpgrp.html) Set the process group associated with terminal fd (an open file descriptor returned by os.open()) to pg. |
| 56            | os. tempnam ([dir[, prefix]]) **Removed in Python3.** Return the unique pathname used to create the temporary file. |
| 57            | os.tmpfile() **Removed in Python3.** Returns an open file object with mode (w+b). This file object has no folder entry, no file descriptor, and will be automatically deleted. |
| 58            | os.tmpnam() **Removed in Python3.** Returns a unique path for creating a temporary file |
| 59            | [os.ttyname(fd)](https://www.runoob.com/python3/python3-os-ttyname.html) Returns a string representing the terminal device associated with file descriptor fd. Raises an exception if fd is not associated with a terminal device. |
| 60            | [os. unlink(path)](https://www.runoob.com/python3/python3-os-unlink.html) delete file path |
| 61            | [os.utime(path, times)](https://www.runoob.com/python3/python3-os-utime.html) Returns the access and modification times of the specified path file. |
| 62            | [os. walk(top[, topdown=True[, onerror=None[, followlinks=False\]]])](https://www.runoob.com/python3/python3-os-walk.html) Output filenames in folders by walking up or down the tree. |
| 63            | [os. write(fd, str)](https://www.runoob.com/python3/python3-os-write.html) Write a string to the file descriptor fd. Return the length of the actually written string |
| 64            | [os.path module](https://www.runoob.com/python3/python3-os-path.html) Get attribute information of a file. |
| 65            | [os. pardir()](https://www.runoob.com/python3/python3-os-pardir.html) Get the parent directory of the current directory, displaying the directory name as a string. |
| 66            | [os. replace()](https://www.runoob.com/python3/python3-os-replace.html) Rename a file or directory. |