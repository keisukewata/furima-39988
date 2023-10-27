# テーブル設計

## users テーブル

| Column             | Type      | Options                   |
| ------------------ | ----------| ------------------------- |
| nickname           | string    | null: false               |
| email              | string    | null: false, unique: true |
| encrypted_password | string    | null: false               |
| last_name          | string    | null: false               |
| first_name         | string    | null: false               |
| furigana_last_name | string    | null: false               |
| furigana_first_name| string    | null: false               |
| birthday           | date      | null: false               |

 
### Association
- has_many :items
- has_many :purchase_records

## items テーブル

| Column                  | Type       | Options                        |
| ---------------------   | ---------- | ------------------------------ |
| name                    | string     | null: false                    |
| explanation             | text       | null: false                    |
| category_id             | integer    | null: false                    | 
| condition_id            | integer    | null: false                    |
| region_id               | integer    | null: false                    |
| delivery_fee_payment_id | integer    | null: false                    |
| period_id               | integer    | null: false                    |
| price                   | integer    | null: false                    |
| user                    | references | null: false, foreign_key: true |

### Association
- belongs_to :user
- has_one :purchase_record

## purchase_records テーブル

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| user    | references | null: false, foreign_key: true |
| item    | references | null: false, foreign_key: true |
 
### Association
- belongs_to :user
- has_one :shipping_info
- belongs_to :item


## shipping_infos テーブル

| Column          | Type       | Options                      |
| ----------------| ---------- | -----------------------------|
| postal_code     | string     | null:false                   |
| region_id       | integer    | null:false                   |
| city            | string     | null:false                   |
| address         | string     | null:false                   |
| building        | string     |                              |
| phone_number    | string     | null:false                    | 
| purchase_record | references | null:false, foreign_key: true|


### Association
- belongs_to :purchase_record

