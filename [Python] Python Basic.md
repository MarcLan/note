# Python Basic

## Python Introduction

### Python  History

- Christmas 1989: Guido von Rossum starts writing a compiler for the Python language.
- February 1991: The first Python compiler (also an interpreter) was born, which was implemented in C language (later), and can call library functions in C language. In the earliest version, Python has provided support for building blocks such as "classes", "functions", and "exception handling", as well as core data types such as lists and dictionaries, and supports building applications based on modules .s

- January 1994: Python 1.0 is officially released.
- October 16, 2000: Python 2.0 was released, adding full garbage collection and providing support for Unicode. At the same time, the entire development process of Python has become more transparent, the influence of the community on the development progress has gradually expanded, and the ecological circle has gradually formed.
- December 3, 2008: Python 3.0 was released, it is not fully compatible with the previous Python code, but because there are still many companies using Python 2.x version in projects and operation and maintenance, so many new Python 3.x The feature was later ported to Python 2.6/2.7 as well.
- The version of Python 3.7.x that I am currently using was released in 2018. The version number of Python is divided into three sections, like A.B.C. Among them, A represents the major version number. Generally, A is added when the overall rewrite or incompatible changes occur; B represents a function update, and B is added when a new function appears; C represents a small change (for example: repairing a certain Bug), add C as long as there is a modification. If you are interested in the history of Python, you can read an online article called "A Brief History of Python".

### Advantages and Disadvantages of Python

#### Advantages

- Simple and clear, with a low learning curve, it is easier to learn than many programming languages.
- Open source, with a strong community and ecosystem, especially in the fields of data analysis and machine learning.
- An interpreted language is inherently platform-portable, and the code can work on different operating systems.
- Both major programming paradigms (object-oriented programming and functional programming) are supported.
- The code is highly standardized and readable, and is suitable for people with code cleanliness and obsessive-compulsive disorder.

#### Disadvantages

- The execution efficiency is slightly lower, and the parts that require high execution efficiency can be written in other languages (such as: C, C++).
- The code cannot be encrypted, but now many companies do not sell software but sell services, this problem will be weakened.
  There are too many frameworks to choose during development (for example, there are more than 100 web frameworks), and where there are choices, there will be mistakes.

#### Applications of Python

At present, Python is widely used in the fields of web application back-end development, cloud infrastructure construction, DevOps, network data collection (crawler), automated testing, data analysis, machine learning, etc.

### Install the Python interpreter

#### windows

You can download the Python Windows installer (exe file) from the Python official website. It should be noted that if you install Python 3.x in the Windows 7 environment, you need to install the Service Pack 1 patch package first (you can automatically install the system through some tool software patch function to install), during the installation process, it is recommended to check "Add Python 3.x to PATH" (add Python 3.x to the PATH environment variable) and select custom installation, it is best to set "Optional Features" in the "Optional Features" interface Check all items such as pip", "tcl/tk", and "Python test suite". It is strongly recommended to choose a custom installation path and ensure that there is no Chinese in the path. After the installation is complete, you will see a "Setup was successful" prompt. If there is a problem that the Python interpreter cannot work due to the lack of some dynamic link library files when running the Python program later, you can solve it according to the following method.

If the system displays that the api-ms-win-crt*.dll file is missing, you can refer to the method explained in the article "Api-ms-win-crt*.dll missing cause analysis and solution" or directly download Visual C++ from Microsoft's official website Redistributable for Visual Studio 2015 files to repair; if some dynamic link library files are missing after updating Windows DirectX, you can download a DirectX repair tool to repair.

#### Linux

The Linux environment comes with Python 2.x version, but if you want to update to 3.x version, you can download the source code of Python from the official website of Python and install it by building and installing the source code. The specific steps are as follows (Take CentOS as an example).

- Install dependent libraries (because without these dependent libraries may fail due to missing underlying dependent libraries when source code artifact installation)

  ```
  yum -y install wget gcc zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gdbm-devel db4-devel libpcap-devel xz-devel libffi-devel
  ```

- Download the Python source code and extract it to the specified directory.

  ```
  wget https://www.python.org/ftp/python/3.7.6/Python-3.7.6.tar.xz
  xz -d Python-3.7.6.tar.xz
  tar -xvf Python-3.7.6.tar
  ```

- Switch to the Python source code directory and execute the following commands to configure and install.

  ```
  cd Python-3.7.6
  ./configure --prefix=/usr/local/python37 --enable-optimizations
  make && make install
  ```

- Modify the file named .bash_profile in the user's home directory, configure the PATH environment variable and make it take effect.

  ```
  cd ~
  vim .bash_profile
  export PATH=$PATH:/usr/local/python37/bin
  ```

- Activate environment variables.

  ```
  source .bash_profile
  ```

### Python Development  Tools

- IDLE
- IPython
- Sublime Text
- [PyCharm](https://github.com/jackfrued/Python-100-Days/blob/master/%E7%95%AA%E5%A4%96%E7%AF%87/%E7%8E%A9%E8%BD%ACPyCharm.md)

