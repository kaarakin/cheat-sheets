# Docker Cheat Sheet

skopeo copy --src-tls-verify=false docker: //busybox:latest docker-archive:busybox.tar
	download image as TAR

sudo docker images
	show images list

sudo usermod -aG docker SUSER
newgrp docker
	add user to docker group

docker load -i busybox. tan
	loading image from tar

docker tag $(docker images --filter "dangling-true" -q) busybox: latest
	assign repository and tag

docker tag busybox:local busybox:latest
	rename tag

docker rmi busybox:local
	delete

docker run busybox
	run container

docker run busybox echo "hello from busybox"
	run command inside the container

docker ps
	show current containers

docker ps -a
	show all

sudo docker run (--rm) -it busybox sh
	interactive tty (--m - auto delete)

docker rm 6Faa9533da56
	delete container by ID

docker rm $(docker ps -a -q -f status=exited)
	delete all exited containers (-q - digit ID, -f = filter)

docker rmi busybox
	delete image

docker run -d -P--name static-site-example prakhar1989-static-site
	(-d - detached terminal mode, -P - all open ports are random and public, --name - name of container)

docker port static-site-example
	show ports of container now you can open in browser

netstat -Intu
	shows available ports

docker stop (kill) ID
	stop/kill the container





--IMAGES -

TAG		- is snapshot of image (latest is default)
IMAGE ID 	- UID

Base and child images
