# concept
- 調剤事務を仕事にしている方々向けの情報交換・質問アプリ
- content(質問・情報)に対してコメントがいくつあるかindexに表示

# DB設計

## usersテーブル(ユーザー管理)
| Column     | Type    | Options     |
| ---------- | ------- | ----------- |
| name       | string  | null: false |
| address_id | integer | null: false |
| email      | string  | null: false, unique: true |
| password   | string  | null: false |

### Association
- has_many :contents
- has_many :comments

## contentsテーブル（情報及び質問の管理）
| Column  | Type       | Options     |
| ------- | ---------- | ----------- |
| title   | string     | null: false |
| article | text       | null: false |
| user    | references | null: false |

### Association
- belongs_to : user
- has_many :comments

## commentsテーブル(コメント機能) 
| Column     | Type       | Options     |
| ---------- | ---------- | ----------- |
| comment    | text       | null: false |
| user       | references | null: false |
| address_id | integer    | null: false |

### Association
- belongs_to :user
- belongs_to :content