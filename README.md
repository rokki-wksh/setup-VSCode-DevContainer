# setup-VSCode-DevContainer

## VSCode で DevContainer を利用した開発環境を構築する

個人学習メモの体裁を少し整えたものです。ブログ代わりだと思っていただければ。

### 動機
- スキルの幅を広げるため自宅の端末に新しい開発環境を導入したい
- ローカル環境をできるだけクリーンな状態に保ちたい
  - 環境依存や競合の発生を避けたい、その解決に時間をかけたくない
  - ローカルへのインストールを許容するもの
    - 何かをする前提として必要かつ困ったら最新版でかまわないもの
    - VSCode、Git など
  - ローカルへのインストールを許容したくないもの
    - 各言語パック、ツールなど専用の環境を用意したいもの
    - Flutter、C#、Unity など
- 開発環境セットアップ手順の簡素化は業務でも使えたら便利

### 参考にしたサイト
- Git公式 : https://gitforwindows.org/
- Windows10でGitHubを始める～①Gitインストール : https://qiita.com/emiki/items/c0aa0b4da4b63921b153
- VisualStudioCode公式 : https://code.visualstudio.com/docs/devcontainers/containers

### 作業前環境
- Windows 10 pro
- VSCode 1.88.1

### 作業後環境
- Windows 10 pro
- VSCode 1.88.1
  - Dev Containers v0.354.0
- git for windows 2.45.0

### 準備
- VSCode
  - VSCode はインストール済みだったので省略。
- Git
  - 以前、業務で使用していたが自端末には未インストールだった
    - [Windows10でGitHubを始める～①Gitインストール](https://qiita.com/emiki/items/c0aa0b4da4b63921b153 "Windows10でGitHubを始める～①Gitインストール")を参考にサクッとインストール。
  - アカウント類は自習用に持っていたのでそのまま使用。

### DevContainer の導入

#### [公式チュートリアル](https://code.visualstudio.com/docs/devcontainers/containers "公式チュートリアル")に従って DockerDesktop からインストールする  

公式からダウンロードしたインストーラーを実行(ショートカット作成はお好みで)  
![DockerDesktop_install1](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/7018b39f-f179-400c-857f-fd581c35c932)
  
インストール中  
![DockerDesktop_install2](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/2f684efd-d579-44ae-b6fb-ae2abe9f627e)
  
完了  
![DockerDesktop_install3](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/779d9e27-dbbe-4148-ae5c-03256e23057e)
  
#### DevContainer のインストール

VSCode を起動し、EXTENSIONS で Dev Containers をインストールする  
![VSCode_install_DevContainer](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/c066ae7b-2746-47a7-b1db-be0fa41a036c)
  
完了  
![VSCode_dev_container_install](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/334e9507-565e-44e8-82f8-acdfe90a693e)
  
#### DevContainer を使用してみる

左下の >< をクリックして New Dev Container を選択  
![VSCode_new_dev_container](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/fbc104fb-b41b-47a7-934b-377df4959248)
  
出てきたコマンドリストは選ばずに……  
![VSCode_NewDevContainer](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/e8d2baa6-618f-4bb9-922c-285a6ae8d90f)
  
`F1`キーを押して表示されたリストから Try a Dev Container Sample を選択  
![VSCode_try_a_DevContainerSample](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/85df4646-b6a9-4f42-9a66-e08bf8fd2e04)
  
チュートリアルに従って一旦 Node を選択  
![VSCode_DevContainerSample_Node](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/258c0e1f-71ef-4221-90fc-3a02878db73e)
  
Node 環境の DevContainer が作成される  
![DevContainer_Node](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/0875ef92-fe24-4a24-8fc9-a3f1bced874c)
  
このまま`F5`で実行してみる  
![Node_F5](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/7c419f46-389a-4ff4-aaf3-5593280ce8e4)
  
Open in Browser ボタンを押すとブラウザで表示される  
![DevContainer_Node_sample](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/30ea418d-036a-41ef-9e72-005bb6d054ae)
  
一旦チュートリアル完了  
インストールされているものが LOCAL と DEV CONTAINER に分かれているのがわかる  
![DevContainer_EXTENSIONS](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/b5d76aad-133e-4b69-a8ed-2bca56b71df4)
  
### 本当にやりたかったこと

今回チュートリアルで手一杯になってしまったが、本来やりたいことがいくつかあった  

- GitHub からクローンしてきてビルドしたら使いたい開発環境ができている状態
  - ……の、出来上がったリポジトリ
- Unity
  - 開発環境の構築
  - チュートリアル
  - 業務利用の予備知識として役立つ程度に何か自作

### 感想

本来、コンテナ内で操作したことはコンテナ外のローカルファイルに内容が反映されるよう同期させる必要があるはず。  
必ずしもローカルに残る必要はなく、git push して GitHub に残して作業終了でもかまわないが。  
しかしながら現時点(2024/04/30)ではそこまで進められていない。  
以前から気になっていたが業務で関わる機会のなかった Rust や、  
業務利用している Flutter 、今後利用予定のある Unity を自習したいので、  
その事前準備として環境整備に着手したものの、これもそれなりに知識が必要であった。  
