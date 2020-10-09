.SILENT:

.PHONEY:

.DEFAULT: help

help:

run:
	docker run --name portainer -d -p 9000:9000 --restart always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer

rebuild: run
	- docker stop portainer
	- docker rm -f portainer
	- docker pull portainer/portainer
	#docker run --name portainer -d -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer

