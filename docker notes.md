essential docker
----------------

docker images --> list all images
docker ps --> list running containers
docker ps -a --> list all containers


docker push {imagename}  -->  push an image to docker hub.  Make sure image name starts with 'mvlancellotti/'
docker pull --> pull an image from the internet



`docker run --rm` --> create container from image and run it
`docker run --rm -v $(pwd):/home/jovyan` --> mount host dir ("volume") . at docker container dir /home/jovyan
docker run -it -v ~/jobs/apps-by-company/meta/code-challenges:/home --rm python:3.7-slim python /home/largest_triple_products.py --> example of using docker python to execute local script instead of using local python installation
docker stop --> pause a running container
docker rm $(docker ps --filter "status=exited" -q) --> remove all stopped containers
docker rmi {image} --> remove image
docker image prune --> interactively remove dangling images
docker rmi -f $(docker images -aq) --> force remove all images
docker start --> resume a paused container
docker exec {cntner} {cmd} --> execute a command in a running container
docker exec -it {container} bash --> get a tty into the container! (or sh)





docker commit {containername} {imagename} --> create image out of current container state.
docker login --> login to docker.com / docker hub / Nexus, so that you can pull/push images from/to it

# logging!
docker logs --tail=50 {container} --> fetch logs for your application!
docker logs --follow {container} --> get logs that automatically update





advanced docker
---------------
:

    # tag a docker image
    docker tag <image id or tag> <new tag>
    docker tag mvlancellotti/tennis:prod mvlancellotti/tennis:prod-2021-01-01





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




Docker Compose notes
-------------------------
docker-compose.yml specification: https://github.com/compose-spec/compose-spec/blob/master/build.md
