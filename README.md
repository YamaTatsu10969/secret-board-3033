# N予備校の教材

# secret-board-3033
入門コースの3章33節 secret-board (ISC License)


## heroku でデプロイするために必要なこと

```
// CLI にログイン
heroku login

// Heroku Container Registry にログインする
heroku container:login 

// サーバーの作成
heroku create

// コンテナのプッシュ
heroku container:push web

// Heroku で利用する PostgreSQL のデータベースの作成（開発用の簡易的な PostgreSQL のデータベース）
heroku addons:create heroku-postgresql:hobby-dev

// アプリケーションのリリース
heroku container:release web

// アプリケーションにアクセス 
// もしくは、 heroku create で表示されたURL
heroku open 
```

M1だとエラーが発生する。そのため、以下を行ってデプロイする。

[M1 MacでHeroku containerにデプロイしたら `Exec format error` と出て困った話](https://zenn.dev/daku10/articles/m1-heroku-container-trouble-exec-format-error)


### example

```
docker buildx build . --platform linux/amd64 -t yamatatsu/quiet-lake-70082:latest
docker tag yamatatsu/quiet-lake-70082 registry.heroku.com/quiet-lake-70082/web
docker push registry.heroku.com/quiet-lake-70082/web
heroku container:release web -a quiet-lake-70082
```

