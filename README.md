# fdutils
Misc foundationdb related scripts / hacks

# Install

git clone https://github.com/harikb/fdbutils.git 

export PATH=/path/to/bin:${PATH}

# Fix fdb-cli wrapper

Include any local customization and make sure it runs

	$ fdb-cli
	Using cluster file `/etc/foundationdb/fdb.cluster'.

	The database is available.

	Welcome to the fdbcli. For help, type `help'.
	fdb>

# Usage

## Show role by IP

	$ fdb-status | fdb-role-by-ip | fdb-unfold
	{"address":"10.0.0.10","roles":"cluster_controller,commit_proxy,data_distributor,grv_proxy,master,ratekeeper"}
	{"address":"10.0.0.11","roles":"commit_proxy,grv_proxy,resolver"}
	{"address":"10.0.0.12","roles":"coordinator,log"}
	{"address":"10.0.0.13","roles":"log,storage"}
	{"address":"10.0.0.14","roles":"log,storage"}
	{"address":"10.0.0.15","roles":"storage"}
	{"address":"10.0.1.10","roles":"coordinator,log"}
	{"address":"10.0.1.11","roles":"coordinator,log"}
	{"address":"10.0.1.12","roles":"coordinator,log"}
	{"address":"10.0.2.10","roles":"router"}
	{"address":"10.0.2.12","roles":"coordinator,log"}
	{"address":"10.0.2.13","roles":"log,storage"}
	{"address":"10.0.2.14","roles":"log,storage"}
	{"address":"10.0.2.15","roles":"storage"}

## Show role by process

	$ fdb-status | fdb-role-by-process | fdb-unfold | head
	{"address":"10.0.0.10:4500","roles":"commit_proxy"}
	{"address":"10.0.0.10:4501","roles":"grv_proxy"}
	{"address":"10.0.0.10:4502","roles":"cluster_controller"}
	{"address":"10.0.0.10:4503","roles":"grv_proxy"}
	{"address":"10.0.0.10:4504","roles":"commit_proxy"}
	{"address":"10.0.0.10:4505","roles":"master"}
	{"address":"10.0.0.10:4506","roles":"data_distributor,ratekeeper"}
	{"address":"10.0.0.10:4507","roles":"commit_proxy"}
	{"address":"10.0.0.11:4500","roles":"grv_proxy"}
	{"address":"10.0.0.11:4501","roles":"resolver"}

