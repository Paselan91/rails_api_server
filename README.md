## Rails API Server

#### コンテナの立ち上げ、停止
```bash
$ make up
```

```bash
$ make stop
```

#### migration/seed
```bash
$ make migrate
```
```bash
$ make seed
```

#### ヘルスチェック
```bash
$ curl http://localhost:3000/users/index
[{"id":1,"name":"Pythagoras","created_at":"2021-04-02T11:27:12.968Z","updated_at":"2021-04-02T11:27:12.968Z"}]
```

#### トラブルシューティング
docker-compose up に失敗する場合は下記コマンドを実行し、再度 docker-compose up
```bash
$ rm tmp/pids/server.pid
```
Ctl + cでdockerを強制終了したことにより、pidファイルが残っているため（らしい）


#### コンテナへの接続
appコンテナ
```bash
$ make attach app
```

DB(mysql)コンテナ
```bash
$ make attach db
```
