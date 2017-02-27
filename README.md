# wireless-printing-with-docker-on-a-raspberry-pi

Convert any printer in to a wireless one.

# Docker build

git pull && \
docker stop cups || \
docker rm cups || \
docker build -t cups . && \
docker run -it -e CUPS_USER_ADMIN=admin -e CUPS_USER_PASSWORD=secr3t --name cups -p 631:631 cups