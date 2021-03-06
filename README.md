# try_azure_app_service

## nodenv で node リスト最新化

```bash
$ git -C "$(nodenv root)"/plugins/node-build pull
...
 create mode 100644 share/node-build/14.16.1
 create mode 100644 share/node-build/15.12.0
 create mode 100644 share/node-build/15.13.0
 create mode 100644 share/node-build/15.14.0
$ nodenv install 14.16.1
$ nodenv versions
* 14.15.3 (set by /home/***/.anyenv/envs/nodenv/version)
  14.16.0
  14.16.1
```

## node ローカルインストール

```bash
$ nodenv local 14.16.1
$ node -v
v14.16.1
$ npm -v
6.14.12
```

## koa2/typescript 環境構築

- [Koa.js ミドルウェアの作り方](https://qiita.com/kei-nakoshi/items/904c46faff621c1be674)
- [TypeScript Ninja](http://typescript.ninja/typescript-in-definitelyland/index.html)
- [TypeScript Deep Dive 日本語版](https://typescript-jp.gitbook.io/deep-dive/)
- [Node.js & TypeScriptのプロジェクト作成](https://typescript-jp.gitbook.io/deep-dive/nodejs)

```bash
$ npm init -y
$ npm i -D typescript @types/node ts-node
$ npx tsc --init --rootDir src --outDir lib --esModuleInterop --resolveJsonModule --lib es6,dom --module commonjs
$ cp -p package.json package.json.org
$ vi package.json
$ diff package.json package.json.org 
7,8d6
<     "8443": "PORT=8443 PUB=on PRI=on ts-node src/index.ts",
<     "start": "sudo ts-node src/index.ts",
$ npm i -S koa
$ npm i -D @types/koa
$ cat src/index.ts
import Koa from 'koa'

// Koa2 サーバ初期設定
const app = new Koa()

// ミドルウェア設定
app.use(async (ctx) => {
  ctx.body = "koa app."
})

// サーバ起動
const port = process.env.PORT || 443
app.listen(port)
$ npm run 8443    # Ctrl-C で停止。http://localhost:8443 でアクセス
```
