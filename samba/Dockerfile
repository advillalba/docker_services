FROM debian
MAINTAINER advillalba
EXPOSE 137/udp 138/udp 139/tcp 445/tcp

ARG samba_user
ARG samba_password

VOLUME /shared

RUN apt update
RUN apt install samba -y
RUN apt install samba-client -y
RUN rm /etc/samba/smb.conf
COPY smb.conf /etc/samba/smb.conf
RUN mkdir /shared -p

RUN useradd -ms /bin/bash ${samba_user}
RUN (echo "${samba_password}"; echo "${samba_password}") | smbpasswd -s -a ${samba_user}

ENTRYPOINT /etc/init.d/smbd start && tail -f /dev/null