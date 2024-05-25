# RabbitMQ-on-docker

## 1. Pull the RabbitMQ Image:

```
docker run -d --hostname my-rmq-service --name some-rabbit rabbitmq:3.13-management
```

## 2. Verify the RMQ Service:

```
docker ps
```

## RMQ config : 
### Configuration via Environment Variables
```
docker run -d -e RABBITMQ_DEFAULT_USER=myuser -e RABBITMQ_DEFAULT_PASS=strongpassword rabbitmq:3.13
```
abbitMQ exposes several environment variables that allow you to customize its behavior. Here are some common examples:

- RABBITMQ_DEFAULT_USER: Set the default username for RabbitMQ access (default: "guest").
- RABBITMQ_DEFAULT_PASS: Set the default password for RabbitMQ access (default: "guest").
- RABBITMQ_DEFAULT_VHOST: Set the default virtual host (default: "/").

## Configuration File Mounting  (Optional):\
#### For more complex configurations, you can create a custom rabbitmq.conf file on your host machine and mount it into the container. Here's a general guideline:

Create a rabbitmq.conf file with your desired configurations. Refer to the RabbitMQ configuration documentation https://www.rabbitmq.com/docs/configure for details on available options.
Run the Docker container mounting the configuration file:


```
docker run -d -v /path/to/your/rabbitmq.conf:/etc/rabbitmq/rabbitmq.conf rabbitmq:3.13
```
This command mounts the rabbitmq.conf file from your host machine (at /path/to/your/rabbitmq.conf) to the container's configuration location (/etc/rabbitmq/rabbitmq.conf).

## Important Notes:

- Using environment variables is generally recommended for simplicity.
- Mounting a configuration file offers more granular control but requires managing the file on your host machine.
- Make sure the user running the Docker container has read permissions for the mounted configuration file.
Remember to choose the method that best suits your needs and refer to the official RabbitMQ documentation for a complete list of available configuration options.



## to study : RMQ - Publishing a Message With Go to 
https://x-team.com/blog/set-up-rabbitmq-with-docker-compose/

