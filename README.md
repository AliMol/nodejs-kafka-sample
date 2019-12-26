# Nodejs Kafka

## Objectives
The purpose of this article is implement a basic event sourcing app, with basic fault tolerance and clear guarantees (at-least-once, timeouts). There are other ready to go solutions out there for example: node-cqrs-domain, nestjs-cqrs, wolkenkit, but i decided to write something quick from scratch for learning purposes.

## Setup

Make sure you have following on your local machine installed
>   docker - 18.03.1
>   docker-compose - 1.21.1
>   node - 9.9.0
>   npm - 5.6.0

Install Project

    npm install
    docker-compose up

Create Kafka Topics

    docker run --rm -it --net=host landoop/fast-data-dev kafka-topics --zookeeper 127.0.0.1:2181 --topic requests --replication-factor 1 --partitions 100 --create
    docker run --rm -it --net=host landoop/fast-data-dev kafka-topics --zookeeper 127.0.0.1:2181 --topic finalevents --replication-factor 1 --partitions 100 --create

Kafka UI

   Visit http://127.0.0.1:3030 to inspect your kafka broker, topics, partitions etc.



## Usage

Terminal1: Start Consumer (you can start multiple in different terminals to spread the load)

    node consumer.js

Terminal2: Start API

    node api.js

Terminal3: Start CLI

    node cli.js

Start interacting with the CLI and observe what the API / Consumer does
