# Emoncms docker

# Community version

Thanks to community member [alexandrecuer](https://community.openenergymonitor.org/u/alexandrecuer) for an up-to-date Emoncms docker 

The easy way =  standalone image with everything inside: [alexjunk/emoncms](https://hub.docker.com/r/alexjunk/emoncms)

Included modules : graph, dashboard, app, sync, postprocess, backup

emonHub docker: https://hub.docker.com/r/alexjunk/emonhub

**Note: this is not a drop in replacement for the emoncms-docker container, this is an all-in-one image with different architecture**

### For more details on how to organize you compose file : https://emoncms-docker.github.io/setup/


# multi-containers version

### An way to deploy a simple Emoncms installation with separate containers 

One for the php server, one for the database, and one for the broker : [Quickstart](web)

**Note: This docker installation is not quite a complete Emoncms installation.** In general we recommend building an Emoncms installation using our EmonScripts installation script on a Debian/Ubuntu/RaspberryPi based system, this said this docker image does provide a useful alternative approach to get a simple but functional emoncms installation up and running.

Latest image hosted on docker hub: [openenergymonitor/emoncms:latest](https://hub.docker.com/r/openenergymonitor/emoncms/)




