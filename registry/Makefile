.PHONY: run clean logs exec

name = $(image-name)

image-name = registry
image-version = latest
image = $(image-name):$(image-version)

ext-port = 5000
int-port = 5000
data-dir = /container/$(name)

run:
	docker run \
		-d \
		-p $(ext-port):$(int-port) \
		-v $(data-dir):/var/lib/registry \
		--restart=always \
		--name=$(name) \
		$(image)

clean:
	-docker stop $(name)
	-docker rm -v $(name)

logs:
	docker logs -f --tail=500 $(name)

exec:
	docker exec -it $(name) sh
