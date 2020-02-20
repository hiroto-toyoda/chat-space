## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :user

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false,unique: true, index: true|
|email|string|null: false,unique: true|
|password|string|null: false,unique: true|

### Association
- has_many :groups,through: :groups_users
- has_many :messages
- has_many :groups_users

### messages
|Column|Type|Options|
|------|----|-------|
|image|string|null: false,unique: true, index: true|
|users_id|string|null: false,unique: foreign_key: true|
|groups_id|string|null: false,unique: foreign_key: true| 

### Association
- has_many :messages
- has_many :groups

### groups
|Column|Type|Options|
|------|----|-------|
|users_id|string|null: false, foreign_key: true|