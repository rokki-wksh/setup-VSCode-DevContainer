# setup-VSCode-DevContainer day3

## 目標

### 自分が欲しい開発環境の DevContainer を作成する

- 1つのGitリポジトリとしてまとまったプロジェクトを作る
  - クローンしてすぐ使える状態になっていること

[day2](../day2/README.md) で手を動かす量が少なすぎて理解が捗らなかったため  
色々と試行錯誤してみる

## 試行した手順等

### プロジェクト内に `.devcontainer` を作る

#### Add Dev Container Configuration Files

- この setup-VSCode-DevContaier リポジトリをプロジェクトとして利用したい  
- Add で良いはず  
![2024-05-02_094240_](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/1e24690f-6be0-4bc1-9f8a-0438f0462561)  

#### Add Configuration to workspace

- プロジェクト内に設定ファイルを置きたいので `to workspace`  
![2024-05-02_094334_](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/5ed58736-1281-4bc6-8b98-f913ae4df05d)  

#### あとは一旦、初期選択値のまま進める

- まずは構造を理解する  
![2024-05-02_094434_](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/3b8b82f2-3ea3-4447-9bff-ab78cb106353)  
![2024-05-02_094450_](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/f78166ca-8391-432e-92a9-ab8b17bbdec0)  
![2024-05-02_094546_](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/d73aa39f-fd36-43ad-b5fe-470c8398017b)  

#### 完了

- `.devcontainer/devcontainer.json` が作成された  
- `.github` ができている  
![2024-05-02_094609](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/43e8c0e8-bd7c-47c7-9386-bb6319d194f6)  

### コンテナの起動

`.devcontainer` ができたので、その設定でコンテナが起動できるはず

#### Reopen in Container

![2024-05-02_095858_](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/f95acd28-5021-4d0d-8d6d-44cb92f4dd5a)  
![2024-05-02_095953](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/e092076a-a16f-4dde-ad39-43d27f49fde1)  
![2024-05-02_100039](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/d09d582c-1600-4588-a846-deb4955c8b38)  

- できたっぽい
  - `Dev Container: Alpine` になっている
  - workspace 内に元々あったファイル群が見えている
  - Changes に commit 済みファイルが見えるようになったのは何？
    - `.github ` が関係あり？
    - 同じリモートリポジトリ見るようになっていないかも？
      - 各所に`ホストの設定を引き継ぐ`と書かれているので大丈夫そうではある

#### commit, push してみる

- try and error の精神で  
![2024-05-02_111534](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/283fcda7-caec-4788-99ce-c739242f5eb0)  
- 大丈夫そう

### 拡張機能のインストール

コンテナ内で VSCode に拡張機能をインストールした状態を main にマージする  
新規でリポジトリをクローンして同じ環境が構築されるところまで確認する  

#### 試しに Unity 環境をインストールする
- 元々 Unity 環境を作りたくて始めた環境構築なので Unity 環境を作る
- インストール前の状態
  - LOCAL - INSTALLED : 2件
    - Dev Containers
    - WSL
  - DEV CONTAINER: ALPINE - INSTALLED : 0件  
![2024-05-02_113522](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/1e108139-fbd7-4ed3-a7ee-af7e61dd2bb8)  

- Unity 環境を作っているサイトにならって進めてみる
  - 参照 : [【VsCode】Unity＆C#を効率よく開発するための拡張機能のすゝめ](https://zenn.dev/tmb/articles/1444e0a85543e5)
  - 一旦、一通り最新バージョンで入れる
    - やりたいことに合わせてバージョン調整が必要であればその時に考える
  - 入れたもの
    - C#
    - C# Snippets
    - C# XML Documentation Comments
    - Unity Code Snippets
    - Trailing Spaces
    - GitLens
  - C# Snippets だけなぜか LOCAL に入ったよう
    - これはやりたいことと違うので対処したい  
![2024-05-02_125829](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/7d121ff6-baa4-4366-b77b-8e32c577a8cc)  

#### C# Snippets を DEV CONTAINER 側にインストールする
- 一旦アンインストール
- `Install` ボタンの横の歯車から `Add to devcontainer.json`  
![2024-05-02_130452_](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/df13f5fe-5f91-41e2-9314-3277ccec552b)  
- 通知が出たので `Rebuild` してみる  
![2024-05-02_130645](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/29ddeee8-f68f-4b5a-b33f-466526677bf3)  
- Rebuild 後
※キャプチャ撮り忘れ  
  
Rebuild した結果、それまで DEV CONTAINER 側にインストール表示されていた拡張機能が消え、  
`Add to devcontainer.json` した `C# Snippets` のみ表示された。なるほど。  
  
`Install` でコンテナ側にインストールされても `devcontainer.json` に追記されていないため、  
リビルドすると消える ＝ 新規参画者が初回ビルドしてもインストールされない。  
`Install` ボタン横の歯車から簡単に `devcontainer.json` に追記できる。  
……ということのよう。  

#### `devcontainer.json` に追記されるように拡張機能を入れなおす

- それぞれ `Add to devcontainer.json` していく  
![2024-05-02_133917](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/5d399f05-5f9a-41fd-a3f4-d445a633c620)  
- 追加し終わったらリビルドする
  - 左下の `><` から `Rebuild Container`  
![2024-05-02_132520_](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/0b2135bc-7da2-4be0-b1b6-fd83ad323786)  
- 完了

#### main にマージして（新規参画者想定で）クローンしなおす

何も入っていない端末に Git、Docker、VSCode、DevContainer だけインストールして、  
その他必要なものはプロジェクトに全部設定が入っている状態が理想。その想定。  

- 任意のフォルダを作成し、`git clone`  
![2024-05-02_143208](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/23457d1e-37b7-4908-9938-e8a2e682c66c)  
- VSCode で開く  
![2024-05-02_143539](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/f113aa68-9b1f-4d34-8349-26566cc6e94b)  
- `Reopen in Container`  
![2024-05-02_143555_](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/018c425e-8e44-480a-a61b-1a4f03df5f10)  
- 完成
![2024-05-02_143636](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/f1357549-fca5-4155-a657-6cf04827b2ed)  

## 追加対応

### 拡張機能のバージョンを指定してインストールするには？

[【VsCode】Unity＆C#を効率よく開発するための拡張機能のすゝめ](https://zenn.dev/tmb/articles/1444e0a85543e5) によると  
その時点では C# のバージョンは`v2.14.8`が必要とのこと。  
ここまでの手順では最新版をインストールし、`devcontainer.json` にもバージョンの記載などないのでバージョン指定が必要な場合、  
どういう設定を記述する必要があるのか確認しておく必要があると感じた。  

### 試行

#### `Install Another Version`

`Uninstall` しようかと思ったが `Install Another Version` があったので試してみる。  
もしかしたらそこで指定したバージョンが設定に追記されるかもしれない。  
![2024-05-02_163827_](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/367e3333-608a-497d-8526-013072d59f30)  
![2024-05-02_163815_](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/301c5966-315a-4feb-a946-20ba03193ed2)  

`devcontainer.json` が変更されなかったのでこれは違ってそう。  
-> `Rebuild Container` をしたら最新版に戻ってしまった。  

#### インストール時に何か指定できるか

一旦アンインストールして、インストール時に選択できる箇所があるか確認する。  
-> 無さそう。

#### `` を編集してバージョン指定を付与できるか

[.devcontainer.json で拡張機能のバージョンを指定する機能](https://github.com/microsoft/vscode-remote-release/issues/3253)  
拡張機能の末尾に`@バージョン番号`でできそう？  
試しに `@2.14.8` をつけてリビルドしてみる。  
![2024-05-02_170552](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/fdfd2045-e119-4218-b4bb-a99aa3341af0)  

-> できた！  
![2024-05-02_170754](https://github.com/rokki-wksh/setup-VSCode-DevContainer/assets/78457029/8bf0c517-3a3f-42de-8cfc-908e81059511)  

### 感想

構築時点の最新版をインストールするとしても、ビルドするタイミングによってインストールされるバージョンが異なるのは  
今回やりたいことから外れてしまっている。環境依存を避けたいという目的の中にはバージョン差異によって生じる種々の事象が  
発生するのを避けたい意図も含む。  
そうなると本日実施した手順では最新版を入れてそのままの `devcontainer.json` の記述にしてあるのがほとんどだが、  
全て`@バージョン番号`を付与する必要がある。  
