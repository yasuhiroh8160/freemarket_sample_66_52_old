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
- has_many :trading
- has_many :comment
- has_many :like

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
- belong_to :category
- has_one :order
- has_many :comment
- has_many :like

## shippingテーブル
|Column|Type|Options|
|------|----|-------|
|method|varchar|null: false|
|prefecture_from|varchar|null: false|
|period_before_shipping|varchar|null: false|
|fee_burden|varchar|null: false|
### Association
- has_one :product



## imageテーブル
|Column|Type|Options|
|------|----|-------|
|url|varchar|null: false|
|product_id|intenger|null: false, foreign_key: true|
### Association
- belong_to :product


## statusテーブル
|Column|Type|Options|
|------|----|-------|
|name|varchar|null: false|
### Association
- has_many :product


## stateテーブル
|Column|Type|Options|
|------|----|-------|
|name|varchar|null: false|
### Association
- has_many :product



## sizeテーブル
|Column|Type|Options|
|------|----|-------|
|name|varchar|null: false|
### Association
- has_many :product


## categoryテーブル
|Column|Type|Options|
|------|----|-------|
|name|varchar|null: false|
|parent_id|string|null: false|
|grandparent_id|string|null: false|
### Association
- has_many :product

## orderテーブル
|Column|Type|Options|
|------|----|-------|
|status|intenger|null: false|
|trading_id|intenger|null: false, foreign_key: true|
|product_id|intenger|null: false, foreign_key: true|
### Association
- has_one :order
- belong_to :trading


## tradingテーブル
|Column|Type|Options|
|------|----|-------|
|seller_id|intenger|null: false|
|buyer_id|intenger|null: false|
### Association
- belong_to :user
- has_many :order
- has_many :review

## reviewテーブル
|Column|Type|Options|
|------|----|-------|
|body|varchar|null: false|
|rating|intenger|null: false|
|trading_id|intenger|null: false, foreign_key: true|
### Association
- belong_to :trading

## commentテーブル
|Column|Type|Options|
|------|----|-------|
|body|longtext|null: false|
|user_id|intenger|null: false, foreign_key: true|
|product_id|intenger|null: false, foreign_key: true|
### Association
- belong_to :user
- belong_to :product

## likeテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|intenger|null: false, foreign_key: true|
|product_id|intenger|null: false, foreign_key: true|
### Association
- belong_to :user
- belong_to :product


## brand_groupテーブル
|Column|Type|Options|
|------|----|-------|
|name|varchar|null: false|
### Association
- has_many :brand


## brandテーブル
|Column|Type|Options|
|------|----|-------|
|name|varchar|null: false|
|brand_group_id|intenger|null: false|
### Association
- belong_to :brand_group


