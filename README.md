## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group

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
|image|string||
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true| 
|body|text||

### Association
- belongs_to :user
- belongs_to :group

### groups
|Column|Type|Options|
|------|----|-------|
|name|string|null: false,unique: true, index: true|

### Association
- has_many :messages
- has_many :groups_users
- has_many :users,through: :groups_users
