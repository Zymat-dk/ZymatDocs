---
layout: default
title: Manage database and code from docker
parent: Docker
nav_order: 2
---

# Database on docker
**IMPORTANT**: The container must be running, while these commands are run - otherwise they wont work. 
All of the commands use the `run` bash script, and Linux or WSL must be used. 

To apply migrations:
```bash
./run manage migrate
```

To make migrations from changed code:
```bash
./run manage makemigrations <MODULE>
```
Most of the time it will be the `pages` module:
```bash
./run manage makemigrations pages
```

Create superuser:
```bash
./run manage createsuperuser
```

# Manage the code 
```bash
./run manage <COMMAND>
```

TODO: Linting, secret, quality, formatting


# Updating dependencies or added new 
```bash
./run pip3:outdated
```

```bash
./run yarn:outdated
```

```bash
./run pip3:install
```

```bash
./run yarn:install
```

# Testing

TODO
