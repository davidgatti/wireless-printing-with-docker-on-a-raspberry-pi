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
    apt-get install cups && \
    apt-get install hplip && \
    apt-get install hpijs-ppds && \
    apt-get install hp-ppd && \
    apt-get install printer-driver-all && \
    apt-get install openprinting-ppds && \
    apt-get clean && \
    apt-get -y autoremove && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

#
#	Add a Printer user
#
RUN useradd \
  	--groups=sudo,lp,lpadmin \
  	--create-home \
  	--home-dir=/home/print \
  	--shell=/bin/bash \
  	print && \
    echo print:sdsds | chpasswd

#
#	Replace the default config file
#
COPY cupsd.conf /etc/cups/cupsd.conf

#
#	Switch the working directory
#
WORKDIR /home/print

#
#	Expose the default port
#
EXPOSE 631

#
#	Run the app
#
CMD service cups start && tail -f /var/log/messages