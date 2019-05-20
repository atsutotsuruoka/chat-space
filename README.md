
# DB設計

## membersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique: true|
|mail|string|null: false|

### Association
- has_many :messages
- has_many :groups, through: :members
- has_many :members

## groupテーブル
|Column|Type|Options|
|------|----|-------|
|group_name|string|null: false, unique: true|
|user_id|integer|null: false, foreign_key: true|

### Association
- has_many :users, through: :members
- has_many :members

## messageテーブル
|Column|Type|Options|
|------|----|-------|
|body|text|
|image|string|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :user
