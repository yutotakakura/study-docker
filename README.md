# メモ
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

# 参考文献
- [Docker入門講座](https://www.youtube.com/watch?v=lZD1MIHwMBY&list=PLs3eD4QT7ow6O5wyRRnRCvB7JMuq_D3-D&index=2)