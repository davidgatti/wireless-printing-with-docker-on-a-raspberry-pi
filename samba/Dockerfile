#
# 	Base Image
#
FROM resin/rpi-raspbian

#
#	Basic Setup
#
MAINTAINER David Gatti "docker@gatti.pl"

#
#	Prepare the app by installing all the dependencies
#
RUN apt-get update && \
    apt-get upgrade && \
    apt-get install apt-utils && \
    apt-get install samba && \
    apt-get clean && \
    apt-get -y autoremove && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

#
#	Replace the default config file
#
COPY smb.conf /etc/samba/smb.conf

#
#
#
RUN mkdir -p /home/drivers
RUN mkdir -p /var/spool/samba && chmod 1777 /var/spool/samba/

#
#	Share the same dbus among all containers
#
RUN mkdir -p /var/run/dbus

#
#	Samba Port
#
EXPOSE 445

#
#	NetBIOS ports
#
EXPOSE 137/udp
EXPOSE 138/udp
EXPOSE 139

#
#	Run the app
#
CMD service smbd start && service nmbd start && tail -f /var/log/lastlog