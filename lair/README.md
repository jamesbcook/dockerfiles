git clone https://github.com/jamesbcook/dockerfiles.git

cd lair

docker-compoose build

docker-compose up -d database

docker run --rm -it --link lair_database_1:database  --network lair_default mongo:3.3 sh

mongo mongodb://database:27017/admin

rs.initiate({_id:"rs0", members: [{_id: 1, host: "database:27017"}]})

quit()

docker-compose up

If everything worked, you should see the following:

```
database_1      | 2017-04-14T05:17:59.827+0000 I INDEX    [conn4] build index done.  scanned 0 total records. 0 secs
database_1      | 2017-04-14T05:18:00.095+0000 I INDEX    [conn4] build index on: lair.meteor_accounts_loginServiceConfiguration properties: { v: 2, unique: true, key: { service: 1 }, name: "service_1", ns: "lair.meteor_accounts_loginServiceConfiguration" }
database_1      | 2017-04-14T05:18:00.095+0000 I INDEX    [conn4]        building index using bulk method
database_1      | 2017-04-14T05:18:00.097+0000 I INDEX    [conn4] build index done.  scanned 0 total records. 0 secs
lair_1          | Created admin@localhost with password b10f40182fd0eaa
```

ctlr + c

docker-compose start
