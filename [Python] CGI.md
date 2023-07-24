# Python CGI

## What is CGI

CGI (Common Gateway Interface), common gateway interface, it is a program, running on the server such as: HTTP server, providing the interface with the client HTML page.



## Web browsing

To better understand how CGI works, we can start with the process of clicking a link or URL on a web page:

- Use your browser to visit the URL and connect to the HTTP web server.
- After receiving the request information, the web server will parse the URL and check whether the accessed file exists on the server. If there is, the content of the file is returned, otherwise an error message is returned.
- The browser receives information from the server and displays received files or error messages.



## CGI Architecture

![image-20230724174734561](https://raw.githubusercontent.com/MarcLan/pic/main/image-20230724174734561.png)



## Web server support and configuration

Before you start CGI programming, make sure your Web server supports CGI and has been configured with a CGI handler. Apache supports CGI configurations: Set up the CGI directory:

```python
ScriptAlias /cgi-bin/ /var/www/cgi-bin/
```

All HTTP server implementations of CGI programs are stored in a pre-configured directory. This directory is known as the CGI directory, and by convention it is named /var/www/cgi-bin. CGI files have a .cgi extension, and python can also use a .py extension. By default, the cgi-bin directory where the Linux server is configured to run is /var/www. If you want to specify other directories to run CGI scripts, you can modify the httpd.conf configuration file as follows:

```python
<Directory "/var/www/cgi-bin">
   AllowOverride None
   Options +ExecCGI
   Order allow,deny
   Allow from all
</Directory>
```

Add a .py suffix to AddHandler so we can access python script files ending in .py:

```python
AddHandler cgi-script .cgi .pl .py
```



## For programming check: https://www.runoob.com/python3/python3-cgi-programming.html



















