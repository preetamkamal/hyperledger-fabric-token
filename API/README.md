# 블록체인 API 서버

# 의존성 프로그램

```
python 2.7
node.js 8.8.11
```

# 서버실행

```
$ npm start
```

# API

## 리스트

1. account 생성
2. account 조회
3. transfer 발생
4. transfer 정보조회
5. 특정 거래내역 가져오기
6. 모든 거래내역 가져오기

## endpoint

```
http://IP:3000/api/v1.0/chaincode
```

### 1. account 생성

* method: POST

* path : /account

* request

```json
{
    "key" : ""
}
```

* response


정상 **201** 코드
```json
{
    "address": "",
    "value": 0
}
```

빈값(key) **404** 코드
```json
{
    "msg": "key가 비었습니다",
}
```

에러 **500** 코드
```json
{
    "msg": "address 생성중 문제발생",
    "err": "에러내용"
}
```

### 2. account 조회

* method: GET

* path : /account

* request

```json
?address=""
```

* response

정상 **201** 코드
```json
{
    "address": "",
    "value": 0
}
```

빈값(address) **404** 코드
```json
{
    "msg": "address가 비었습니다",
}
```

에러 **500** 코드
```json
{
    "msg": "address 조회중 문제발생",
    "err": "에러내용"
}
```

### 3. transfer 발생

* method: POST

* path : /transaction

* request:

```json
{
    "from": "",
    "to": "",
    "value": 0
}
```

* response

정상 **201** 코드
```json
{
    "txId" :""
}
```

에러 **500** 코드
```json
{
    "msg" : "토큰 전송중 문제발생",
    "err" : "",
}
```

빈값(from) **404** 코드
```json
{
    "msg" : "from이 비었습니다."    
}
```

빈값(to) **404** 코드
```json
{
    "msg" : "to이 비었습니다."    
}
```

빈값(value) **404** 코드
```json
{
    "msg" : "value가 비었습니다."    
}

```
### 4. transfer 정보조회

* method: GET

* path : /transaction

* request:

```json
?txId=""
```

* response

정상 **200** 코드
```json
{
    "TxId":"",
    "From":"",
    "To":"",
    "Value":0,
    "Timestamp":""
}
```

에러 **500** 코드
```json
{
    "msg" : "txId 조회중 문제발생",
    "err" : "",
}
```

빈값(txId) **404** 코드
```json
{
    "msg" : "txId가 비었습니다."    
}

```

### 5. 특정 거래내역 가져오기 

* method: GET

* path : /receipt

* request:

```json
?receiptId=""
```

* response

정상 **200** 코드
```json
{
    "receiptId" : "",
    "txId" : "",
    "nextReceiptId" : "",
    "prevReceiptId" : "",
    "status" : ""
}
```

에러 **500** 코드
```json
{
    "msg" : "receiptId 조회중 문제발생",
    "err" : "",
}
```

빈값(receiptId) **404** 코드
```json
{
    "msg" : "receiptId가 비었습니다."    
}

```



### 6. 모든 거래내역 가져오기

* method: GET

* path: /receipt/all

* request:

```json
?address=""
```

* response

정상 **200** 코드
```json
[
    {
        "receiptId" : "",
        "txId" : "",
        "nextReceiptId" : "",
        "prevReceiptId" : "",
        "status" : ""
    },
    . . . 중 략 . . .
]
```

에러 **500** 코드
```json
{
    "msg" : "address 조회중 문제발생",
    "err" : "",
}
```

빈값(address) **404** 코드
```json
{
    "msg" : "address가 비었습니다."    
}

```