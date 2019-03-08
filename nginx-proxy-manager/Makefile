build: stop rm run

run: stop
	docker run -d \
		--name=nginx-proxy-manager \
		-p 8181:8181 \
		-p 8080:8080 \
		-p 4443:4443 \
		-v /docker/appdata/nginx-proxy-manager:/config:rw \
		jlesage/nginx-proxy-manager

stop:
	- docker stop nginx-proxy-manager

rm: stop
	- docker rm nginx-proxy-manager
