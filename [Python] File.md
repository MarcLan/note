# Python3 File(file) method

### open() method

The Python **open()** method is used to open a file and return a file object.

This function needs to be used in the process of processing the file. If the file cannot be opened, **OSError** will be thrown .

**Note:** When using **the open()** method, you must ensure that the file object is closed, that is, call **the close()** method.

**The common form of the open()** function is to receive two parameters: the file name (file) and the mode (mode).

```
open ( file , mode = 'r' )
```

The full syntax format is:

```
open ( file , mode = 'r' , buffering =- 1 , encoding = None , errors = None , newline = None , closefd = True , opener = None )
```

Parameter Description:

- file: Required, file path (relative or absolute path).
- mode: optional, file opening mode
- buffering: set buffering
- encoding: generally use utf8
- errors: error level
- newline: distinguish newline characters
- closefd: the incoming file parameter type
- opener: Set a custom opener, the return value of the opener must be an open file descriptor.

The mode parameters are:

| model | describe                                                     |
| :---- | :----------------------------------------------------------- |
| t     | Text mode (default).                                         |
| x     | Write mode, create a new file, if the file already exists, an error will be reported. |
| b     | binary mode.                                                 |
| +     | Open a file for update (readable and writable).              |
| u     | Universal newline mode ( **not supported in Python 3** ).    |
| r     | Open the file read-only. The file pointer will be placed at the beginning of the file. This is the default mode. |
| rb    | Open a file in binary format for reading only. The file pointer will be placed at the beginning of the file. This is the default mode. Generally used for non-text files such as pictures, etc. |
| r+    | Open a file for reading and writing. The file pointer will be placed at the beginning of the file. |
| rb+   | Open a file in binary format for reading and writing. The file pointer will be placed at the beginning of the file. Generally used for non-text files such as pictures, etc. |
| w     | Open a file for writing only. If the file already exists, the file will be opened and edited from the beginning, ie the original content will be deleted. If the file does not exist, create a new file. |
| wb    | Open a file in binary format for writing only. If the file already exists, the file will be opened and edited from the beginning, ie the original content will be deleted. If the file does not exist, create a new file. Generally used for non-text files such as pictures, etc. |
| w+    | Open a file for reading and writing. If the file already exists, the file will be opened and edited from the beginning, ie the original content will be deleted. If the file does not exist, create a new file. |
| wb+   | Open a file in binary format for reading and writing. If the file already exists, the file will be opened and edited from the beginning, ie the original content will be deleted. If the file does not exist, create a new file. Generally used for non-text files such as pictures, etc. |
| a     | Open a file for appending. If the file already exists, the file pointer will be placed at the end of the file. That is, the new content will be written after the existing content. If the file does not exist, a new file is created for writing. |
| ab    | Open a file in binary format for appending. If the file already exists, the file pointer will be placed at the end of the file. That is, the new content will be written after the existing content. If the file does not exist, a new file is created for writing. |
| a+    | Open a file for reading and writing. If the file already exists, the file pointer will be placed at the end of the file. The file will be opened in append mode. If the file does not exist, create a new file for reading and writing. |
| ab+   | Open a file in binary format for appending. If the file already exists, the file pointer will be placed at the end of the file. If the file does not exist, create a new file for reading and writing. |

Defaults to text mode, add **b** if you want to open in binary mode .

### file object

The file object is created using the open function. The following table lists the commonly used functions of the file object:

| serial number | Method and description                                       |
| :------------ | :----------------------------------------------------------- |
| 1             | [file. close()](https://www.runoob.com/python3/python3-file-close.html)Close the file. After closing, the file can no longer be read or written. |
| 2             | [file. flush()](https://www.runoob.com/python3/python3-file-flush.html)Refresh the internal buffer of the file, directly write the data in the internal buffer to the file immediately, instead of passively waiting for the output buffer to be written. |
| 3             | [file. fileno()](https://www.runoob.com/python3/python3-file-fileno.html)Returns an integer file descriptor (file descriptor FD integer), which can be used in some low-level operations such as the read method of the os module. |
| 4             | [file. isatty()](https://www.runoob.com/python3/python3-file-isatty.html)Return True if the file is attached to a terminal device, False otherwise. |
| 5             | [file. next()](https://www.runoob.com/python3/python3-file-next.html)**File objects in Python 3 do not support a next() method.**Returns the next line in the file. |
| 6             | [file. read([size\])](https://www.runoob.com/python3/python3-file-read.html)Reads the specified number of bytes from the file, or all if not given or negative. |
| 7             | [file. readline([size\])](https://www.runoob.com/python3/python3-file-readline.html)Read the entire line, including the "\n" characters. |
| 8             | [file. readlines([sizeint\])](https://www.runoob.com/python3/python3-file-readlines.html)Read all rows and return a list. If sizeint>0 is given, rows whose sum is about sizeint bytes are returned. The actual read value may be larger than sizeint because the buffer needs to be filled. |
| 9             | [file.seek(offset[, whence\])](https://www.runoob.com/python3/python3-file-seek.html)Move the file read pointer to the specified position |
| 10            | [file. tell()](https://www.runoob.com/python3/python3-file-tell.html)Returns the current position of the file. |
| 11            | [file.truncate([size\])](https://www.runoob.com/python3/python3-file-truncate.html)Truncated from the first character of the first line of the file, the truncated file is size characters, no size means truncated from the current position; after truncated, all subsequent characters are deleted, and the newline under the windows system represents the size of 2 characters. |
| 12            | [file. write(str)](https://www.runoob.com/python3/python3-file-write.html)Write a string to a file, and return the length of characters written. |
| 13            | [file. writelines(sequence)](https://www.runoob.com/python3/python3-file-writelines.html)Write a list of sequence strings to the file, and add a newline character for each line if a newline is required. |