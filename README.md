# テーブル設計

## users テーブル

| Coloumn                       | Type    | Options      |
|-------------------------------|---------|--------------|
| name                          | string  | null: false  |
| email                         | string  | null: false  |
| encrypted_password            | string  | null: false  |

### Association

- has_many :room_users
- has_many :rooms, through: :room_users
- has_many :messages

## rooms テーブル

| Coloumn            | Type    | Options      |
|--------------------|---------|--------------|
|name                | string  | null: false  |

### Association

- has_many :users, through: :room_users
- has_many :room_users
- has_many :messages

## room_users テーブル
| Coloumn            | Type       | Options                        |
|--------------------|------------|--------------------------------|
|user                | references | null: false, foreign_key: true |
|room                | references | null: false, foreign_key: true |

### Assosiation

- belongs_to :user
- belongs_to :room


## messages テーブル

| Coloumn            | Type       | Options                        |
|--------------------|------------|--------------------------------|
| content            | string     |                                |
| user               | references | null: false, foreign_key: true |
| room               | references | null: false, foreign_key: true |

### Assosiation

- belongs_to :user
- belongs_to :room