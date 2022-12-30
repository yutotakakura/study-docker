# メモ
## アプリの作成・実行
イメージを作成
```
$ docker image build -t sample/webrick:latest .
```
コンテナをバックグラウンドで立ち上げる
```
$ docker container run -d -p 8000:8000 --name webrick sample/webrick:latest
```
レスポンスが返ってくることを確認
```
$ curl http://localhost:8000
```
コンテナを停止（Ctrl + Cと同義）
```
$ docker container stop webrick
```
コンテナを削除
```
$ docker container rm webrick
```
ログを確認
```
$ docker container logs webrick
```
別コマンドを実行
```
$ docker container exec webrick ruby -v
```
後片付け
```
$ docker system prune -a
```
# Dockerfileの作成
Dockerfileに最初からコマンドを記載していかない。<br>
まずは /bin/bashでコンテナに入り、直でコマンドを実行してうまくいったものを後から追加していく。
```
$ docker image build -t sample/sinatra:latest .
```
-v 以下のオプションで、ローカルとコンテナでディレクトリを共有する。<br>
イメージを再作成しなくてもローカルの反映を逐一コンテナにも反映させることができる。
```
$ docker container run -it -p 4567:4567 --name sinatra -v ${PWD}/src:/var/www sample/sinatra:latest
```

# 参考文献
- [Docker入門講座](https://www.youtube.com/watch?v=lZD1MIHwMBY&list=PLs3eD4QT7ow6O5wyRRnRCvB7JMuq_D3-D&index=2)