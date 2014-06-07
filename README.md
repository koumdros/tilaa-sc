tilaa-sc
========

tilaa snapshot control

Defaults can be set in line 109 and 110. Then you can simply do  
* `tilaa-sc -status 1` - for snapshot overview  
* `tilaa-sc -id 1234` - for create a snapshot with default name
* `tilaa-sc -id 1234 -name "hello world"` - create snapshot with given name  
* `tilaa-sc -delete 123` - delete snapshot id 123


	-u api@user.tld
	-p password
	-id 1234 # tilaa server id while creating
	-n "snapshot backup name" # default "backup"
	-o <0|1> # overwrite existing snapshot. default 1
	-l <0|1> # online (live) snapshotting. default 1
	-s|status <0|1> # list snapshot overview
	-debug <0|1> # list all parameters
	-delete 123 # snapshot id, NOT! server id! get snapshot id with -status 1

	EXAMPLE
	=======

	## STATUS
	tilaa-sc -u api@user -p pwd1 -status 1

	Tilaa snapshot overview

	"status":"ERROR"
	"message":"Not Found"

	## CREATE (while creating, ID is the ID of your SERVER!!
	tilaa-sc -u api@user -p pwd1 -id 1234 # default parameter for -l -o -n.

	"status":"OK"
	"message":"The virtual machine snapshot is being created"

	## STATUS
	tilaa-sc -u api@user -p pwd1 -status 1 # notice: status => start

	Tilaa snapshot overview

	"status":"OK"
	"snapshots":"id":36,"name":"backup"
	"ram":0,"storage":30,"template":"id":313,"name":"ArchLinux 2012.12.01, 64 bit"
	"status":"start"
	"created":"2014-06-07T17:46:03+02:00"

	## STATUS
	tilaa-sc -u api@user -p pwd1 -status 1

	"status":"OK"
	"snapshots":"id":36,"name":"backup"
	"ram":0,"storage":30,"template":"id":313,"name":"ArchLinux 2012.12.01, 64 bit"
	"status":"success"
	"created":"2014-06-07T17:46:03+02:00"

	## DELETE
	tilaa-sc -u api@user -p pwd1 -delete 36 # delete snapshot id 36. see -status 1 for snapshot id!!

	"status":"OK"
	"message":"The virtual machine snapshot has been deleted"
	

