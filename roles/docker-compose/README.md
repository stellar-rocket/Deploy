# Docker-compose Role
General role for deploying containers with docker-compose

## Requirement
	+ A `docker-compose.yml` file configured with your containers

## How to use
- Create a new role 
- Put your `docker-compose.yml` inside the role `files` folder
- Include the docker-compose role into your tasks:

#### Standalone container (no config to mount)

```
---
# tasks/main.yml

- name: "Docker-Compose | Include"
  include: "../../docker-compose/tasks/main.yml"
```

#### Containers with mounted config files

```
---
# tasks/main.yml

- name: "Docker-Compose | Include require"
  include: "../../docker-compose/tasks/require.yml"

#
# Wathevec script you want
#
  
- name: "Docker-Compose | Include install"
  include: "../../docker-compose/tasks/install.yml"
```

## Feature
### Force container restart

Usefull if you change your configs files. Set `update_required` variable to `true`. If you modify your `docker-compose.yml` file, `update_require` is set to `true` by default