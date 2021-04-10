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
