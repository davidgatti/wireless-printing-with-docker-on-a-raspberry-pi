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
#
#
RUN useradd \
  	--groups=sudo,lp,lpadmin \
  	--create-home \
  	--home-dir=/home/print \
  	--shell=/bin/bash \
  	print

#
#
#
RUN echo print:sdsds | chpasswd

#
#	Copy the config file
#
COPY cupsd.conf /etc/cups/cupsd.conf

#
#	Copy the content of the app
#
COPY start.sh /home/print

#
#	Switch working directory
#
WORKDIR /home/print

#
#
#
RUN chmod +x start.sh

#
#
#
EXPOSE 631

#
#	Run the app
#
CMD service cups start && tail -f /var/log/faillog