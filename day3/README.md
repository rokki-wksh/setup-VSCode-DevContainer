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

#### Add Configuration to workspace

- プロジェクト内に設定ファイルを置きたいので `to workspace`  

#### あとは一旦、初期選択値のまま進める

- まずは構造を理解する  
[Alpine]
[3.19]
[additional features : none]

#### 完了

- `.devcontainer/devcontainer.json` が作成された  
- `.github` もできている  

### コンテナの起動

- `.devcontainer` ができたので、その設定でコンテナが起動できるはず

#### Reopen in Container

- できたっぽい
  - `Dev Container: Alpine` になっている
  - workspace 内に元々あったファイル群が見えている
  - Changes に commit 済みファイルが見えるようになったのは何？
    - `.github ` が関係あり？
    - 同じリモートリポジトリ見るようになっていないかも？
      - 各所に`ホストの設定を引き継ぐ`と書かれているので大丈夫そうではある

#### commit, push してみる

- try and error の精神で
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

#### C# Snippets を DEV CONTAINER 側にインストールする
- 一旦アンインストール
- `Install` ボタンの横の歯車から `Add to devcontainer.json`
- 通知が出たので `Rebuild` してみる
- Rebuild 後
  
Rebuild した結果、それまで DEV CONTAINER 側にインストール表示されていた拡張機能が消え、  
`Add to devcontainer.json` した `C# Snippets` のみ表示された。なるほど。  
  
`Install` でコンテナ側にインストールされても `devcontainer.json` に追記されていないため、  
リビルドすると消える ＝ これから使おうとする人が初回ビルドしても入ってこない。  
`Install` ボタン横の歯車から簡単に `devcontainer.json` に追記できる。  
……ということのよう。  

#### `devcontainer.json` に追記されるように拡張機能を入れなおす

- それぞれ歯車から `Add to devcontainer.json` していく
- 追加し終わったらリビルドする
- 左下の `><` から `Rebuild Container`
- 完了

#### main にマージして（新規参画者想定で）クローンしなおす

何も入っていない端末に Git、Docker、VSCode、DevContainer だけインストールして、  
その他必要なものはプロジェクトに全部設定が入っている状態が理想。その想定。  

