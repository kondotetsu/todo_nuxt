# ポートフォリオ紹介

「Clean City」はゴミ拾い活動を活性化させたいと思い作成したアプリケーションです。<br>
Twitterクローンに近く、さらにイベントを組み合わせたSNSアプリです。<br>
ゲストログインもありますので気軽に楽しんでください。

https://todonuxt-front.herokuapp.com/


# 制作背景

学校や職場、家の近くなどで当たり前に見かけるポイ捨てごみ。<br>
ボランティアで拾ってくれる方々もいますが、それでも集めきれないゴミの量。<br>
ボランティアの方を少しでもサポートしたい、もっとゴミ拾いの活動の輪を広げていきたい<br>
さらにSDGsの項目「海の豊かさを守ろう」「住み続けられるまちづくりを」「つくる責任つかう責任」の後押しにつながればと思い作成しました。

# サービスの特徴

このサービスはSNSとイベント二つを軸に構成されており、<br>
つぶやきでゴミ拾いの記録をつけ、コメントでメッセージを送り合う。<br>
イベントでは参加者と一緒にゴミ拾いを行い、同じ目的を持った仲間ができます。


# トップページ(つぶやき)

![toppage.jpg](https://user-images.githubusercontent.com/77315028/134213355-fb4ddd68-d795-4063-8739-77ff32ed8dc7.jpg)

# イベント

![event.png](https://user-images.githubusercontent.com/77315028/134344404-69874592-b23b-4d28-9363-31d332fc9afb.png)

# Ajax処理

![Ajax.gif](https://user-images.githubusercontent.com/77315028/134439445-761bad4c-4c7e-4a9b-8ebe-f54d6399c1de.gif)

# 使用技術

各バージョン
- Ruby 2.7.2
- Rails 6.0.4.1
- nuxt 2.13.3
- @nuxtjs/vuetify 1.11.3
- Docker 20.10.8
- docker-compose 1.29.2

#### フロントエンド
| 名称 | 説明 |
| ---- | ---- |
| Nuxt.js | フロントエンドフレームワーク |
| Vuetify | UIコンポーネント |
- Vuetifyコンポーネントを導入することで、レスポンシブデザインを実現。

- ログイン機能はNuxt.jsのAuth Module使ってログイン機能を実装

- 未ログイン状態でアクセスして欲しくないページ（ /users/editなど ）へのアクセス対策には、Nuxt.jsのmiddlewareを活用することで自動的にリダイレクトするようにしました。

- ログイン状態でアクセスして欲しくないページ （ログインページ, 新規作成ページ） へのアクセスも同じくリダイレクトします。
#### バックエンド
| 名称 | 説明 |
| ---- | ---- |
| Rails (API mode) | APIサーバーとして利用 |
| PostgreSQL | データベース |
- RailsはAPIサーバーとして利用しており、フロントエンドコンテナからのリクエストに対してJSONデータを返しています。
- 画像データはActiveStorage経由でS3バケットに保存。

#### テストコード
| 名称 | 説明 |
| ---- | ---- |
| RSpec | バックエンドテスト |
- modelとcontrollerのバリデーションのテストのみ

#### インフラ
| 名称 | 説明 |
| ---- | ---- |
| Heroku |  レンタルサーバー |
| Docker, Docker-compose | コンテナ環境 |
| Github | バージョン管理 |
- ローカル開発環境からデプロイまで一貫してDockerを使用。

# DB設計

![DB設計.png](https://user-images.githubusercontent.com/77315028/134330743-24d7c6d3-f22d-4fe0-80ce-4c7c994a356c.png)

# アプリの機能紹介
| 機能名 | 説明 |
|----|----|
| ユーザー機能 | 新規登録、登録内容変更、アバター登録、アバター変更、ログイン、ログアウト |
| つぶやき機能 | 投稿、削除、画像登録 |
| つぶやきコメント機能 | つぶやきに対してのコメント投稿,コメントへのリプライ、削除 |
| つぶやきいいね機能 | いいねできる、自分がいいねしたつぶやきを一覧できる いいね外しができる |
| イベント機能 | 一覧、投稿、編集、削除 |
| イベントコメント機能 | イベント詳細でコメント投稿、コメントへのリプライ、削除 |
| イベント参加機能 | イベントへの参加ができる、ユーザー名が表示、参加のキャンセルができる |
| 市区郡検索機能 | 市区郡別で検索が可能 |
| 投稿機能 | Ajaxで処理を行なっています。 |


# 苦労したところ

| 苦労したところ | 理由 |
|----|----|
| AuthModuleログイン機能 | エラーが頻発し動作させるまでに苦労しました。 |
| 親コンポーネントと子コンポーネントのデータ受け渡し | propsとemitのデータ受け渡しの理解に苦労しました。 |
| vuexの仕組み | state,getters,mutations,actionsの仕組みの理解に時間がかかりました。 |
| 命名規則 | 命名規則の理解が曖昧まま作業をしており、キャメルケースを用いた記述をしているのに気づくのが遅れてしまいました。 |
| Herokuでのエラー | applicationerrorが発生し、解決までに1週間ほどかかってしまいました。 （備忘録としてQiitaにまとめました)|

# 最後に

大変お忙しい中、最後までご覧いただき誠にありがとうございました。<br>
ご興味を持っていただけましたら、下記リンクもご覧頂けると幸いです。<br>
[→[Qiita](https://qiita.com/TETSU33):発信力を持ったエンジニアになるべく今後は学んだことをドシドシ投稿していきます！]
