# Private Cloud

This project utilizes a Docker-Machine to run a Mesos/Marathon Cluster.  Mesos & Marathon are setup in containers with direct acces to the host docker system in the Docker-Machine.

Docker Containers

	- Master
	- Slave
	- Marathon
	- Mesos DNS

Marathon controlled applications can then be added and managed via the Marathon API using Curl, dcos if installed or the available marthon bash script.

Mesos URL can be accessed at:  http://{docker-machine ip}:8080
Marathon URL can be access at http://{docker-machine ip}:5050

The benefits of this is the developer now has direct access to the underlying docker system via his client docker binary to attach, execute, anaylize logs or work with additional containers as needed.

#### Clone down the project

```bash
$ git clone https://github.com/degnome/private-cloud.git
$ cd private-cloud
```

##### Alternately the following Environment Variables can be used

- DOCKER_USER=username
- DOCKER_PWD=password
- DOCKER_EMAIL=email

#### To install the project

1. Install

	```bash
	$ ./mesos create
	```

2. Start

	```bash
	$ ./mesos start
	```

3. Stop

	```bash
	$ ./mesos stop
	```

4. Destroy

	```bash
	$ ./mesos destroy
	```

Create a env.sh file to store your required environment variables if you need to login to a directory

>_ATTENTION: You must specify the desired repository username password and email in the file to login properly_



### To Deploy an Application


1. Deploy a Group

	```bash
	$ ./marathon group_add apps/ts.json
	```

2. Destroy a Group

	```bash
	$ ./marathon group_rm {groupId}
	```

3. Deploy an Application

	```bash
	$ ./marathon app_add apps/helloworld.json
	```

4. Destroy an Application

	```bash
	$ ./marathon app_rm {appId}
	```



### Tools

Scripts exist in the tools directory to help work with the Databases.

1. Query Mesos DNS to check for the service

	```bash
	$ ./tools/dig marathon.mesos
	```

2. Connect to the Cassandra DB

	```bash
	$ ./tools/cqlsh {CassandraDB Hostname}
	```

3. Connect to the Mongo DB

	```bash
	$ ./tools/mongo {MongoDB Hostname}
	```

4. Connect to the Redis DB

	```bash
	$ ./tools/redis-cli {RedisDB Hostname}
	```


