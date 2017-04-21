# notes
Notes on code/mongo queries used

This is a placeholder for where I can dump queries and mongo code used (so as to remember WTH I did when...)  :)

Alex gave me this - needed to manually add the users back to a database being brought up on ORD (Chicago).

[
	{
		"_id" : "prod_smartsheet_com.app",
		"user" : "app",
		"db" : "prod_smartsheet_com",
		"roles" : [
			{
				"role" : "readWrite",
				"db" : "prod_smartsheet_com"
			},
			{
				"role" : "read",
				"db" : "prod_smartsheet_com"
			}
		]
	},
	{
		"_id" : "prod_smartsheet_com.reader",
		"user" : "reader",
		"db" : "prod_smartsheet_com",
		"roles" : [
			{
				"role" : "read",
				"db" : "prod_smartsheet_com"
			}
		]
	},
	{
		"_id" : "prod_smartsheet_com.build",
		"user" : "build",
		"db" : "prod_smartsheet_com",
		"roles" : [
			{
				"role" : "dbAdmin",
				"db" : "prod_smartsheet_com"
			}
		]
	},
	{
		"_id" : "prod_smartsheet_com.dbaReader",
		"user" : "dbaReader",
		"db" : "prod_smartsheet_com",
		"roles" : [
			{
				"role" : "readWrite",
				"db" : "prod_smartsheet_com"
			}
		]
	}
]


Todd was able to find that only the users reader and build were on this instance.  The code I came up with was:

use prod_smartsheet_com 

db.createUser(
   {
     user: "app",
     pwd: "XXXXXXXXXX",
     roles: [ "readWrite", "read" ]
   }
)



use prod_smartsheet_com 

db.createUser(
   {
     user: "reader",
     pwd: "XXXXXXXXXX",
     roles: [ "read" ]
   }
)


use prod_smartsheet_com 

db.createUser(
   {
     user: "build",
     pwd: "XXXXXXXXXX",
     roles: [ "dbadmin" ]
   }
)


use prod_smartsheet_com 

db.createUser(
   {
     user: "dbaReader",
     pwd: "XXXXXXXXXX",
     roles: [ "readWrite" ]
   }
)

This worked.
