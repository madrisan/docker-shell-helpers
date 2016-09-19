# Helper functions for using Docker in shell scripts

The script __docker-shell-helpers.sh__ provides a list of functions for making
(hopefully) simpler the creation and usage of Docker containers inside a shell scripts.

## List of Helper Functions

The __docker-shell-helpers__ library currently provides the following public functions:

* __container_id()__
  * _desc:_ return the _Docker Id_ of a container
  * _args:_ container name
* __container_exists()__
  * _desc:_ return true if the container exists, and false otherwise
  * _args:_ container name
* __container_is_running()__
  * _desc:_ return true if the container is running, and false otherwise
  * _args:_ container name
* __container_stop()__
  * _desc:_ stop a container, if it's running
  * _args:_ container name
* __container_remove()__
  * _desc:_ stop and remove a container from the host node
  * _args:_ container name
* __container_exec_command()__
  * _desc:_ run a command (or a sequence of commands) inside a container
  * _args:_ container name
* __container_property()__
  * _desc:_ get a container property
  * _args:_ container name and one of the options: --id, --ipaddr, --os
* __container_create()__
  * _desc:_ create a container
  * _args:_ container --name, --os and a host folder (--disk) to map
* __container_start()__
  * _desc:_ start a container if not running
  * _args:_ container name
* __container_status_table()__
  * _desc:_ return the status of a container
  * _args:_ container name of no args to list all the containers
* __container_list()__
  * _desc:_ return the available container name
  * _args:_ none
* __container_list_ul()__
  * _desc:_ return the available container names, as an unsigned list
  * _args:_ none

## Example

Here's is a simple example of how the library functions can be used.

```
container_create --name centos7 --os "centos:latest" --disk ~/docker-datadisk:/shared:rw
container_start centos7
echo "The running OS is: $(container_property --os centos7)"
container_exec_command centos7 "echo 'Hello World!'"
container_remove centos7
```
