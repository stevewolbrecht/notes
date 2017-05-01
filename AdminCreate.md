# mongoDB
MongoDB stuff

<b>Basic commands and stuff<b/>

<b>Basic logins</b>
```
mongo <hostname>:<mongodbPortNum>/<databaseName> -u <user> -p <pass>
```

<b>Create login prompt</b>
```
prompt = function() {
    user = db.runCommand({connectionStatus:1}).authInfo.authenticatedUsers[0]
    host = db.getMongo().toString().split(" ")[2]
    curDB = db.getName()
    if (user) {
       uname = user.user
    }
    else {
       uname = "local"
    }
    return uname + "@" + host + ":" + curDB + "> "
} 
```

<b>Create admin user for Mongo 3.0+</b>

```
db.createUser(
   {
       user: "admin", 
       pwd: "password", 
       roles:["root"]
   })
   ```
   
   
