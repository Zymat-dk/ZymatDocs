---
layout: default
title: How to run?
parent: Docker
nav_order: 1
---
# How to run?
The application is dockerized and therefore running the application must be done through docker. The application first needs to be built. This builds the Django code and Tailwind. Some of the code can be changed while the container is running, and will apply in realtime. 
```bash
docker compose up --build
```
To run the following times (use `-d` to run in deamon mode):
```bash
docker compose up -d
```

First time running the application locally, the database needs to be setup. This can be done as follows:
```bash
./run manage migrate
```
This only works in Linux machines or WSL. The `run` bash script is used for multiple things, when interacting with the container. 

To shut down the container (only needed if run in deamon mode):
```bash
docker compose down
```