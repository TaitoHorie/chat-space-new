# chat-space DB設計


## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|strig|null: false, foreign_key: true|
|email|string|unique: true|
|password|string||
|created_at|datetime||

### Association
- has_many :messages
- has_many :group_users
- has_many groups, through: :group_users

## messsagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|text||
|image|string||
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|
|created_at|datetime||

### Association
- belongs_to :user
- belongs_to :group

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, foreign_key: true|

### Association
- has_many :messages
- has_many :group_users
- has_many :users through: :group_users

## group_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group