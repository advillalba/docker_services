FROM debian
MAINTAINER advillalba
EXPOSE 9091 51413/tcp 51413/udp

ARG transmision_password
ARG transmission_user

VOLUME /transmission/downloads

RUN apt update
RUN apt install transmission-daemon -y
RUN mkdir /transmission/downloads -p

RUN chown debian-transmission:debian-transmission /transmission -R

COPY settings.json /etc/transmission-daemon/settings.json
RUN sed -i "s/transmision_password/${transmision_password}/g" /etc/transmission-daemon/settings.json
RUN sed -i "s/transmission_user/${transmission_user}/g" /etc/transmission-daemon/settings.json


USER debian-transmission
ENTRYPOINT /etc/init.d/transmission-daemon start && tail -f /dev/null