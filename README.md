## Rails API Server

build & up application
```bash
$ make up
```

migrate
```bash
$ make migrate
```

migrate
```bash
$ make seed
```

Health Check
```bash
curl http://localhost:3000/users/index
[{"id":1,"name":"Pythagoras","created_at":"2021-04-02T11:27:12.968Z","updated_at":"2021-04-02T11:27:12.968Z"}]
```

#### Others
attach app container
```bash
$ make attach app
```

attach DB(mysql) container
```bash
$ make attach db
```
