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
    apt-get install cups && \
    apt-get clean && \
    apt-get -y autoremove

#
#	Copy the config file
#
COPY cupsd.conf /etc/cups/cupsd.conf

#
#	Create app directory
#
RUN mkdir -p /home/cups

#
#	Copy the content of the app
#
COPY start.sh /home/cups

#
#	Switch working directory
#
WORKDIR /home/cups

RUN chmod +x start.sh

EXPOSE 631

#
#	Run the app
#
CMD ["top"]