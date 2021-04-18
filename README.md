# 🟢chat-ranch
###自分の趣味や悩みなどなんでもこのchat-ranchに書き込んで人々が繋がってくれたらいいなと思いから作成したアプリケーションです。

![toppage]
(https://gyazo.com/e3763050f4e43d1db19fc84dfd37af29)

#概要
### 自分のchatroomを作る事ができる
好きなだけchatroomを作る事ができ話したい話題ごとにchatroomを作成し、共通の話題についてみんなでchatすることができる。

# 🌍App URL
### **https://chat-ranch.herokuapp.com/**

#　利用方法
#### トップページから新規登録〜サインイン
(https://gyazo.com/ccd3e88f543b7abf3d7842f73879266b)
(https://gyazo.com/279f4374cad7d908ba8c63043ea28e42)
#### チャットを作成する　を押しチャットルームを作成
#### ページ下部にある投稿フォームより投稿
#### room名をクリックするとクリックしたroomに入室できる
#### チャットを終了する　をクリックでchat-roomの削除、終了となる

# 機能一覧
ユーザー管理機能（新規登録・ログイン・ログアウト機能）
チャットルーム管理機能（チャットルームの新規作成・削除機能）
メッセージ管理機能（テキスト投稿・画像投稿機能）

# 追加したい機能
ユーザーのフォロー機能追加
動画投稿機能の追加

# 開発環境
- VScode
- Ruby 2.6.5
- Rails 6.0.0
- mysql2 0.4.4
- gem 3.0.3
- heroku 7.47.7

# テーブル設計

## users テーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| name     | string | null: false |
| email    | string | null: false |
| password | string | null: false |

### Association

- has_many :room_users
- has_many :rooms, through: room_users
- has_many :messages

## rooms テーブル

| Column | Type   | Options     |
| ------ | ------ | ----------- |
| name   | string | null: false |

### Association

- has_many :room_users
- has_many :users, through: room_users
- has_many :messages

## room_users テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| user   | references | null: false, foreign_key: true |
| room   | references | null: false, foreign_key: true |

### Association

- belongs_to :room
- belongs_to :user

## messages テーブル

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| content | string     |                                |
| user    | references | null: false, foreign_key: true |
| room    | references | null: false, foreign_key: true |

### Association

- belongs_to :room
- belongs_to :user