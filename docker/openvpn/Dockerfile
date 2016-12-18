FROM ubuntu

RUN apt-get update
RUN apt-get install -y apt-utils

RUN apt-get install -y openvpn \
    easy-rsa

RUN mkdir -p /data/conf/openvpn
RUN mkdir -p /data/keys/openvpn
RUN mkdir -p /data/logs/openvpn

COPY ./start /data
COPY ./adduser /data
COPY ./rmuser /data
COPY ./server.ovpn /data/conf/openvpn

RUN chmod +x /data/start
RUN chmod +x /data/adduser
RUN chmod +x /data/rmuser

EXPOSE 1194

CMD /data/start