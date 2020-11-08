# テーブル設計

## usersテーブル

| Column             | Type    | Option      |
| ------------------ | ------- | ----------- |
| email              | string  | null: false |
| encrypted_password | string  | null: false |
| nickname           | string  | null: false |
| first_name         | string  | null: false |
| last_name          | string  | null: false |
| first_furigana     | string  | null: false |
| last_furigana      | string  | null: false |
| birthday           | date    | null: false |

### Association

- has_many :items
- has_many :sold_items

## itemsテーブル

| Column              | Type       | Option                         |
| ------------------- | -----------| -------------------------------|
| name                | string     | null: false                    |
| description         | text       | null: false                    |
| category_id         | integer    | null: false                    |
| status_id           | integer    | null: false                    |
| fee_type_id         | integer    | null: false                    |
| hassou_id           | integer    | null: false                    |
| date_of_shipment_id | integer    | null: false                    |
| price               | integer    | null: false                    |
| user                | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- has_one :sold_item
- belongs_to :category
- belongs_to :status
- belongs_to :fee-type
- belongs_to :hassou

## sold_itemsテーブル

| Column        | Type       | Option                         |
| ------------- | -----------| -------------------------------|
| item          | references | null: false, foreign_key: true |
| user          | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :item
- has_one :addresses

## addressesテーブル

| Column        | Type       | Option                         |
| ------------- | -----------| -------------------------------|
| postal_code   | string     | null: false                    |
| prefecture_id | integer    | null: false                    |
| city          | string     | null: false                    |
| address       | string     | null: false                    |
| building      | string     |                                |
| phone_number  | string     | null: false                    |
| sold_item     | references | null: false, foreign_key: true |

### Association

- belongs_to :sold_item
- belongs_to :prefecture