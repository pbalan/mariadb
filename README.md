MARIADB
=======

The sole purpose of this docker is to run mariadb 10.3.9 so that we dont rely on brew installation.
Mitigate issues like installing MySQL version 8 which is incompatible with SequelPro client.

## Steps to run

> If you have Mariadb/MySQL installed on your machine, it is likely that your port 3306 is being used.
> We must free up the port first to allow docker to bind to this port on host machine.

### Stop your host machine's MariaDB or MySQL

- First, check which service is turned on by running the following:

```
brew services list
```

Expected output
===============

|Name       |Status  |User   |Plist                                                            |
|-----------|--------|-------|-----------------------------------------------------------------|
|dnsmasq    |started |root   |/Library/LaunchDaemons/homebrew.mxcl.dnsmasq.plist               |
|**mariadb**|started |root   |/Library/LaunchDaemons/homebrew.mxcl.mariadb.plist               |
|nginx      |started |pbalan |/Users/pbalan/Library/LaunchAgents/homebrew.mxcl.nginx.plist     |
|php        |started |pbalan |/Users/pbalan/Library/LaunchAgents/homebrew.mxcl.php.plist       |
|php@7.2    |started |pbalan |/Users/pbalan/Library/LaunchAgents/homebrew.mxcl.php@7.2.plist   |
|redis@3.2  |started |pbalan |/Users/pbalan/Library/LaunchAgents/homebrew.mxcl.redis@3.2.plist |
|supervisor |started |pbalan |/Users/pbalan/Library/LaunchAgents/homebrew.mxcl.supervisor.plist|


- Run the following command to stop the service
> Note: Replace service with appropriate service name.

```
brew services stop **service**
```

## Spin up your container

```
docker-compose up -d
```

## Check if you can connect via SequelPro

| Host                | Username         | Password      |
|---------------------|------------------|---------------|
| host.docker.internal| root             | root          |


