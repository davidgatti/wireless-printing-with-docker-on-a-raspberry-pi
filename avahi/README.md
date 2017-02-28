git avahi && \
docker kill avahi && \
docker rm avahi && \
docker rmi avahi && \
docker build -t avahi . && \
echo -e "\a" && \
docker run -d --name avahi avahi