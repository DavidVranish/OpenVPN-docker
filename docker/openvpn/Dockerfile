FROM ubuntu

RUN apt-get update
RUN apt-get install -y apt-utils

RUN apt-get install -y openvpn \
    easy-rsa

RUN mkdir -p /root/bin
RUN mkdir -p /root/conf

COPY ./bin/start /root/bin
COPY ./bin/adduser /root/bin
COPY ./bin/rmuser /root/bin
COPY ./conf/server.ovpn /root/conf

RUN chmod +x /root/bin/start
RUN chmod +x /root/bin/adduser
RUN chmod +x /root/bin/rmuser

EXPOSE 1194

CMD /root/bin/start
