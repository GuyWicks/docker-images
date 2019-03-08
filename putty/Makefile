.SILENT:

.PHONEY:

.DEFAULT: run

pull:
	docker pull jlesage/putty

run: stop
	docker run -d \
		--restart always \
    		--name=putty \
    		-p 5800:5800 \
    		-v /docker/appdata/putty:/config:rw \
    		jlesage/putty

stop:
	- docker stop putty
	- docker rm putty
