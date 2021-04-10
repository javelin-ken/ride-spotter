# テーブル設計

# usersテーブル

| Column             | Type   | Option                    |
| ------------------ | ------ | ------------------------- |
| nickname           | string | null: false               | 
| email              | string | null: false, unique :true |
| password           | string | null: false               |
| encrypted_password | string | null: false               |


### Association

- has_many :spots
- has_many :comments
- has_many :visits


# spotsテーブル

| Column        | Type   | Option      |
| ------------- | ------ | ----------- |
| name          | string | null: false | 
| prefecture_id | integer| null: false |
| highlight     | text   | null: false |


### Association

- has_many :comments
- has_many :visits
- belongs_to :user


# commentsテーブル

| Column  | Type       | Option                         |
| ------- | ---------- | ------------------------------ |
| text    | string     | null: false                    | 
| user    | references | null: false, foreign_key :true |
| post    | references | null: false, foreign_key :true |


### Association

- belongs_to :user
- belongs_to :spot


# visitsテーブル

| Column  | Type       | Option                         |
| ------- | ---------- | ------------------------------ |
| user    | references | null: false, foreign_key :true |
| post    | references | null: false, foreign_key :true |


### Association

- belongs_to :user
- belongs_to :spot