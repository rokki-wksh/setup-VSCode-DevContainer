# setup-VSCode-DevContainer day3

## 目標

### 自分が欲しい開発環境の DevContainer を作成する

- 1つのGitリポジトリとしてまとまったプロジェクトを作る
  - クローンしてすぐ使える状態になっていること

[day2](../day2/README.md) で手を動かす量が少なすぎて理解が捗らなかったため  
色々と試行錯誤してみる

## 試行した手順等

### プロジェクト内に `.devcontainer` を作る

1. Add Dev Container Configuration Files
  - この setup-VSCode-DevContaier リポジトリをプロジェクトとして利用したい
  - Add で良いはず

1. Add Configuration to workspace
  - プロジェクト内に設定ファイルを置きたいので `to workspace`

1. あとは一旦、初期選択値のまま進める
  - まずは構造を理解する
[Alpine]
[3.19]
[additional features : none]

1. 完了
  - `.devcontainer/devcontainer.json` が作成された
  - `.github` もできている

### コンテナの起動

`.devcontainer` ができたので、その設定でコンテナが起動できるはず

1. Reopen in Container

1. できたっぽい
  - `Dev Container: Alpine` になっている
  - workspace 内に元々あったファイル群が見えている
  - Changes に commit 済みファイルが見えるようになったのは何？
    - `.github ` が関係あり？
    - 同じリモートリポジトリ見るようになっていないかも？
      - 各所に`ホストの設定を引き継ぐ`と書かれているので大丈夫そうではある

1. commit, push してみる
  - try and error の精神で


