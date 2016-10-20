# Galera Cluster (Experimental)

### Usage:

Galera clients are installed on host labeled `mysql=1`
Galera-lb is installed on host labeled `nfs=server`
phpmyadmin is installed on host labeled `pma=1`

Once deployed, use a mysql client to connect:

`mysql -u root -p -h<galera-lb>`

(No user database is installed at startup)

### Info:

This template creates a MariaDB Galera cluster on top of Rancher. Using the Galera plugin, the MariaDB cluster runs in a multi-master replicated mode.

When deployed from the catalog, a three node cluster is created. The cluster is set up for replication between all of the nodes. The cluster sits behind a light weight proxy layer that forwards all reads/writes to a single server in order for transaction locks. The proxy layer is fronted by a Rancher load balancer.

Clients should access the cluster through the load balancer so they do not need to be updated in the event of a failure.

When the cluster is completely stopped and started, user intervention is required to bring it back online. Instructions can be found in the [Galera documentation](http://galeracluster.com/documentation-webpages/quorumreset.html).

The replication mechanism used in the cluster is based on the MySQL dump method. This has the side effect of taking a long time to bring in a new node when there are large data sets.

A PhpMyAdmin instence is created as well in the stack with no port mapping on the host. '''Configure the HAproxy to get access to it'''.
