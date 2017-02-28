# Wireless Printing With Docker On A Raspberry-PI

Convert any printer in to a wireless one.

# Docker build

git pull && \
docker tag cups cups:old
docker build -t cups . && \
docker kill cups && \
docker rm cups && \
docker rmi cups:old && \
echo -e "\a" && \
docker run -d --name cups -p 631:631 cups

