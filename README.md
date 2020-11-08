# テーブル設計

## usersテーブル

| Column         | Type    | Option      |
| -------------- | ------- | ----------- |
| email          | string  | null: false |
| password       | string  | null: false |
| nickname       | string  | null: false |
| name           | string  | null: false |
| first_name     | string  | null: false |
| last_name      | string  | null: false |
| first_furigana | string  | null: false |
| last_furigana  | string  | null: false |
| birth_year     | integer | null: false |
| birth_month    | integer | null: false |
| birth_day      | integer | null: false |

### Association

- has_many :items
- has_many :sold_items

## itemsテーブル

| Column           | Type       | Option                         |
| ---------------- | -----------| -------------------------------|
| item_name        | string     | null: false                    |
| description      | text       | null: false                    |
| category         | string     | null: false                    |
| status           | string     | null: false                    |
| fee_type         | string     | null: false                    |
| hassou           | string     | null: false                    |
| date_of_shipment | string     | null: false                    |
| price            | integer    | null: false                    |
| user             | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- has_one :sold_item

## sold_itemsテーブル

| Column       | Type       | Option                         |
| -------------| -----------| -------------------------------|
| postal_code  | string     | null: false                    |
| prefecture   | string     | null: false                    |
| city         | string     | null: false                    |
| address      | string     | null: false                    |
| building     | string     |                                |
| phone_number | string     | null: false                    |
| item         | references | null: false, foreign_key: true |
| user         | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :item