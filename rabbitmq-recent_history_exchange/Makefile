.PHONY: build run clean logs bash iter

image-name = rabbitmq-recent_history_exchange
container-name = rabbitmq
port = 5672
admin-port = 15672


build:
	docker build \
	-t $(image-name) \
	.

run:
	docker run \
	--name $(container-name) \
	-d \
	-p $(port):$(port) \
	-p $(admin-port):$(admin-port) \
	--restart=always \
	$(image-name)

clean:
	-docker stop $(container-name)
	-docker rm $(container-name)

logs:
	docker logs -f $(container-name)

bash:
	docker exec \
	-it \
	$(container-name) sh -c 'exec bash'

iter: clean build run logs
