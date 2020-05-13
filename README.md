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
## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## messagesテーブル

|column|Type|Options|
|------|----|-------|
|body|text|validates_presence_of|
|image|string|validates_presence_of|
|group-id|integer|null: false, foreign_key: true|
|user-id|integer|null: false, foreign_key: true|

### Association

- belongs_to :user
- belongs_to :group

## usersテーブル

|column|Type|Options|
|------|----|-------|
|name|string|null: false|
|address|string|null: false, unique: true|
|password|string|null: false, unique: true|

### Association

- has_many :groupss, through: :groups_users
- has_many :messages
- has_many :groups_users

## groupsテーブル

|column|Type|Options|
|------|----|-------|
|name|string|null: false|

### Association

- has_many :users, through: :groups_users
- has_many :messages
- has_many :groups_users