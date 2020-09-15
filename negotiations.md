### [&laquo; Home](README.md)

[Bukalapak Negotiations API](#bukalapak-negotiations-api)
- [Negotiation Listing](#negotiation-listing)
	- [Resource URL](#resource-url)
	- [Parameters](#parameters)
	- [Example Request](#example-request)
	- [Example Response](#example-response)
- [Accept Negotiation](#accept-negotiation)
  - [Resource URL](#resource-url)
  - [Parameters](#parameters)
  - [Example Request](#example-request)
  - [Example Response](#example-response)
- [Reject Negotiation](#reject-negotiation)
  - [Resource URL](#resource-url)
  - [Parameters](#parameters)
  - [Example Request](#example-request)
  - [Example Response](#example-response)

## Bukalapak Negotiations API

### Negotiation Listing
Get list of negotiations owned by user

+ Use `GET` http method.
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/negotiations.json]().

##### Parameters
+ `page` *(optional)*.
+ `per_page` *(optional)*.

##### Example Request
```sh
curl -u 110677:JheQQS0OKApu3hGJwkRH https://api.bukalapak.com/v2/negotiations.json
```

##### Example Response
Successfull example
```json
{
  "status":"OK",
  "negotiations":[
  {
    "id":10530,
    "state":"rejected",
    "product":
    {
      "id":1069174,
      "category":"Buku",
      "category_id":60,
      "category_structure":["Hobi & Hiburan","Buku"],
      "name":"Buku Palsu",
      "city":"Jakarta Barat",
      "province":"DKI Jakarta",
      "price":20000,"weight":"1000",
      "images":["http://www.local.host:3000/system/images/2/6/0/0/3/5/9/large/Screenshot_-_111113_-_15_47_03.png?1384836182"],
      "small_images":["http://www.local.host:3000/system/images/2/6/0/0/3/5/9/small/Screenshot_-_111113_-_15_47_03.png?1384836182"],
      "url":"http://www.local.host:3000/p/hobi-hiburan/buku/mwza-jual-buku-palsu",
      "desc":"asdasd",
      "condition":"new",
      "nego":false,
      "seller_name":"Liem Lie Wie",
      "payment_ready":true,
      "stock":49999,
      "specs":{"type":null},
      "state_description":[]
    },
    "normal_price":100000,
    "quantity":1,
    "nego_price":10000,
    "actions":[],
    "buyer":
    {
      "id":31432,
      "name":"Khairul",
      "username":"kahirul"
    },
    "seller":
    {
      "id":62817,
      "name":"Sayur Kangkung",
      "username":"sayurkangkung"
    }
  }
  ...
  ],
  "message": null
}
```

### Accept Negotiation
Accept incoming negotiation

+ Use `PUT` http method.
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/negotiations/:id/accept.json]().

##### Parameters
None

##### Example Request
```sh
curl -u 110677:JheQQS0OKApu3hGJwkRH -d {} https://api.bukalapak.com/v2/negotiations/124/accept.json -X PUT
```

##### Example Response
Successfull example
```json
{
  "status":"OK",
  "negotiation":[
  {
    "id":124,
    "state":"accepted",
    "product":
    {
      "id":1069174,
      "category":"Buku",
      "category_id":60,
      "category_structure":["Hobi & Hiburan","Buku"],
      "name":"Buku Palsu",
      "city":"Jakarta Barat",
      "province":"DKI Jakarta",
      "price":20000,"weight":"1000",
      "images":["http://www.local.host:3000/system/images/2/6/0/0/3/5/9/large/Screenshot_-_111113_-_15_47_03.png?1384836182"],
      "small_images":["http://www.local.host:3000/system/images/2/6/0/0/3/5/9/small/Screenshot_-_111113_-_15_47_03.png?1384836182"],
      "url":"http://www.local.host:3000/p/hobi-hiburan/buku/mwza-jual-buku-palsu",
      "desc":"asdasd",
      "condition":"new",
      "nego":false,
      "seller_name":"Liem Lie Wie",
      "payment_ready":true,
      "stock":49999,
      "specs":{"type":null},
      "state_description":[]
    },
    "normal_price":100000,
    "quantity":1,
    "nego_price":10000,
    "actions":[],
    "buyer":
    {
      "id":31432,
      "name":"Khairul",
      "username":"kahirul"
    },
    "seller":
    {
      "id":62817,
      "name":"Sayur Kangkung",
      "username":"sayurkangkung"
    }
  }
  ...
  ],
  "message": null
}
```

Failed example
```json
{
  "status":"ERROR",
  "negotiation": nil,
  "message": "Stock not available"
}
```

### Reject Negotiation
Reject incoming negotiation

+ Use `PUT` http method.
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/negotiations/:id/reject.json]().

##### Parameters
None

##### Example Request
```sh
curl -u 110677:JheQQS0OKApu3hGJwkRH -d {} https://api.bukalapak.com/v2/negotiations/124/reject.json -X PUT
```

##### Example Response
Successfull example
```json
{
  "status":"OK",
  "negotiation":[
  {
    "id":124,
    "state":"rejected",
    "product":
    {
      "id":1069174,
      "category":"Buku",
      "category_id":60,
      "category_structure":["Hobi & Hiburan","Buku"],
      "name":"Buku Palsu",
      "city":"Jakarta Barat",
      "province":"DKI Jakarta",
      "price":20000,"weight":"1000",
      "images":["http://www.local.host:3000/system/images/2/6/0/0/3/5/9/large/Screenshot_-_111113_-_15_47_03.png?1384836182"],
      "small_images":["http://www.local.host:3000/system/images/2/6/0/0/3/5/9/small/Screenshot_-_111113_-_15_47_03.png?1384836182"],
      "url":"http://www.local.host:3000/p/hobi-hiburan/buku/mwza-jual-buku-palsu",
      "desc":"asdasd",
      "condition":"new",
      "nego":false,
      "seller_name":"Liem Lie Wie",
      "payment_ready":true,
      "stock":49999,
      "specs":{"type":null},
      "state_description":[]
    },
    "normal_price":100000,
    "quantity":1,
    "nego_price":10000,
    "actions":[],
    "buyer":
    {
      "id":31432,
      "name":"Khairul",
      "username":"kahirul"
    },
    "seller":
    {
      "id":62817,
      "name":"Sayur Kangkung",
      "username":"sayurkangkung"
    }
  }
  ...
  ],
  "message": null
}
```

Failed example
```json
{
  "status":"ERROR",
  "negotiation": nil,
  "message": null
}
```

### Dictionary
- `state` State of negotiation. Possible values are as listed
  - `waiting` initial state. Negotiation newly created and waiting for seller response
  - `accepted` negotiation has been accepted by seller
  - `rejected` negotiation has been rejected by seller
  - `finished` negotiation has been accepted by seller and paid by buyer
  - `expired` negotiation has been expired
  - 'cancelled' negotiation has been cancelled by buyer
- `actions` Actions that can be performed by current user. Possible values are
  - `accept` Can be performed by seller at [Accept Negotiation](#accept-negotiation) endpoint
  - `rejected` Can be performed by seller at [Reject Negotiation](#reject-negotiation) endpoint

<!--
 - [Create Negotiation](#create-negotiation)
	- [Resource URL](#resource-url)
	- [Parameters](#parameters)
	- [POST request data](#post-request-data)
	- [Example Request](#example-request)
	- [Example Response](#example-response)
- [Update Negotiation](#update-negotiation)
	- [Resource URL](#resource-url)
	- [Parameters](#parameters)
	- [PUT request data](#put-request-data)
	- [Example Request](#example-request)
	- [Example Response](#example-response)
 -->

<!-- ### Create Negotation
Create a new negotiation

+ Use `POST` http method.
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/negotiations.json]().

##### Parameters
None

##### POST request data
+ `amount` *(required)*. Ammount of negotiation
+ `product_id` *(required)*. Product ID which negotiation will be addressed
+ `quantity` *(required)*. Quantity of the product to be negotiated

##### Example Request
```sh
curl -u 110677:JheQQS0OKApu3hGJwkRH -d '{ "amount":"1400000", "product_id":"gglq", "quantity":"1" }' https://api.bukalapak.com/v2/negotiations.json -H "Content-Type: application/json" -X POST
```

##### Example Response
Failed example
```json
{
	"status":"ERROR",
	"id":null,
	"message": "Negosiasi gagal: jumlah barang minimal 1"
}
```
```json
{
	"status":"ERROR",
	"id":null,
	"message": "Negosiasi gagal: jumlah barang tersedia hanya 1"
}
```
```json
{
	"status":"ERROR",
	"id":null,
	"message": "Negosiasi gagal, angka negosiasi tidak boleh kurang dari 1300000"
}
```
Successfull example
```json
{
	"status":"OK",
	"id":"12702",
	"message": "Negosiasi berhasil"
}
```

### Update Negotation
Update an existing negotiation

+ Use `PUT` http method.
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/negotiations/:id.json]().

##### Parameters
None

##### PUT request data
+ `status` *(required)*. can be one of the following: "accept", "reject", "cancel", or "update"
+ `amount` *(required)*. Ammount of negotiation if status is "update"

##### Example Request
Cancel Negotiation, Reject Negotiation, Accept Negotiation:
```sh
curl -u 110677:JheQQS0OKApu3hGJwkRH -d '{ "status":"accept" }' https://api.bukalapak.com/v2/negotiations/10537.json -H "Content-Type: application/json" -X PUT
```
Update Negotiation:
```sh
curl -u 110677:JheQQS0OKApu3hGJwkRH -d '{ "status":"update", "amount":"1350000" }' https://api.bukalapak.com/v2/negotiations/10537.json -H "Content-Type: application/json" -X PUT
```

##### Example Response
Failed example
```json
{
	"status":"ERROR",
	"id":null,
	"message": Pembaruan negosiasi gagal, angka negosiasi tidak boleh kosong
}
```
```json
{
	"status":"ERROR",
	"id":null,
	"message": "Pembaruan negosiasi gagal, angka negosiasi tidak boleh kurang dari 1300000"
}
```
```json
{
	"status":"ERROR",
	"id":null,
	"message": "Anda tidak memiliki hak akses untuk membatalkan negosiasi ini"
}
```
```json
{
	"status":"ERROR",
	"id":null,
	"message": "Anda tidak memiliki hak akses untuk menolak negosiasi ini"
}
```
```json
{
	"status":"ERROR",
	"id":null,
	"message": "Anda tidak memiliki hak akses untuk menerima negosiasi ini"
}
```
```json
{
	"status":"ERROR",
	"id":null,
	"message": "Anda tidak memiliki hak akses untuk memperbarui negosiasi ini"
}
```
Successfull example
Negotiation Cancelled
```json
{
	"status":"OK",
	"id":"12702",
	"message": "Negosiasi dibatalkan"
}
```
Negotiation Rejected
```json
{
	"status":"OK",
	"id":"12702",
	"message": "Negosiasi ditolak"
}
```
Negotiation Accepted
```json
{
	"status":"OK",
	"id":"12702",
	"message": "Negosiasi diterima"
}
```
Negotiation Updated
```json
{
	"status":"OK",
	"id":"12702",
	"message": "Negosiasi diperbarui"
}
``` -->
