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
    apt-get install libnss-mdns && \
    apt-get install avahi-daemon && \
    apt-get -y autoclean && \
    apt-get -y autoremove && \
    apt-get -y clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

#
#
#
COPY avahi-daemon.conf /etc/avahi/avahi-daemon.conf

#
#	Services
#
COPY smb.service /etc/avahi/services/smb.service
COPY printer.service /etc/avahi/services/printer.service

#
#	Share the same dbus among all containers
#
RUN mkdir -p /var/run/dbus

#
#	Expose the default port
#
EXPOSE 5353/udp
EXPOSE 53791/udp

#
#	Run the app
#
CMD avahi-daemon --no-drop-root && tail -f /var/log/lastlog