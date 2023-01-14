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
| birth_date         | string              | null: false               |

### Association

- has_many :items
- has_many :buys

## items table

| Column                              | Type       | Options                        |
|-------------------------------------|------------|--------------------------------|
| title                               | string     | null: false                    |
| category                            | string     | null: false                    |
| text                                | text       | null: false                    |
| image                               | references | null: false, foreign_key: true |
| condition                           | string     | null: false                    |
| delivery_charge                     | string     | null: false                    |
| sender_area                         | string     | null: false                    |
| delivery_time                       | string     | null: false                    |
| price                               | string     | null: false                    |
| user                                | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- has_one :buys

## buys table

| Column      | Type       | Options                        |
|-------------|------------|--------------------------------|
| user        | references | null: false, foreign_key: true |
| item        | references | null: false, foreign_key: true |

### Association

- belongs_to :prototype
- belongs_to :user

## addresss table

| Column        | Type       | Options                        |
|-------------- |------------|--------------------------------|
| postal_code   | string     | null: false, foreign_key: true |
| prefecture    | string     | null: false, foreign_key: true |
| municipality  | string     | null: false,                   |
| house_number  | string     | null: false,                   |
| building_name | string     |                                |
| tel           | string     | null: false,                   |
| user          | references | null: false, foreign_key: true |
| item          | references | null: false, foreign_key: true |

- belongs_to :buy