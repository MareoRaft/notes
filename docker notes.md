docker images --> list all images
docker ps --> list running containers
docker ps -a --> list all containers


docker pull --> pull an image from the internet



`docker run` --> create container from image and run it
`docker run -v $(pwd):/home/jovyan` --> mount host dir ("volume") . at docker container dir /home/jovyan
docker stop --> pause a running container
docker start --> resume a paused container
docker exec {cntner} {cmd} --> execute a command in a running container
docker exec -it {container} bash --> get a tty into the container! (or sh)






Dockerfile notes
-----------------------
# copy a file in
COPY host/computer/file.py /container/file.py
COPY host/computer/file.py /container/.

# first arg of '.' indicates entire directory
COPY . /container/dir

# second arg of '.' indicates '~/.' for each file

COPY . .







swarm tutorial:
https://docs.docker.com/engine/swarm/swarm-tutorial/
