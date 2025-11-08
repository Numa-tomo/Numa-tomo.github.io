# gitの機能およびコマンド

## コミット
- [ファイル作成/変更/削除]の記録
- 変更を登録するのみ,実際に適用するのは別
- git commit "コミットを適用するファイル名" -m "メッセージ"

## ブランチ
- 作業を枝分かれさせることができる
- 枝分かれの図をフローと呼ぶ

## gitの設定
- git config global: 現在の設定を確認する
- git config global user.name "使用するユーザ名": usernameの登録
- git config global user.email "使用するメールアドレス": mailadressの登録
- .gitignore: gitに管理してほしくないファイルの指定
- git branch --set-upstream-to origin/main: リモートブランチを紐付ける設定

## 共同編集時に使用するコマンド
- git diff origin -- index.html: originにあるindex.htmlとローカルのindex.htmlの比較
- git stash: 一時退避
- git pull: originからpull(同期)
- git stash pop: 一時退避したものの変更を加える
### ブランチマージのコンフリクトの対処例
- git merge --about
  - mainブランチを,マージを試行する前の状態に復元
  - git pullコマンドを実行して,マージ先の変更を取得
  - 新しいブランチを作成し,変更を行って,そのブランチをmainブランチにマージ
  - 変更をプッシュ

- git reset --hard
  - マージを開始する前の状態に戻す
  - 影響を受けたファイルにGitによって挿入された情報を使用して,手動で解決

## gitコマンドまとめ
### 設定・確認系
- git init: gitの初期化・設定開始
- git status: ワークツリーのステータスを表示
- git config: 設定周りの確認・変更
- git log: ログを表示, --onelineでコミットメッセージの1行のみの一覧表示
- git diff: ファイルの差分を表示
### コミット系
- git add [ディレクトリ名(現在の位置であれば'.'でよい)]: ステージングエリアに追加
- git commit: コミットの実行
### 修正系
- git commit --amend --no-edit: コミットの修正
- git checkout: 削除されたファイルの復旧や過去コミットの復元など
- git reset: コミットのリセット
- git revert: 「コミットの変更を打ち消す」コミット
- git rm: ファイルとindex情報の削除
### リモート系
- git clone: レポジトリをコピー
- git pull: リモートレポジトリの同期
  - git pull origin [ReomteBranch]:[LocalBranch]: 特定のローカルブランチを特定のリモートブランチと同期する
- git push: 変更をアップロードする
- git request-pull: プルリクエスト:変更依頼
- git remote: リモートレポジトリの設定
### ブランチ系
- git branch: ブランチの作成
  - git branch -u origin/[RemoteBranch]: 現在のローカルブランチに特定のリモートレポジトリを追跡設定する(これで`git pull`コマンドのみでそのリモートレポジトリと同期できる)
- git checkout: ブランチの切り替え
- git merge: ブランチの統合
  - --ff-only: fast forward only. 変更のない統合先ブランチにマージ
- git clone \[GitHub URL\]: リモートレポジトリをローカルレポジトリにコピー
- git push: 変更をアップロードする

## GitHubのcloneとforkの違い
- `fork`: (他人の)レポジトリをコピーして自分のアカウントに持ってくるもの
- `clone`: GitHub上のレポジトリ(リモート)をPCのディレクトリ(ローカル)にコピーしてそのPCで編集ができるようにするもの
