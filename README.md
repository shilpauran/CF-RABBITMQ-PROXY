# CF RabbitMQ Enterprise Proxy

This small proxy app helps you to make your RabbitMQ Enterprise dashboard from a Swisscom Application Cloud [RabbitMQ instance](https://docs.developer.swisscom.com/service-offerings/rabbitmqent.html) publicly available. For it to work, the app needs to be bound to your RabbitMQ service instance.

## How to use - Method 1

1. Clone this repo
1. Change the `host` in `manifest.yml` to something that isn't taken yet
1. Change the entry in `services` in `manifest.yml` from `rabbitmq-ent` to the name of your RabbitMQ instance in Cloud Foundry
1. Run `cf push`

This proxy is a copy of the [CF Kibana Proxy](https://github.com/swisscom/cf-kibana-proxy) with adjustments for RabbitMQ Enterprise. 

## How to use - Method 2 - by Command Line

First you'll need an application binded to your RabbitMQ with SSH enabled see [cf enable-ssh](https://cli.cloudfoundry.org/en-US/cf/enable-ssh.html)

1. Run `cf env your-application`
2. Take not of rabbitmq.credentials.host and rabbitmq.credentials.port
3. Run `cf ssh your-application -L local-port:rabbitmq.credentials.host:rabbitmq.credentials.port`

Example: `cf ssh tax-maestro -L 8080:10.11.184.227:15672`

This will open the RabbitMQ Management on your localhost:8080
