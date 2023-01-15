# DB 設計

## users table

| Column             | Type                | Options                   |
|--------------------|---------------------|---------------------------|
| nickname           | string              | null: false               |
| email              | string              | null: false, unique: true |
| encrypted_password | string              | null: false               |
| last_name          | string              | null: false               |
| first_name         | string              | null: false               |
| last_name_kana     | string              | null: false               |
| first_name_kana    | string              | null: false               |
| birth_date         | date                | null: false               |

### Association

- has_many :items
- has_many :buys

## items table

| Column                              | Type       | Options                        |
|-------------------------------------|------------|--------------------------------|
| title                               | string     | null: false                    |
| category                            | string     | null: false                    |
| text                                | text       | null: false                    |
| condition_id                        | integer    | null: false                    |
| delivery_charge_id                  | integer    | null: false                    |
| prefecture_id                       | integer    | null: false                    |
| delivery_time_id                    | integer    | null: false                    |
| price                               | integer    | null: false                    |
| user                                | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- has_one :buy

## buys table

| Column      | Type       | Options                        |
|-------------|------------|--------------------------------|
| user        | references | null: false, foreign_key: true |
| item        | references | null: false, foreign_key: true |

### Association

- belongs_to :item
- belongs_to :user

## addresss table

| Column        | Type       | Options                        |
|-------------- |------------|--------------------------------|
| postal_code   | string     | null: false,                   |
| prefecture    | string     | null: false,                   |
| municipality  | string     | null: false,                   |
| house_number  | string     | null: false,                   |
| building_name | string     |                                |
| tel           | string     | null: false,                   |

- belongs_to :buy