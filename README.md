##Prerequisites

* VirtualBox
* Vagrant
* vagrant-berkshelf plugin

##Running

With the above prerequisites satisfied, the VM can be started with:

    $ vagrant up
    
When this has finished, you should be able to connect to the database instance as follows:

* host - `localhost`
* port - `15432` (note the `1` in front of the standard port `5432` - this is to avoid port conflict with a PostgreSql instace running on the host)
* username - `postgres`
* password - `password`

e.g.:

    $ psql -h localhost -p 15432 -U postgres -w postgres
    

