git pull && \
docker kill samba && \
docker rm samba && \
docker rmi samba && \
docker build -t samba . && \
echo -e "\a" && \
docker run -d --name samba -p 139:139 -p 445:445 samba