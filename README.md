# Download-files-using-AIOQUIC
To download a file using AIOQUIC library follow these below steps
1.Copy files from the folder(original files folder) and place  them in "/root/aioquic/examples/htdocs/" 
step1 must be done on machine which you want to run your server
[cp /var/www/html/test.pdf /root/aioquic/examples/htdocs/]
2.start the server by using "python examples/http3_server.py --certificate tests/ssl_cert.pem --private-key tests/ssl_key.pem -v"
3.go to client machine and download file using "python examples/http3_client.py --ca-certs tests/pycacert.pem https://server_ip:4433/test.pdf -v --outputdir /tmp/"
[downloaded file will be stored in /tmp/]
4.you will notice file will be downloaded and sha256um and original file contents and downloaded file also will be same

OR 
Another way is to

1.Open demo.py from "/root/aioquic/examples/demo.py"
2.Make changes in the line number "20" from "demo.py"
htdocs to location of files present in your machine
[ STATIC_ROOT = os.environ.get("STATIC_ROOT", os.path.join(ROOT, "htdocs"))] to [STATIC_ROOT = os.environ.get("STATIC_ROOT", os.path.join(ROOT, "/var/www/html/"))]
In my case all my files are present in /var/www/html,so i have changed from "htdocs" to "/var/www/html/"
This all changes must be done Server machine where your http3_server.py is running
[python examples/http3_server.py --certificate tests/ssl_cert.pem --private-key tests/ssl_key.pem -v]




Note:-Currently using "Ubuntu 20.04.4 LTS (GNU/Linux 5.4.0-113-generic x86_64)" terminal,"Python 3.8.10" version for running both http3_client.py and http3_server.py to download a file by using above scenario and Unable to create Multiple streams in a Single connection.
