### [&laquo; Home](README.md)

[Notifications API](#notifications-api)
- [Add Android Device](#add-android-device)
  - [Resource URL](#resource-url)
  - [Parameters](#parameters)
  - [Example Request](#example-request)
  - [Example Response](#example-response)
- [Logout Android Device](#logout-android-device)
  - [Resource URL](#resource-url)
  - [Parameters](#parameters)
  - [Example Request](#example-request)
  - [Example Response](#example-response)
- [Remove Android Device](#remove-android-device)
  - [Resource URL](#resource-url)
  - [Parameters](#parameters)
  - [Example Request](#example-request)
  - [Example Response](#example-response)
- [Get Unread Notifications](#get-unread-notifications)
  - [Resource URL](#resource-url)
  - [Parameters](#parameters)
  - [Example Request](#example-request)
  - [Example Response](#example-response)
- [Set Notifications as Read](#set-notifications-as-read)
  - [Resource URL](#resource-url)
  - [Parameters](#parameters)
  - [Example Request](#example-request)
  - [Example Response](#example-response)
- [Set a Notification as Read](#set-a-notifications-as-read)
  - [Resource URL](#resource-url)
  - [Parameters](#parameters)
  - [Example Request](#example-request)
  - [Example Response](#example-response)
- [Fetch Notification Config Settings](#fetch-notification-config-settings)
  - [Resource URL](#resource-url)
  - [Parameters](#parameters)
  - [Example Request](#example-request)
  - [Example Response](#example-response)
- [Set Notification Config Settings](#set-notification-config-settings)
  - [Resource URL](#resource-url)
  - [Parameters](#parameters)
  - [Example Request](#example-request)
  - [Example Response](#example-response)
- [Android Notifications Data Examples](#android-notifications-data-examples)

## Notifications API

### Add Android Device
Add user's Android device to receive notifications.
+ Use `POST` http method
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/notifications/android.json]()

##### Parameters
+ `reg_id` *(required)*. Registration ID of the device.
+ `model` *(optional)*. Device model.
+ `manufacturer` *(optional)*. Device manufacturer.
+ `product_name` *(optional)*. Device product name.

##### Example Request
````sh
curl -u 204254:Sy7PRGGr4foUk22uzjMu "https://api.bukalapak.com/v2/notifications/android.json" -X POST --data "reg_id=ASD223SDA&model=GG-P4124H&manufacturer=Nokia&name=Lumpia"

````

#### Example Response
Success response:

````json
{
  "status":"OK",
  "message":"Device added"
}
````

Failed response:
````json
{
  "status":"ERROR",
  "message":"Failed adding device"
}
````

### Logout Android Device
Logout current user from current device.
+ Use `DELETE` http method
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/notifications/logout.json]()

##### Parameters
+ `reg_id` *(required)*. Registration ID of the device.

##### Example Request
````sh
curl -u 204254:Sy7PRGGr4foUk22uzjMu "https://api.bukalapak.com/v2/notifications/logout.json" -X DELETE --data "reg_id=ASD223SDA"

````

#### Example Response
Success response:
````json
{
  "status":"OK",
  "message":"Device logged out"
}
````

Failed response:
````json
{
  "status":"ERROR",
  "message":"Failed logging out"
}
````


### Remove Android Device
Remove user's Android device from receiver devices list.
+ Use `DELETE` http method
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/notifications/android.json]()

##### Parameters
+ `reg_id` *(required)*. Registration ID of the device.

##### Example Request
````sh
curl -u 204254:Sy7PRGGr4foUk22uzjMu "https://api.bukalapak.com/v2/notifications/android.json" -X DELETE --data "reg_id=ASD223SDA"

````

#### Example Response
Success response:
````json
{
  "status":"OK",
  "message":"Device unregistered"
}
````

Failed response:
````json
{
  "status":"ERROR",
  "message":"The requested device doesn't belong to this user"
}
````

### Get Unread Notifications
Get numbers of unread messages and transactions.
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/notifications/unreads.json]()

##### Parameters
+ `reg_id` *(required)*. Registration ID of the device.

##### Example Request
````sh
curl -u 204254:Sy7PRGGr4foUk22uzjMu "https://api.bukalapak.com/v2/notifications/unreads.json"

````

#### Example Response
````json
{
  "messages":0,
  "transactions_need_action_as_seller":0,
  "transactions_as_buyer":0,
  "unread_notifications":0,
  "transactions_need_action_as_buyer":4
}
````

### Set Notifications as Read
+ Use `PUT` http method
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/notifications.json]()

##### Parameters
+ `reg_id` *(required)*. Registration ID of the device.

##### Example Request
````sh
curl -u 204254:Sy7PRGGr4foUk22uzjMu -X PUT "https://api.bukalapak.com/v2/notifications.json" --data ""

````

#### Example Response
````json
{
  "status":"OK",
  "message":null
}
````

### Set a Notification as Read
+ Use `PUT` http method
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/notifications/:notification_transaction_id.json]()

##### Parameters
+ `notification_transaction_id` *(required)*. Notification ID of the transaction.

##### Example Request
````sh
curl -u 204254:Sy7PRGGr4foUk22uzjMu -X PUT "http://api.local.host:3000/v2/notifications/52a6e5e284eab03aa200013a.json"

````

#### Example Response
````json
Success response

{
  "status":"OK",
  "unread":0,
  "message":null
}

Failed response

{
  "status":"ERROR",
  "unread":1,
  "message":"The requested notifications doesn't belong to the current user"
}
````

### Fetch Notification Config Settings
+ Use `GET` http method
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/notifications/config.json]()

##### Parameters
+ `reg_id` *(required)*. Device registration ID.

##### Example Request
````sh
curl -u 204254:Sy7PRGGr4foUk22uzjMu https://api.bukalapak.com/v2/notifications/config.json?reg_id=BD12A34

````

#### Example Response
````json
Success response

{
  "status":"OK",
  "config":{
    "transaction":1,
    "nego":1,
    "message":1,
    "report":1
  },
  "message":null
}

Failed response

{
  "status":"ERROR",
  "config":null,
  "message":"Failed Fetching Device Configuration"
}
````

### Set Notification Config Settings
+ Use `PUT` http method
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/notifications/config.json]()

##### Parameters
+ `reg_id` *(required)*. Device registration ID.
+ `config` *(required)*. Configuration hash values. At least one must be present. Value `1` if on, value `0` if off.
  + `config[transaction]` *(optional)*. Transaction push notification.
  + `config[message]` *(optional)*. Message push notification.
  + `config[nego]` *(optional)*. Offer push notification.
  + `config[report]` *(optional)*. Report push notification.

##### Example Request
````sh
curl -u 204254:Sy7PRGGr4foUk22uzjMu -X PUT "https://api.bukalapak.com/v2/notifications/config.json" --data "reg_id=BDNAEASM&config[transaction]=1&config[message]=0"

````

#### Example Response
````json
Success response

{
  "status":"OK",
  "message":"Configuration Updated"
}

Failed response

{
  "status":"ERROR",
  "message":"Failed Updating Configuration"
}
````


### Android Notifications Data Examples

````json
Transaction Notification

{
  "type"=>"transaction",
  "receiver_id"=>204254,
  "message"=>"Transaksi baru dari Liem Lie Wie",
  "details"=>{
    "id"=>51960,
    "state"=>"paid",
    "transaction_id"=>"131211141960",
    "amount"=>155000,
    "quantity"=>1,
    "shipping_fee"=>8000,
    "total_amount"=>163000,
    "products"=>[1069398],
    "consignee"=>{
      "name"=>"Me Ow",
      "address"=>"Jl Lancar XXI",
      "city"=>"Jakarta Barat",
      "province"=>"DKI Jakarta",
      "post_code"=>"11440"
    },
    "buyer"=>{
      "id"=>15,
      "name"=>"Me Ow",
      "username"=>"meow"
    },
    "seller"=>{
      "id"=>204254,
      "name"=>"Testing Account",
      "username"=>"testingaccount"
    },
    "actions"=>["deliver", "reject"],
    "created_at"=>"2013-12-11T14:59:21+07:00"
  }
}

Offer Notification

{
  "data"=>{
    "type"=>"nego",
    "receiver_id"=>204254,
    "message"=>"Anda mendapatkan tawaran nego dari Me Ow",
    "details"=>{
      "id"=>51588,
      "state"=>"waiting",
      "amount"=>100,
      "quantity"=>1,
      "product"=>{
        "id"=>1069403,
        "name"=>"Bantal bibir pink Impor",
        "normal_price"=>70000
      },
      "actions"=>["accept", "reject"],
      "buyer"=>{
        "id"=>15,
        "name"=>"Me Ow",
        "username"=>"meow"
      },
      "seller"=>{
        "id"=>204254,
        "name"=>"Testing Account",
        "username"=>"testingaccount"
      }
    }
  }
}

Message Notification

{
  "data"=>{
    "type"=>"message",
    "receiver_id"=>204254,
    "message"=>"Anda mendapatkan pesan dari Me Ow"
    "details"=>{
      "id":"56be34322",
      "inbox_id":"56be34",
      "message"=>"mantab gan"
    }
  }
}

Report Notification

{
  "data"=>{
    "type"=>"report",
    "receiver_id"=>204254,
    "message"=>"g.kunci sinchan telah dilaporkan",
    "details"=>nil
  }
}

Reminder (Only Received Right After Logging in via App)

{
  "data"=>{
    "type"=>"reminder",
    "unread_notifications"=>17,
    "messages"=>0,
    "transactions_need_action_as_seller"=>12,
    "transactions_need_action_as_buyer"=>3,
    "offers_need_action_as_seller"=>1,
    "offers_need_action_as_buyer"=>0
  }
}
````
