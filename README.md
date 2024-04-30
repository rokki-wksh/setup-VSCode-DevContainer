# setup-VSCode-DevContainer

## VSCode で DevContainer を利用した開発環境を構築する

### 動機
- スキルの幅を広げるため自宅の端末に新しい開発環境を導入したい
- ローカル環境をできるだけクリーンな状態に保ちたい
  - 環境依存や競合の発生を避けたい、その解決に時間をかけたくない
- 新規参画者の開発環境セットアップを簡便にできるのも一つのスキル

### 参考にしたサイト
- https://gitforwindows.org/
- https://qiita.com/emiki/items/c0aa0b4da4b63921b153
- [VisualStudioCode公式|https://code.visualstudio.com/docs/devcontainers/containers]

### 構築環境
- Windows 10 pro
- VSCode 1.88.1 (system setup)
- git for windows 2.45.0

### 準備
- VSCode
  - VSCode はインストール済みだったので省略。
- Git
  - 未インストールだったので[Windows10でGitHubを始める～①Gitインストール|https://qiita.com/emiki/items/c0aa0b4da4b63921b153]を参考にサクッとインストール。
  - アカウント類は自習用に持っていたのでそのまま使用。

### DevContainer の導入
VSCode で DevContainer を利用して、Docker 環境内に開発環境を構築する。  
そうすることで欲しい環境ごとのライブラリ競合などを避けることができる。  
公式チュートリアルに従ってDockerDesktopからインストールする  
[DockerDesktop_install]

