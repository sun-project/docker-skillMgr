# 使い方

## GitHub Personal Access Token (PAT) の作成

[個人アクセストークンを使用する] を参考に、Personal Access Tokenを作成します。

[個人アクセストークンを使用する]: https://docs.github.com/ja/free-pro-team@latest/github/authenticating-to-github/creating-a-personal-access-token

- アクセストークンには、 `read:packages` の権限を付与してください。
- 発行したアクセストークンは、二度と表示されないため、注意してください。

## Docker registryへのログイン

`docker-compose` を実行するホスト上で、Docker registryにログインします。

```sh
docker login docker.pkg.github.com -u <GitHubのユーザー名> -p <アクセストークン>
```

## 起動・停止コマンド集

```sh
# 起動
docker-compose up -d
# ビルドして起動
dokcer-compose up -d --build
# ビルド
docker-compose build [container_name]
# コンテナを更新せずに、再起動
docker-compose restart [container_name]
# 停止
docker-compose down
# volumeも削除して停止
# 現状mysqlの設定だとdatabaseも消える
docker-compose down -v

# 起動中に新しいコンテナに更新する場合
docker-compose build [container_name]
docker-compose up -d
# downはしなくてOK

# ログ確認
docker-compose logs
docker-compose logs -f

# コンテナ確認
docker-compose ps

# プロセス確認
docker-compose top
docker-compose top [container_name]

# コンテナに入る
docker-compose exec [container_name] /bin/sh
```