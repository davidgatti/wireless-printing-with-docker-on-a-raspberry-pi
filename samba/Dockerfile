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

#
#	Expose the default port
#
EXPOSE 139
EXPOSE 445

#
#	Run the app
#
CMD service samba start && tail -f /var/log/faillog