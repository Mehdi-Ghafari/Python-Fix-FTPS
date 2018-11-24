# Fix-FTPS

For the implicit FTP TLS/SSL(defualt port 990) - [FTPS](https://en.wikipedia.org/wiki/FTPS), our client program must build a TLS/SSL connection right after the socket is created. But python's class FTP_TLS doesn't reload the connect function from class FTP. We need to fix it.

This derived class reloads the connect function and builds a wrapper around the socket to TLS. After you successfully connect and login to FTP server, you need to call: ftp.prot_p() before executing any FTP command!

## Upload-file Function

Use the function `upload_file` for the test upload.

```python
upload_file(ftp_connection, upload_file_path)
```

## Test Program

I am write a Test Program, For Use this Program you need copy binary file to server and Extract with command ```tar xvf ftpsTest.tar.gz``` after extract file you used below example command to run program in terminal without need to python install:

```bash
./ftpsClass 172.25.205.37 990 testftp Zz123456 /home/ghaffari/ testUpload.txt /mahdi
```


## Useful URL
[ftplib — FTP protocol client](https://docs.python.org/3/library/ftplib.html#ftplib.FTP.transfercmd)

[How to convert a PFX to a seperate .key/.crt file](https://www.markbrilman.nl/2011/08/howto-convert-a-pfx-to-a-seperate-key-crt-file/)

[FTP_TLS Example](https://programtalk.com/python-examples/ftplib.FTP_TLS/)

[FTPES - Session Reuse Required](https://stackoverflow.com/questions/14659154/ftpes-session-reuse-required?lq=1)

[What’s the Difference? FTP, SFTP, and FTP/S](https://titanftp.com/2018/05/18/whats-the-difference-ftp-sftp-and-ftp-s/)

[What firewall ports do I need to open when using FTPS?](https://serverfault.com/questions/10807/what-firewall-ports-do-i-need-to-open-when-using-ftps)

[Connecting to 'Explicit FTP over TLS' in Python (??)](https://stackoverflow.com/questions/44057732/connecting-to-explicit-ftp-over-tls-in-python)

## ALL BUG
[python bug : python ftps "OSError: [Errno 0] Error"](https://www.google.com/search?client=firefox-b-ab&ei=68H3W9nkAdH4gQasnrvgCQ&q=python+ftps+%22OSError%3A+%5BErrno+0%5D+Error%22&oq=python+ftps+%22OSError%3A+%5BErrno+0%5D+Error%22&gs_l=psy-ab.3...232787.234738..234970...0.0..0.188.1936.0j12......0....1..gws-wiz.......0i71j0i7i30j0i30.r4O6FZGDi1c)

[python bug: FTP_TLS errors when use certain subcommands](https://bugs.python.org/issue31727)

[python bug: test_ftplib is failing with TLS 1.3](https://bugs.python.org/issue34391)

[python bug: ftplib: FTP_TLS seems to have problems](https://bugs.python.org/issue33122)

[python bug: Issue with ftplib.FTP_TLS and server forcing SSL connection reuse](https://bugs.python.org/issue25437)

[python bug: ftplib Add client-side SSL session resumption](https://bugs.python.org/issue19500)

[windows bug: 550 The supplied message is incomplete. The signature was not verified.](https://support.microsoft.com/en-gb/help/2888853/fix-the-supplied-message-is-incomplete-error-when-you-use-an-ftps-clie)

[windows bug: Unable to upload file with FTPS](https://support.plesk.com/hc/en-us/articles/213959085-Unable-to-upload-file-with-FTPS-550-The-supplied-message-is-incomplete-The-signature-was-not-verified)

[windows bug: Bug it IIS 8.0 Update to IIS 10.0 - Windows Server 2016](https://social.technet.microsoft.com/Forums/en-US/cc650ccd-9ab2-44a3-be52-5e0a9f93c61d/win8-clients-cant-write-over-ftps-to-win-2012-with-ftp-site-hosted-in-iis-8?forum=winserver8gen)



## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.


## License
[GPL Version 3](https://www.gnu.org/licenses/gpl-3.0.en.html/)
