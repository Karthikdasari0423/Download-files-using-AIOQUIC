# Download-file-using-AIOQUIC
To download a file using AIOQUIC library follow these below steps
1.Copy files from the folder(original files folder) and place  them in /root/aioquic/examples/htdocs/ 
step1 must be done on machine which you want to run your server
[cp /var/www/html/test.pdf /root/aioquic/examples/htdocs/]
2.start the server by using python examples/http3_server.py --certificate tests/ssl_cert.pem --private-key tests/ssl_key.pem -v
3.go to client machine and download file using python examples/http3_client.py --ca-certs tests/pycacert.pem https://server_ip:4433/test.pdf -v --outputdir /tmp/
[downloaded file will be stored in /tmp/]
4.you will notice file will be downloaded and sha256um and original file contents and downloaded file also will be same
