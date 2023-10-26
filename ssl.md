mkdir -p /marcelo/16_nginx/cfg
mkdir -p /marcelo/16_nginx/cert
cd /marcelo/16_nginx/cert

openssl req \
 -newkey rsa:4096 -nodes -sha256 -keyout 192.168.68.106.key \
 -x509 -days 365 -out 192.168.68.106.crt


docker run -it --rm --name=tmp -v /marcelo/16_nginx/cfg:/cfg nginx:1.21-alpine sh
cp /etc/nginx/* /cfg -R 
exit
sudo cp /marcelo/16_nginx/cfg/conf.d/default.conf /marcelo/16_nginx/cfg/conf.d/ssl.conf
