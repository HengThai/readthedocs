# API - Special Account Number

## Introduction
API Endpoints for VIP Special Account Number:
1. `POST` OAuth Token
2. `POST` OAuth Refresh Token
3. `GET` Get List VIP Account
4. `PUT` Update Rule Price
5. `GET` Get List Rule
6. `POST` Reserve VIP Account Number

## 1. OAuth Token
Request to get `access_token` with username & password
```
POST /esb/oauth/token
```

### HEADERS
`Content-Type`
application/json

BODY raw
```
{
  "app_code": "VIP_ACCOUNT",
  "client_id": "a0741a0f-6d2a-4abe-aa18-5b0fc6ee98d0",
  "client_secret": "QSbO8SajhSn_f0KWveI0DSWe",
  "password": "HTB#9999",
  "username": "apiuser",
  "grant_type": "password"
}
```

### Example Request
```
curl --location --request POST 'http://172.16.28.75:8081/esb/oauth/token' \
--data-raw '{
    "app_code": "VIP_ACCOUNT",
    "client_id": "a0741a0f-6d2a-4abe-aa18-5b0fc6ee98d0",
    "client_secret": "QSbO8SajhSn_f0KWveI0DSWe",
    "password": "HTB#9999",
    "username": "apiuser",
    "grant_type": "password"
}'
```


## 2. OAuth Refresh Token
Request to get `access_token` with `refresh_token`
```
POST /esb/oauth/token
```

### HEADERS
`Content-Type`
application/json

BODY raw
```
{
    "app_code": "VIP_ACCOUNT",
    "client_id": "a0741a0f-6d2a-4abe-aa18-5b0fc6ee98d0",
    "client_secret": "QSbO8SajhSn_f0KWveI0DSWe",
    "grant_type": "refresh_token",
    "refresh_token": "d46ab7fd-5e8d-4f9b-938a-fc9a39e63d45"
}
```

### Example Request
```
curl --location --request POST 'http://172.16.28.75:8081/esb/oauth/token' \
--data-raw '{
    "app_code": "VIP_ACCOUNT",
    "client_id": "a0741a0f-6d2a-4abe-aa18-5b0fc6ee98d0",
    "client_secret": "QSbO8SajhSn_f0KWveI0DSWe",
    "grant_type": "refresh_token",
    "refresh_token": "d46ab7fd-5e8d-4f9b-938a-fc9a39e63d45"
}'
```


## 3. List VIP Account

```
GET /esb/rest_server/api/v1/vip-account/list?account={account}&min={min}&max={max}&query_count=N&page={page}&page_size={page_size}&search_type={search_type}
```

### HEADERS
`Content-Type`
application/json

`Authorization`
{access_token}

### PARAMS
`account`
Enter minimum 4 digits

`min`
Minimum price

`max`
Maximum price

`query_count` Return total records if `Y`, Not return total records if `N` 

`page`
Active page, default 1

`page_size`
Page size, default 10

`search_type`
Filter type (contain, start, end), default contain



### Example Request
```
curl --location --request GET 'http://172.16.28.75:8081/esb/rest_server/api/v1/vip-account/list?account=8888&min=&max=&query_count=N&page=&page_size=&search_type='
```

### HEADERS
`Content-Type`
application/json

`Authorization`
{access_token}

## 4. Update Rule Price
```
PUT /esb/rest_server/api/v1/vip-account/rule/update
```

### HEADERS
`Content-Type`
application/json

`Authorization`
{access_token}

BODY raw
```
{
    "id": 1,
    "price": 123,
    "name_en": "Special Reserve",
    "name_kh": "Special Reserve",
    "modified_by": "sys"
}
```

### Example Request
```
curl --location --request PUT 'http://172.16.28.75:8081/esb/rest_server/api/v1/vip-account/rule/update' \
--data-raw '{
    "id": 1,
    "price": 123,
    "name_en": "Special Reserve",
    "name_kh": "Special Reserve",
    "modified_by": "sys"
}'
```

## 5. Get List Rule
```
GET /esb/rest_server/api/v1/vip-account/rule/list
```

### HEADERS
`Content-Type`
application/json

`Authorization`
{access_token}


### Example Request
```
curl --location --request GET 'http://172.16.28.75:8081/esb/rest_server/api/v1/vip-account/rule/list'
```

## 6. Reserve VIP Account Number
```
PUT /esb/rest_server/api/v1/vip-account/reserve
```

### HEADERS
`Content-Type`
application/json

`Authorization`
{access_token}

BODY raw
```
{
  "name": "Customer",
  "phone_number": "012121212",
  "id_number": "123456789",
  "account_number": "123456789",
  "created_by": "sys"
}
```

### Example Request
```
curl --location --request PUT 'http://172.16.28.75:8081/esb/rest_server/api/v1/vip-account/rule/update' \
--data-raw '{
  "name": "Customer",
  "phone_number": "012121212",
  "id_number": "123456789",
  "account_number": "123456789",
  "created_by": "sys"
}'
```
