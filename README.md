# Trino & Monk
This repository contains Monk.io template to deploy Trino & Monk either locally or on cloud of your choice (AWS, GCP, Azure, Digital Ocean).

# Prerequisites
- [Install Monk](https://docs.monk.io/docs/get-monk)
- [Register and Login Monk](https://docs.monk.io/docs/acc-and-auth)
- [Add Cloud Provider](https://docs.monk.io/docs/cloud-provider)
- [Add Instance](https://docs.monk.io/docs/multi-cloud)

#### Make sure monkd is running.
```bash
foo@bar:~$ monk status
daemon: ready
auth: logged in
not connected to cluster
```

## Clone Repository
```bash
git clone https://github.com/Burakhan/monk-trino
```

## Load Template
```bash
cd monk-trino
monk load MANIFEST
```


#### Let's take a look at the themes I have installed.
```bash
foo@bar:~$ monk list monk-trino
✔ Got the list
Type      Template          Repository  Version  Tags
group     monk-trino/stack  local       -        -
runnable  monk-trino/trino  local       -        -
```

## Deploy Stack
```bash
foo@bar:~$ monk run monk-trino/stack
? Select tag to run [local/monk-trino/stack] on: mnk
✔ Starting the job: local/monk-trino/stack... DONE
✔ Preparing nodes DONE
✔ Checking/pulling images...
✔ [================================================] 100% trinodb/trino:latest mnk
✔ Checking/pulling images DONE
✔ Started local/monk-trino/stack

🔩 templates/local/monk-trino/stack
 └─🧊 Peer mnk
    └─🔩 templates/local/monk-trino/trino
       └─📦 019faad75e1cf1237bc5f81384a51073-al-monk-trino-trino-monk-trino
          ├─🧩 trinodb/trino:latest
          └─🔌 open 13.51.200.163:8086 (0.0.0.0:8086) -> 8080

💡 You can inspect and manage your above stack with these commands:
	monk logs (-f) local/monk-trino/stack - Inspect logs
	monk shell     local/monk-trino/stack - Connect to the container's shell
	monk do        local/monk-trino/stack/action_name - Run defined action (if exists)
💡 Check monk help for more!
```
## Check admin gui

`http://13.49.137.107:8084/`


## Variables
The variables are in `stack.yml` file. You can quickly setup by editing the values here.

| Variable                     	| Description                               	|
|------------------------------	|-------------------------------------------	|
| trino_port                    | Trino web port, Default 8086	               |





## Stop, remove and clean up workloads and templates

```bash
monk purge -x -a
```

