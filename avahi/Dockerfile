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
    apt-get install avahi-daemon && \
    apt-get clean && \
    apt-get -y autoremove

#
#	Expose the default port
#
EXPOSE 5353 UDP

#
#	Run the app
#
CMD service avahi start && tail -f /var/log/faillog