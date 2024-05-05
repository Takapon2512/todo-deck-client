# 使用するベースイメージを指定
FROM node:22.0-alpine

# 作業ディレクトリを設定
WORKDIR /app

# npmのアップデートチェックを無効化
ENV NO_UPDATE_NOTIFIER true

# パッケージリストの更新とシステムパッケージのアップグレード
RUN apk update && apk upgrade && \
    apk add git

# package.json と package-lock.json (もし存在する場合) をコピー
COPY package*.json ./

# 依存関係をインストール
RUN npm install

# ソースコードをコピー
COPY . .

# ポート3000を公開
EXPOSE 3000

# Nuxt.js アプリケーション環境変数
ENV NUXT_HOST=0.0.0.0
ENV NUXT_PORT=3000

# Nuxt.js アプリケーションを起動
CMD ["npm", "run", "dev"]
