# setup-VSCode-DevContainer day2

## [day1](../day1/README.md) に書いた`本当にやりたかったこと`を進めていく  

> GitHub からクローンしてきてビルドしたら使いたい開発環境ができている状態

知識がないため調査から開始。  
VSCode Remote Containerが良い : https://qiita.com/d0ne1s/items/d2649801c6f804019db7  
ここで書かれている `Dockerfile` や `docker-compose.yml` を自分で用意したいするには何からやればいいのか？と詰まる。  

> VSCodeで`Dockerfile`や`docker-compose.yml`があるプロジェクトを開く

＝ 自分で Docker 環境を用意したことが無いから基礎の基礎が理解できていない。  
  
調べる。  
Dockerfileの作り方（基礎） : https://qiita.com/daisuke30x/items/a3ea62ff8fa582b2b065  
Docker Compose作成方法 : https://qiita.com/ryome/items/c9fded9da60bce0f0b94  
  
どちらを用意するのが簡単、便利？  
  
Dockerファイルとdocker-compose.ymlの違い : https://zenn.dev/mom/articles/519466e9c7a22d  
> つまり、Dockerfileは単独のDockerイメージを作るための設定ファイルであり、docker-compose.ymlは複数のDockerイメージを組み合わせてアプリケーションを実行するための設定ファイルです。
  
一旦 Dockerfile で足りそう？  
  
C# や Unity は VSCode の 拡張でインストールできるので Dockerfile も不要なようにも見える。  
VSCode Dev Containersでユーザーが追加した拡張機能を保持 : https://zenn.dev/greendrop/articles/8bf88aad068f7d

