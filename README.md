# README
# chat-space DB設計

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_name|string|null: false, unique: true|
|email|string|null: false, unique: true|
|password|string|null: false|
### Association
- has_many :groups, through: :groups_users
- has_many :messeages

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|group_name|integer|null: false, foreign_key: true|
### Association
- has_many :messeages
- has_many :users, through: :groups_users

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user

## messeageテーブル
|Column|Type|Options|
|------|----|-------|
|body|text|null: false|
|image|string|foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user

