# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

# chat-space DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null:false|
|email|string|null: false|
|password|string|null: false|
|password combination|string|null: false|

### Association
- has_many :comments
- has_many :group_users
- has_many  :groups,  through:  :groups_users

## messageテーブル
|Column|Type|Options|
|------|----|-------|
|body|text||
|user_id|integer|null: false, foreign_key: true|
|image|string| |
|groups_id|integer|null: false,foreign_key: true

### Association
- belongs_to :group
- belongs_to :user


## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false

### Association
- has_many :messages
- has_many :group_users
- has_many  :users,  through:  :group_users

## groups_users
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|grops_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group
