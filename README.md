# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...


## userテーブル
|Column|Type|Options|
|------|----|-------|
|nickname|varchar|null: false|
|email|varchar|null: false|
|password|varchar|null: false|
### Association
- has_many :sns_credentials
- has_one :profile
- has_one :creditcard
- has_many :product

## sns_credentialsテーブル
|Column|Type|Options|
|------|----|-------|
|token|longtext|null: false|
|uid|varchar|null: false|
|provider|varchar|null: false|
|user_id|intenger|null: false, foreign_key: true|
### Association
- belong_to :user


## profileテーブル
|Column|Type|Options|
|------|----|-------|
|body|mediumtext|null: false|
|last_name|varchar|null: false|
|first_name|varchar|null: false|
|last_name_kana|varchar|null: false|
|first_name_kana|varchar|null: false|
|birth_year|varchar|null: false|
|birth_month|varchar|null: false|
|birth_day|varchar|null: false|
|phone_namber|varchar|null: false|
|zipcode|varchar|naull: false|
|prefecture|varchar|null: false|
|city|varchar|null: false|
|district|varchar|null: false|
|building|varchar|null: false|
|user_id|intenger|null: false, forein_key: true|
### Association
- has_one :user


## creditcardテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|intenger|null: false, foreign_key: true|
|token|longtext|null:false|
### Association
has_one :user


## productテーブル
|Column|Type|Options|
|------|----|-------|
|name|varchar|null: false|
|price|varchar|null: false|
|description|varchar|null: false|
|brand|varchar|null: false|
|shipping_id|intenger|null: false, foreign_key: true|
|category_id|intenger|null: false, foreign_key: true|
|size_id|intenger|null: false, foreign_key: true|
|state_id|intenger|null: false, foreign_key: true|
|status_id|intenger|null: false, foreign_key: true|
|user_id|intenger|null: false, foreign_key: true|
### Association
- belong_to :user
- has_one :shipping
- has_many :image
- belong_to :status
- belong_to :state
- belong_to :size

## shippingテーブル
|Column|Type|Options|
|------|----|-------|

### Association
- has_one :product



## imageテーブル
|Column|Type|Options|
|------|----|-------|

### Association
- belong_to :product


## statusテーブル
|Column|Type|Options|
|------|----|-------|

### Association
- has_many :product


## stateテーブル
|Column|Type|Options|
|------|----|-------|

### Association
- has_many :product



## sizeテーブル
|Column|Type|Options|
|------|----|-------|

### Association
- has_many :product


## categoryテーブル
|Column|Type|Options|
|------|----|-------|

### Association
- 

## テーブル
|Column|Type|Options|
|------|----|-------|

### Association
- 


## テーブル
|Column|Type|Options|
|------|----|-------|

### Association
- 