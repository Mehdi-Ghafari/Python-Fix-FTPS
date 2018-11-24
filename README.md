# Fix-FTPS

For the implicit FTP TLS/SSL(defualt port 990), our client program must build a TLS/SSL connection right after the socket is created. But python's class FTP_TLS doesn't reload the connect function from class FTP. We need to fix it

## Upload-file Function

Use the function `upload_file` for the test upload.

```python
upload_file(ftp_connection, upload_file_path)
```

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.


## License
[GPL Version 3](https://www.gnu.org/licenses/gpl-3.0.en.html/)