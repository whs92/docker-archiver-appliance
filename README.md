# Docker-Compose Deployment of Archiver Appliance

This respository in an example deployment of
W.Smith Docker image of the EPICS Archiver Appliance
(on [Docker Hub][] and on [Github][])
bundled together with a Redis database. Each appliance is in it's own container.

Redis is used for the persistance of the appliance configuration,
see the [RedisPersistence class][].

Data is stored in ./storage/{sts,mts,lts} mounted from the host.

### Usage

Modify the [docker image](https://github.com/whs92/docker-archiver-image) for your IP address and build it.
Run:

```
docker-compose up -d
```

In a browser, open <http://localhost:17665/mgmt/ui/index.html>.
It might take ~20-30 seconds until the tomcat server is
fully up and running, so if you get the following error,
just refresh the page after a couple of seconds:

> HTTP Status 503 – Service Unavailable  
> This appliance is still starting up

On this home page of the archiver appliance, you can add the PVs
served by the example IOC by entering the following lines
in the input field and then clicking the `[Archive]` button:

[RedisPersistence class]: https://slacmshankar.github.io/epicsarchiver_docs/api/org/epics/archiverappliance/config/persistence/RedisPersistence.html
[Docker Hub]: https://hub.docker.com/r/pklaus/archiver-appliance
[Github]: https://github.com/pklaus/docker-archiver-appliance
