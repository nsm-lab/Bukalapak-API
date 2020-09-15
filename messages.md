### [&laquo; Home](README.md)

[Bukalapak Messages API](#bukalapak-negotiations-api)
- [Get Inbox](#get-inbox)
	- [Resource URL](#resource-url)
	- [Parameters](#parameters)
	- [Example Request](#example-request)
	- [Example Response](#example-response)
- [Get Conversation](#get-conversation)
	- [Resource URL](#resource-url)
	- [Parameters](#parameters)
	- [Example Request](#example-request)
	- [Example Response](#example-response)
- [Get Message](#get-message)
	- [Resource URL](#resource-url)
	- [Parameters](#parameters)
	- [Example Request](#example-request)
	- [Example Response](#example-response)
- [Create Message](#create-message)
	- [Resource URL](#resource-url)
	- [Parameters](#parameters)
	- [POST request data](#post-request-data)
	- [Example Request](#example-request)
	- [Example Response](#example-response)
- [Delete Conversation](#delete-conversation)
	- [Resource URL](#resource-url)
	- [Parameters](#parameters)
	- [Example Request](#example-request)
	- [Example Response](#example-response)
- [Delete Message](#delete-message)
	- [Resource URL](#resource-url)
	- [Parameters](#parameters)
	- [Example Request](#example-request)
	- [Example Response](#example-response)

## Bukalapak Messages API

### Get Inbox
Get current user's inbox

+ Use `GET` http method.

##### Resource URL
+ [https://api.bukalapak.com/v2/messages.json]().

##### Parameters
+ `page` *(optional)*. Default to `1`
+ `per_page` *(optional)*. Default to `10`

##### Example Request
````sh
curl -u 67287:lXymG93y83m6RHzZV5FY https://api.bukalapak.com/v2/messages.json?page=1
````

##### Example Response
````json
{
    "status": "OK",
    "unread": 0,
    "inbox": [
        {
            "id": "520e0474e42b5658ab00001c",
            "updated_at": "2013-12-03T08:54:49+07:00",
            "partner_id": "155905",
            "partner_name": "Zakka Fauzan Muhammad",
            "user_id": "62817",
            "user_name": "Sayur Kangkung",
            "last_message": "sip diterima san..."
        },
        {
            "id": "5125950c948f5c1a05000662",
            "updated_at": "2013-12-02T21:50:51+07:00",
            "partner_id": "39435",
            "partner_name": "Cecep",
            "user_id": "62817",
            "user_name": "Sayur Kangkung",
            "last_message": "ok"
        },
        {
            "id": "516ffb155ff21f7b53000178",
            "updated_at": "2013-12-02T11:26:03+07:00",
            "partner_id": "78285",
            "partner_name": "Khairul",
            "user_id": "62817",
            "user_name": "Sayur Kangkung",
            "last_message": "kung"
        },
        {
            "id": "4ffab90e5ff21f447e000004",
            "updated_at": "2013-07-28T17:05:40+07:00",
            "partner_id": "57451",
            "partner_name": "Renjay Shop",
            "user_id": "62817",
            "user_name": "Sayur Kangkung",
            "last_message": "testing..."
        }
    ]
}
````

### Get Conversation
Get current user's selected conversation

+ Use `GET` http method.

##### Resource URL
+ [https://api.bukalapak.com/v2/messages/:id.json]().

##### Parameters
+ `page` *(optional)*. Default to `1`
+ `per_page` *(optional)*. Default to `10`

##### Example Request
````sh
curl -u 67287:lXymG93y83m6RHzZV5FY https://api.bukalapak.com/v2/messages/516d3299425762188f000011.json?per_page=5
````

##### Example Response
````json
{
    "status": "OK",
    "instant_messages": [
        {
            "id": "529c0bdb521fb0dc4500025e",
            "body": "kung",
            "created_at": "2013-12-02T11:26:03+07:00",
            "inbox_id": "516ffb155ff21f7b53000178",
            "read": true,
            "receiver_id": "78285",
            "receiver_name": "Khairul",
            "sender_id": "62817",
            "sender_name": "Sayur Kangkung",
            "updated_at": "2013-12-02T11:26:03+07:00"
        },
        {
            "id": "529c0b01e42b565bfb00047a",
            "body": "kung",
            "created_at": "2013-12-02T11:22:25+07:00",
            "inbox_id": "516ffb155ff21f7b53000178",
            "read": true,
            "receiver_id": "78285",
            "receiver_name": "Khairul",
            "sender_id": "62817",
            "sender_name": "Sayur Kangkung",
            "updated_at": "2013-12-02T11:22:25+07:00"
        }
    ],
    "message": null
}
````

### Get Message
Get current user's selected message

+ Use `GET` http method.

##### Resource URL
+ [https://api.bukalapak.com/v2/messages/im/:id.json]().

##### Parameters
None

##### Example Request
````sh
curl -u 67287:lXymG93y83m6RHzZV5FY https://api.bukalapak.com/v2/messages/im/516e2565177961034c000002.json
````

##### Example Response
````json
{
    "status": "OK",
    "instant_message": {
        "id": "524673ca318b27602f00000a",
        "body": "Halo Sayur Kangkung,\n\nKami telah memblokir lapakmu untuk barang:\n<strong>[DT] WIMCYCLE ADRENALINE DH TEAM 2012 - SIZE M</strong>\nSeharga: Rp 125.000\nKondisi barang: Bekas\n\nBarang diblokir karena alasan berikut ini:\n- Harga tidak sesuai\n\nJika kamu ingin mengaktifkan kembali lapakmu, kami minta kerjasama kamu untuk memperbaikinya. Kamu bisa langsung memperbaiki dengan klik http://www.local.host:3000/products/ggm8-jual-dt-wimcycle-adrenaline-dh-team-2012-size-m/edit.\n\nTerima kasih atas perhatian & kerjasama Kamu.\n\n",
        "created_at": "2013-09-28T13:14:34+07:00",
        "inbox_id": "524673c9318b27602f000009",
        "read": true,
        "receiver_id": "62817",
        "receiver_name": "Sayur Kangkung",
        "sender_id": "225448",
        "sender_name": "roni hafid",
        "updated_at": "2013-12-03T18:39:41+07:00"
    },
    "message": null
}
````

### Create Message
Create a new message

+ Use `POST` http method.
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/messages.json]().

##### Parameters
None

##### POST request data
+ `instant_message` *(required)*. New message to be sent, which contains:
	+ `receiver_id` *(required)*. Message receiver's user ID
	+ `category` *(required)*. Message category: '0' => normal message, '1' => question, '2' => suggestion, '3' => feature, '4' => transaction, note that for category > 0 must be addressed to admin
	+ `body_bb` *(required)*. Message's content

##### Example Request
```sh
curl -u 110677:JheQQS0OKApu3hGJwkRH -d '{ "instant_message":{"receiver_id":"110675", "category":"0", "body_bb":"tesssss"} }' https://api.bukalapak.com/v1/messages.json -H "Content-Type: application/json" -X POST
```

##### Example Response
Failed example
```json
{
	"status":"ERROR",
	"id":null,
	"message": "Gagal mengirim pesan: harap menggunakan format yang seharusnya"
}
```
```json
{
	"status":"ERROR",
	"id":null,
	"message": "Gagal mengirim pesan"
}
```
```json
{
	"status":"ERROR",
	"id":null,
	"message": "Pengiriman pesan untuk kategori ini hanya dapat ditujukan kepada admin"
}
```
Successfull example
```json
{
	"status":"OK",
	"id":"516d303c425762188f000007",
	"message": "Pesan terkirim"
}
```

### Delete Conversation
Delete existing conversation

+ Use `DELETE` http method.
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/messages/:id.json]().

##### Parameters
+ `id` *(required)*. Identifier for product being destroy.

##### Example Request
```sh
curl -u 110677:JheQQS0OKApu3hGJwkRH https://api.bukalapak.com/v2/messages/516d3299425762188f000011.json -H "Content-Type: application/json" -X DELETE
```

##### Example Response
Successfull example
```json
{
	"status":"OK",
	"id":"516d3299425762188f000011",
	"message": "Conversation berhasil dihapus"
}
```

### Delete Message
Delete existing message

+ Use `DELETE` http method.
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/messages/im/:id.json]().

##### Parameters
+ `id` *(required)*. Identifier for product being destroy.

##### Example Request
```sh
curl -u 110677:JheQQS0OKApu3hGJwkRH https://api.bukalapak.com/v2/messages/516d3299425762188f000015.json -H "Content-Type: application/json" -X DELETE
```

##### Example Response
Successfull example
```json
{
	"status":"OK",
	"id":"516d3299425762188f000015",
	"message": "Pesan berhasil dihapus"
}
```
