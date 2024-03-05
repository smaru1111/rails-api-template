## 参考にしたやーつ
https://zenn.dev/chiku_dev/articles/29ae4b8afa6fd4#rails-api-%E3%81%AE%E8%A8%AD%E5%AE%9A

## 起動方法

```
docker-compose build
docker-compose up -d
docker-compose ps
// psでコンテナを確認したら、webと書かれているコンテナのNAMEをコピーして、{NAME}を置き換える
docker exec -it {NAME} bash
```

## 動作確認
Create
```
curl -X POST -H "Content-Type: application/json" -d '{"regex":{"title":"{ここに作成するタイトル}"}}' http://localhost:3000/api/v1/regexes
```
Read
```
curl -X GET http://localhost:3000/api/v1/regexes
```
Update
```
curl -X PUT -H "Content-Type: application/json" -d '{"regex":{"title":"{ここに更新するタイトル}"}}' http://localhost:3000/api/v1/regexes/{ここにidを指定}
```
Delete
```
curl -X DELETE http://localhost:3000/api/v1/regexes/{ここにidを指定}
```

## ディレクトリ説明

```
app: アプリケーションのメインのコードが含まれる場所。

assets: CSS、JavaScript、画像ファイルなどの静的ファイルが格納される。
controllers: コントローラのコードが格納される。リクエストを受け取り、適切なモデルやビューに処理を委譲する。
models: データモデルのコードが格納される。データベースとのやり取りやデータのバリデーションなどが定義される。
views: ビューのテンプレートファイルが格納される。HTML と Ruby の組み合わせで、ユーザに表示されるコンテンツを生成する。
bin: アプリケーションの実行可能ファイルが含まれる。

config: アプリケーションの設定ファイルが格納される。

environments: 環境ごとの設定ファイルが含まれる。
initializers: アプリケーションの初期化に関する設定ファイルが格納される。
db: データベース関連のファイルが含まれる。

migrate: データベースのマイグレーションファイルが格納される。
schema.rb: データベースのスキーマが自動生成されたファイル。
lib: サポートライブラリやユーティリティクラスが格納される。

log: アプリケーションのログファイルが格納される。

public: 外部に公開するファイルが格納される。主に画像やスタイルシートなどの静的ファイルが含まれる。

test: テストコードが格納される。

tmp: 一時ファイルが格納される。

vendor: サードパーティ製のライブラリが格納される。
```
