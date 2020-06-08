# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false, add_index|
|password|string|null: false|
|name|string|null: false, add_index|
### Association
- has_many :posts
- has_many :comments
- has_many :groups

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|text|text|
### Association
- belongs_to :user
- has_many :comments
- has_many :posts

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user

## postsテーブル
|Column|Type|Options|
|------|----|-------|
|title|text|null: false|
|text|text|null: false|
|user_id|references|null: false, foreign_key: true|
### Association
- belongs_to :user
- has_many :comments
- has_many :posts_tags
- has_many  :tags, through:  :posts_tags

## tagsテーブル
|Column|Type|Options|
|------|----|-------|
|text|text|null: false|
### Association
- has_many :posts_tags
- has_many :posts, through:  :posts_tags

## posts_tagsテーブル
|Column|Type|Options|
|------|----|-------|
|post_id|references|null: false, foreign_key: true|
|tag_id|references|null: false, foreign_key: true|
### Association
- belongs_to :post
- belomgs_to :tag

## commentsテーブル
|Column|Type|Options|
|------|----|-------|
|body|text|---------|
|image|string|------|
|user_id|references|null: false, foreign_key: true|
|group_id|refernces|null: false, foreign_key: true|
### Association
- belongs_to :post
- belongs_to :user

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...
