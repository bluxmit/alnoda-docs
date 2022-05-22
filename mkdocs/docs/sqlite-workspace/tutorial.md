This doc has examples how to use workspace toolset to develop SQLite databases and fill them with data. 
As well explore, query and visualise.  
  
To start open Quickstart page for quick access to all the tools 

![Workspace collage](img/sqlite-wid.png)

Use workspace terminal to execute CLI commands

![codeserver-demo](../base-workspace/img/base-workspace-terminal.gif)

Workspace conntains example SQLite database, the file `/home/static-server/sqlite-viewer/examples/Chinook_Sqlite.sqlite`  


## NocoDB

[NocoDB](https://docs.nocodb.com/). NocoDB is an open source Airtable alternative. Use it to create SQLite tables, develop databases 
without SQL.  

NocoDB can also be used to fill SQLite databases with data with the help of nice interactive UI. 

Launch the workspace, navigate to the Workspace UI and open NocoDB. 
Create new user (provide any email,pass). Create tables, enter data, import data files, create forms and much more.  


### NocoDB with existing SQLite database

Create NocoDB project with an empty external SQLite database file `/home/project/sqlite-db/db-main.sqlite`. 

![noco-new-main](img/noco-new-main.png

Create some data, and explore it with Sqlite-web 

![noco-new-main](img/sqliteweb-main.gif)

You can also open existing SQLIte database, and edit it with NocoDB. Let's open example SQLite database `/home/static-server/sqlite-viewer/examples/Chinook_Sqlite.sqlite` 

![noco-new-main](img/noco-chinook.gif)


### query NocoDB data 

NocoDB is backed by SQLite3, database file `/home/nocodb/noco.db `.  

You can query NocoDB databse directly with sqlite-web. Open it from Workspace UI Quickstart page.  

At any moment you can copy SQLite database from NocoDB with all the data, edit, modify and configure for the needs of your application. 

- Copy of NocoDB database and continue developing with Sqlite-web

```
mv -f /home/nocodb/noco.db /home/project/sqlite-db/db-main.sqlite 
```


## Sqlite 

SQLite3 is installed. Open terminal and execute

```
sqlite3
```

__Note:__ check out a better CLI [litecli](#litecli) 

### Sqlite extensions

The following compiled extensions are present in the folder `/home/sqlite-extensions`

- [crypto](https://github.com/nalgeon/sqlean/blob/main/docs/crypto.md): secure hashes
- [fileio](https://github.com/nalgeon/sqlean/blob/main/docs/fileio.md): read and write files
- [fuzzy](https://github.com/nalgeon/sqlean/blob/main/docs/fuzzy.md): fuzzy string matching and phonetics
- [ipaddr](https://github.com/nalgeon/sqlean/blob/main/docs/ipaddr.md): IP address manipulation
- [re](https://github.com/nalgeon/sqlean/blob/main/docs/re.md): regular expressions
- [stats](https://github.com/nalgeon/sqlean/blob/main/docs/stats.md): math statistics
- [text](https://github.com/nalgeon/sqlean/blob/main/docs/text.md): string functions
- [unicode](https://github.com/nalgeon/sqlean/blob/main/docs/unicode.md): Unicode support
- [uuid](https://github.com/nalgeon/sqlean/blob/main/docs/uuid.md): Universally Unique IDentifiers

Example start SQLite, and load extension: 

```
sqlite3
.load /home/sqlite-extensions/stats
```

### Upload & download SQLite databases

No matter if workspace is used locally, in cloud or kubernetes you can upload and download database files using file browser 

![noco-new-main](img/filebrowser-download.png)

### Copy SQlite databases

SQlite is just a file, jou can copy it and replace other databases. For example, if you want to copy NocoDB database 
into the "Main" database, which is served by Sqlite-web ('Main') simply execute in terminal

```
mv -f /home/nocodb/noco.db /home/project/sqlite-db/db-main.sqlite 
```

You also can use file browser to move or copy files.


## Sqlite-web

[sqlite-web](https://github.com/coleifer/sqlite-web) - is a web-based SQLite database browser. It can serve any SQLite database.  

There are 2 SQlite database served by default:

- NocoDB database. Sqlite-web 'Nocodb' 
- 'Main' database. Empty SQlite3 database. Sqlite-web 'Main'
- 'Example/test' database. Filled with test "Chinook" database. 

![noco-new-main](img/sqliteweb-chinook.gif)

### Serve on-demand SQlite database

One port 8034 is reserved for serving on-demand database with Sqlite-web. 
Serve it with the following command

```
sqlite_web <path-to-your-sqlite-database-file> --host 0.0.0.0 --port 8034
```

Example, start sqlite-web on port 8034 for SQLite database file `/home/static-server/sqlite-viewer/examples/Chinook_Sqlite.sqlite`

```
sqlite_web /home/static-server/sqlite-viewer/examples/Chinook_Sqlite.sqlite --host 0.0.0.0 --port 8034 
```

and with extensions loaded:

```
sqlite_web /home/static-server/sqlite-viewer/examples/Chinook_Sqlite.sqlite --host 0.0.0.0 --port 8034  -e /home/sqlite-extensions/text.so -e /home/sqlite-extensions/unicode.so -e /home/sqlite-extensions/uuid.so
```

You can open on-demand database served with Sqlite-web from the Quickstart page.


## Sqlite-viewer 

[sqlite-viewer](https://github.com/inloop/sqlite-viewer) - explore and query SQLite databases.   

Upload SQLite database file (from your local machine) and explore.

![noco-new-main](img/sqlite-viewer.png)


## Web-GUI-for-SQLite

[Web-GUI-for-SQLite](https://github.com/cyrilbois/Web-GUI-for-SQLite) - explore and query SQLite databases.  

Upload SQLite database file (from your local machine) and explore.
 
![noco-new-main](img/sqlite-web-gui.png)


## Litecli

[Litecli](https://github.com/dbcli/litecli) - is a command-line client for SQLite databases that has auto-completion and syntax highlighting. Useful if you prefer CLI.  

Open Terminal and try with example database:  

```
litecli /home/static-server/sqlite-viewer/examples/Chinook_Sqlite.sqlite
```

![noco-new-main](img/litecli-1.png)

![noco-new-main](img/litecli-2.png)


Load extensions

```
.load /home/sqlite-extensions/stats
```


## Tbls

Generate docs for the example database

```
tbls doc sqlite:////home/static-server/sqlite-viewer/examples/Chinook_Sqlite.sqlite /home/static-server/sql-tbls
```

and view SVG files with Static File Server

![noco-new-main](img/tbls.gif)


## DB designer

With DB designer you can visually create ERD diagrams, and generate DDL SQL scripts 

![noco-new-main](img/dbdesigner.png)

## Advanced 

### SQLite Json

Examples

```
CREATE TABLE jsontest   (
  id INTEGER NOT NULL PRIMARY KEY,
  jss JSON
);

INSERT INTO jsontest  VALUES 
(1, json(' { "key1" : "my key 1", "key2": [ "test" ] } ')),
(2, json(' { "key1" : "my new key", "key2": [ "test", "test" ] } ')),
(3, json(' { "key1" : "my yet another key", "key2": [ "test", "test", "test2" ] } '));

SELECT * FROM jsontest;
```

__Links:__
    - [Complete SQlite JSON docs](https://www.sqlite.org/json1.html#jmini)


### Rclone

[rclone](https://rclone.org/) is a command line program to manage files on cloud storage. 
It is a feature rich alternative to cloud vendors' web storage interfaces.  

__Copy dump to S3:__  
Create file `~/.config/rclone/rclone.conf` with the following content

```
[remote]
type = s3
provider = AWS
access_key_id = XXXXXXXXXXXXXXXXXXXXXX
secret_access_key = XXxxXXxXXXxxxXXxXXXxxXXXxxxXXXxXXXX
region = xx-xxxx-x
```

Use Rclone to copy to S3 and delete from local

```
rclone move /home/project/sqlite-db remote:my-s3-bucket/sqlite/
```

__Restore from S3 to local:__
When there is a need to get database from S3 to local folder. 

```
# copy 
rclone copy remote:my-s3-bucket/sqlite/ /home/sqlite-db/
# mount S3 without copying
rclone sync remote:my-s3-bucket/sqlite/ /home/sqlite-db/
```

