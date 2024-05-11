# How to Add a Project to a Running Instance

First extract the source folder to ./opengrok/src while docker-compose is running.
The files should be next level down underneath the folder. For example:

```

```

Obtain a shell inside the docker container, such as with:

```
docker-compose exec opengrok bash
```

Next steps:

 1. Add the project
 1. Index the progject
 1. Save changes to disk

### Add the project

```
opengrok-projadm -b /opengrok -U http://localhost:8080/opengrok -a <FOLDER_NAME>
```

Where an example value of `<FOLDER_NAME>` would be `virt-manager-4.1.0`

### Index that project

This step often takes a long time

```
opengrok-indexer -a /opengrok/lib/opengrok.jar -- -s /opengrok/src -d /opengrok/data -W /opengrok/etc/configuration.xml -H -P -S -G -U http://localhost:8080/opengrok <FOLDER_NAME>
```

### Save Changes

Update the config on disk, and update the running instance's index page

```
opengrok-projadm -b /opengrok -U http://localhost:8080/opengrok -r

# Experimenting with adding -u on the end to cause it to update the index without bouncing opengrok
```
