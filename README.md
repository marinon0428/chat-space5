# CHAT-SPACE DB設計

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|email|string|null: false|
|password|string|null: false|
### Association
- has_many :groups,through:group_users
- has_many :groups-users
- has_many :comments


## commentsテーブル
|Column|Type|Options|
|------|----|-------|
|image|string|null: false|
|text|text|null: false|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :groups


## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|group_id|integer|null: false, unique: true|
### Association
- has_many :comments
- has_many :group_users
- has_many :users,through:group_users


## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user