git avahi && \
docker kill avahi && \
docker rm avahi && \
docker rmi avahi && \
docker build -t avahi . && \
echo -e "\a" && \
docker run -d --name avahi -p 5353:5353/udp avahi