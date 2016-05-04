.PHONY: run clean logs exec

name = cadvisor

image-name = google/cadvisor
image-version = latest
image = $(image-name):$(image-version)

ext-port = 50005
int-port = 8080

run:
	docker run \
		--volume=/:/rootfs:ro \
		--volume=/var/run:/var/run:rw \
		--volume=/sys:/sys:ro \
		--volume=/var/lib/docker/:/var/lib/docker:ro \
		--publish $(ext-port):$(int-port) \
		--detach=true \
		--name=$(name) \
		--restart=always \
		$(image)

clean:
	-docker stop $(name)
	-docker rm -v $(name)

logs:
	docker logs -f --tail=500 $(name)

exec:
	docker exec -it $(name) sh
