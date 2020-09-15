### [&laquo; Home](README.md)

[Bukalapak User API](#bukalapak-user-api)
- [User Info](#user-info)
  - [Resource URL](#resource-url)
  - [Parameters](#parameters)
  - [Example Request](#example-request)
  - [Example Response](#example-response)
- [Register](#register)
  - [URL](#url)
  - [Parameters](#parameters)
  - [Example Request](#example-request)
  - [Example Response](#example-response)
- [Password Reset](#register)
  - [URL](#url)
  - [Parameters](#parameters)
  - [Example Request](#example-request)
  - [Example Response](#example-response)
- [User Account Setting View](#user-info)
  - [Resource URL](#resource-url)
  - [Parameters](#parameters)
  - [Example Request](#example-request)
  - [Example Response](#example-response)
- [User Account Setting Update](#user-info)
  - [Resource URL](#resource-url)
  - [Parameters](#parameters)
  - [Example Request](#example-request)
  - [Example Response](#example-response)
- [User Feedbacks](#user-feedbacks)
  - [Resource URL](#resource-url)
  - [Parameters](#parameters)
  - [Example Request](#example-request)
  - [Example Response](#example-response)
- [Show Bank Accounts](#show-bank-accounts)
  - [Resource URL](#resource-url)
  - [Parameters](#parameters)
  - [Example Request](#example-request)
  - [Example Response](#example-response)
- [Add New Bank Account](#add-new-bank-account)
  - [Resource URL](#resource-url)
  - [Parameters](#parameters)
  - [Example Request](#example-request)
  - [Example Response](#example-response)
- [Update Bank Account](#add-new-bank-account)
  - [Resource URL](#resource-url)
  - [Parameters](#parameters)
  - [Example Request](#example-request)
  - [Example Response](#example-response)
- [Set Bank Account to Primary](#set-bank-account-to-primary)
  - [Resource URL](#resource-url)
  - [Parameters](#parameters)
  - [Example Request](#example-request)
  - [Example Response](#example-response)
- [Delete Bank Account](#delete-bank-account)
  - [Resource URL](#resource-url)
  - [Parameters](#parameters)
  - [Example Request](#example-request)
  - [Example Response](#example-response)
- [Supported Banks](#supported-banks)

## Bukalapak User API

### User Info
Get information for current user
+ Use `GET` http method
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/users/info.json]()

##### Parameters
None

##### Example Request
````sh
curl -u 15:wcrG8WPPWaq9Ndiesbjn https://api.bukalapak.com/v2/users/info.json

````

##### Example Response
Success response:
````json
{
  "status":"OK",
  "user":
  {
    "name":"Me Ow",
    "email":"meow@domain.com",
    "phone":"022345678901",
    "avatar":"https://secure.gravatar.com/avatar/c8a0457bfc1b881755588e05a6ce55f0?s=50",
    "bank":
    {
      "name":"Bank Republik Dummy",
      "number":"234567890"
    }
  },
  "message":null
}
````


### Register
Return token after registration to enable access for `required authentication's resources`

+ Use `POST` http method.

##### URL
+ [https://api.bukalapak.com/v2/users.json]()

##### Parameters
None

##### POST request data
+ `user[email]` *(required)*. E-mail address to register.
+ `user[username]` *(required)*. Username to register.
+ `user[name]` *(required)*. New user's name.
+ `user[birthday(3i)]` *(optional)*. Date of birth. Use together with `user[birthday(2i)]` and `user[birthday(1i)]`.
+ `user[birthday(2i)]` *(optional)*. Month of birth. Use together with `user[birthday(3i)]` and `user[birthday(1i)]`
+ `user[birthday(1i)]` *(optional)*. Year of birth. Use together with `user[birthday(3i)]` and `user[birthday(2i)]`
+ `user[password]` *(required)*. Password.
+ `user[password_confirmation]` *(required)*. Password confirmation.
+ `user[phone]` *(optional)*. User's phone number.
+ `user[address_attributes][province]` *(optional)*. User's province. Use together with other `address_attributes` data.
+ `user[address_attributes][city]` *(optional)*. User's city. Use together with other `address_attributes` data.
+ `user[address_attributes][area]` *(optional)*. User's area. Use together with other `address_attributes` data.
+ `user[address_attributes][address]` *(optional)*. User's address. Use together with other `address_attributes` data.
+ `user[address_attributes][post_code]` *(optional)*. User's postal code. Use together with other `address_attributes` data.
+ `user[policy]` *(required)*. Sign that user has accepted the agreements.

##### Example Request
````sh
curl -X POST --data "user[email]=testing@testing12349.com&user[username]=testingtesting9&user[name]=asadasan&user[birthday(3i)]=12&user[birthday(2i)]=12&user[birthday(1i)]=1999&user[password]=testing1234&user[password_confirmation]=testing1234&user[phone]=081238877&user[address_attributes][province]=Banten&user[address_attributes][city]=Tangerang&user[address_attributes][area]=Batuceper&user[address_attributes][address]=jl xxx&user[address_attributes][post_code]=11111]&user[policy]=1" "https://api.bukalapak.com/v2/users.json"

````

##### Example Response
Success response:
````json
{
  "status":"OK",
  "user_id": "204270",
  "token": "49Rk5LJvph5PAccAQ2Mq"
  "message":null
}
````

Failed response
````json
{
  "status":"ERROR",
  "user_id":null,
  "token":null,
  "message":"Username sudah digunakan, Email sudah digunakan"
}
````

### Password Reset
Send password reset link and instruction to a registered user's e-mail address.

+ Use `POST` http method.

##### URL
+ [https://api.bukalapak.com/v2/users/password_reset.json]()

##### Parameters
None

##### POST request data
+ `user[email]` *(required)*. E-mail address for sending password reset instruction.

##### Example Request
````sh
curl -X POST --data "email=testingaccount@test.com" "https://api.bukalapak.com/v2/users/password_reset.json"

````

##### Example Response
Success response:
````json
{
  "status":"OK",
  "message":"Email penggantian password telah dikirimkan, silakan ikuti petunjuk yang diberikan"
}
````

Failed response
````json
{
  "status":"ERROR",
  "message":"Tidak ada user yang terdaftar dengan email tersebut"
}
````

### User Account Setting View
Get account information for current user
+ Use `GET` http method
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/users/:id.json]()

##### Parameters
None

##### Example Request
````sh
curl -u 204254:Sy7PRGGr4foUk22uzjMu https://api.bukalapak.com/v2/users/204254.json

````

##### Example Response
Success response:
````json
{
  "status":"OK",
  "user":{
    "id":204254,
    "email":"testingaccount@test.com",
    "phone":"081238877",
    "name":"Testing Account",
    "birthday":"1999-12-12",
    "address":{
      "province":"Banten",
      "city":"Tangerang",
      "area":"Batuceper",
      "address":"jl xxx",
      "postal_code":"11111"
    }
  },
  "message":null
}
````

### User Account Setting Update
Update account information for current user
+ Use `PUT` http method
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/users/:id.json]()

##### Parameters
+ `user[name]` *(optional)*. User's name.
+ `user[birthday(3i)]` *(optional)*. Date of birth. Use together with `user[birthday(2i)]` and `user[birthday(1i)]`.
+ `user[birthday(2i)]` *(optional)*. Month of birth. Use together with `user[birthday(3i)]` and `user[birthday(1i)]`
+ `user[birthday(1i)]` *(optional)*. Year of birth. Use together with `user[birthday(3i)]` and `user[birthday(2i)]`
+ `user[phone]` *(optional)*. User's phone number.
+ `user[address_attributes][province]` *(optional)*. User's province. Use together with other `address_attributes` data.
+ `user[address_attributes][city]` *(optional)*. User's city. Use together with other `address_attributes` data.
+ `user[address_attributes][area]` *(optional)*. User's area. Use together with other `address_attributes` data.
+ `user[address_attributes][address]` *(optional)*. User's address. Use together with other `address_attributes` data.
+ `user[address_attributes][post_code]` *(optional)*. User's postal code. Use together with other `address_attributes` data.

##### Example Request
````sh
curl -u 204254:Sy7PRGGr4foUk22uzjMu https://api.bukalapak.com/v2/users/204254.json  -X PUT --data "user[name]=asadasan&user[birthday(3i)]=12&user[birthday(2i)]=12&user[birthday(1i)]=1999&user[phone]=081238877&user[address_attributes][province]=Banten&user[address_attributes][city]=Tangerang&user[address_attributes][area]=Batuceper&user[address_attributes][address]=jl xxx&user[address_attributes][post_code]=11111"

````

##### Example Response
Success response:
````json
{
  "status":"OK",
  "user":{
    "id":204254,
    "email":"testingaccount@test.com",
    "phone":"081238877",
    "name":"asadasan",
    "birthday":"1999-12-12",
    "address":{
      "province":"Banten",
      "city":"Tangerang",
      "area":"Batuceper",
      "address":"jl xxx",
      "postal_code":"11111"
    }
  },"message":"Account Updated"
}
````

### User Feedbacks
Get feedback listing for current user
+ Use `GET` http method
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/users/:id/feedbacks.json]()

##### Parameters
+ `page` *(optional)*.
+ `per_page` *(required)*.
+ `seller` *(required)*. Field indicating whether to return feedback as seller, or as buyer. Possible value `0` and anything else. If set to '0', response will return feedbacks as buyer. Other values or empty will return feedback as seller.


##### Example Request
````sh
curl -u 15:wcrG8WPPWaq9Ndiesbjn https://api.bukalapak.com/v2/users/62817/feedbacks.json?page=1&per_page=10&seller=0

````

##### Example Response
Success response:
````json
{
  "status": "OK",
  "message": null,
  "feedbacks": [
    {
      "id": 22032,
      "transaction_id": 7921,
      "sender_id": 1,
      "sender_name": "Nugroho Herucahyono",
      "user_id": 62817,
      "user_name": "Sayur Kangkung",
      "body": "Pembeli yang baik. Tidak rewel dan responsive",
      "positive": true,
      "created_at":"2012-10-11T17:55:34+07:00",
      "updated_at":"2012-10-11T17:55:34+07:00"
    },
    {
      "id": 22031,
      "transaction_id": 7907,
      "sender_id": 31432,
      "sender_name": "Khairul",
      "user_id": 62817,
      "user_name": "Sayur Kangkung",
      "body": "Recommended buyer. Ga banyak tanya :). Bayar sesuai harga dan cepat tanggap.",
      "positive": true,
      "created_at":"2012-10-11T17:55:34+07:00",
      "updated_at":"2012-10-11T17:55:34+07:00"
    }
  ]
}
````

### Show Bank Accounts
Get bank account listing for the current user.
+ Use `GET` http method
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/users/banks.json]()

##### Parameters
None


##### Example Request
````sh
curl -u 15:wcrG8WPPWaq9Ndiesbjn https://api.bukalapak.com/v2/users/banks.json

````

##### Example Response
````json
{
  "status":"OK",
  "accounts":[
    {
      "id":41829,
      "bank":"Bank Central Asia (BCA)",
      "number":"123 456 789",
      "name":"Me Ow",
      "primary":false
    },
    {
      "id":41831,
      "bank":"Bank Central Asia (BCA)",
      "number":"987 654 321",
      "name":"Me Ow",
      "primary":false
    }
  ],
  "message":null
}
````

### Add New Bank Account
Add new bank account for the current user.
+ Use `POST` http method
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/users/banks.json]()

##### Parameters
+ `payment_bank_account[name]` *(required)*. Name of the account owner.
+ `payment_bank_account[bank]` *(required)*. Name of the bank.
+ `payment_bank_account[number]` *(required)*. The bank account's number.
+ `password` *(required)*. Current user's password.


##### Example Request
````sh
curl -u 204254:Sy7PRGGr4foUk22uzjMu -X POST "https://api.bukalapak.com/v2/users/banks.json" --data "payment_bank_account[name]=Testing Account&payment_bank_account[bank]=Bank Central Asia (BCA)&payment_bank_account[number]=987 654 321&password=testing1234"

````

##### Example Response
````json
Success response

{
  "status":"OK",
  "message":"Bank account added"
}

Failed response

{
  "status":"ERROR",
  "message":"Incorrect password"
}
````

### Update Bank Account
Update current user's bank account.
+ Use `PUT` http method
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/users/banks/:bank_account_id.json]()

##### Parameters
+ `payment_bank_account[name]` *(required)*. Name of the account owner.
+ `payment_bank_account[bank]` *(required)*. Name of the bank.
+ `payment_bank_account[number]` *(required)*. The bank account's number.
+ `password` *(required)*. Current user's password.


##### Example Request
````sh
curl -u 204254:Sy7PRGGr4foUk22uzjMu -X PUT "https://api.bukalapak.com/v2/users/settings/bank/41829/primary.json" --data "payment_bank_account[name]=Bill Gates&payment_bank_account[bank]=Bank Central Asia (BCA)&payment_bank_account[number]=123 456 789&password=testing1234"
````

##### Example Response
````json
Success response

{
  "status":"OK",
  "message":"Bank account updated"
}

Failed response

{
  "status":"ERROR",
  "message":"Incorrect password"
}
````

### Set Bank Account to Primary
Set current user's primary bank account.
+ Use `PUT` http method
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/users/banks/:bank_account_id/primary.json]()

##### Parameters
None


##### Example Request
````sh
curl -u 204254:Sy7PRGGr4foUk22uzjMu -X PUT "https://api.bukalapak.com/v2/users/banks/41831/primary.json" --data ""
````

##### Example Response
````json
{
  "status":"OK",
  "message":"Set to primary"
}
````

### Delete Bank Account
Delete current user's bank account.
+ Use `DELETE` http method
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/users/banks/:bank_account_id.json]()

##### Parameters
None


##### Example Request
````sh
curl -u 204254:Sy7PRGGr4foUk22uzjMu -X DELETE "https://api.bukalapak.com/v2/users/banks/41832.json" --data ""
````

##### Example Response
````json
Success response

{
  "status":"OK",
  "message":"Deleted"
}

Failed response

{
  "status":"ERROR",
  "message":"The bank account doesn't belong to the current user"
}
````

### Supported Banks

````
[
  "Bank Central Asia (BCA)",
  "Bank Mandiri",
  "Bank Negara Indonesia (BNI)",
  "Bank Rakyat Indonesia (BRI)",
  "Bank Tabungan Negara (BTN)",
  "Bank Agroniaga",
  "Bank Artha Graha International",
  "Bank Bukopin",
  "Bank Bumi Arta",
  "Bank Capital Indonesia",
  "Bank CIMB Niaga",
  "Bank Danamon Indonesia",
  "Bank Ekonomi Raharja",
  "Bank Ganesha",
  "Bank Hana",
  "Bank ICB Bumiputra",
  "Bank ICBC Indonesia",
  "Bank Index Selindo",
  "Bank Maybank Indonesia",
  "Bank Maspion",
  "Bank Mayapada",
  "Bank Mega",
  "Bank Mestika Dharma",
  "Bank Metro Express",
  "Bank Nusantara Parahayangan",
  "Bank OCBC NISP",
  "Bank of India Indonesia",
  "Panin Bank",
  "Bank Permata",
  "Bank QNB Kesawan",
  "Bank SBI Indonesia",
  "Bank Sinarmas",
  "Bank UOB Indonesia",
  "Anglomas International Bank",
  "Bank Andara",
  "Bank Artos Indonesia",
  "Bank Bisnis Internasional",
  "Centrama Nasional Bank",
  "Bank Dipo International",
  "Bank Fama International",
  "Bank Harda International",
  "Bank Ina Perdana",
  "Bank Jasa Jakarta",
  "Bank Kesejahteraan Ekonomi",
  "Bank Liman International",
  "Bank Mayora",
  "Bank Mitraniaga",
  "Bank Multi Arta Sentosa",
  "Bank Nationalnobu",
  "Prima Master Bank",
  "Bank Pundi Indonesia",
  "Bank Royal Indonesia",
  "Bank Sahabat Purba Danarta",
  "Bank Sinar Harapan Bali",
  "Bank Tabungan Pensiunan Nasional",
  "Bank Victoria International",
  "Bank Yudha Bhakti",
  "Bank Jambi (Jambi)",
  "Bank Kalsel (Banjarmasin)",
  "Bank Kaltim (Samarinda)",
  "Bank Sultra (Kendari)",
  "Bank BPD DIY (Yogyakarta)",
  "Bank Nagari (Padang)",
  "Bank DKI (Jakarta)",
  "Bank Lampung (Bandar Lampung)",
  "Bank Kalteng (Palangka Raya)",
  "Bank BPD Aceh (Banda Aceh)",
  "Bank Sulsel (Makassar)",
  "Bank BJB (Bandung)",
  "Bank Kalbar (Pontianak)",
  "Bank Maluku (Ambon)",
  "Bank Bengkulu (Bengkulu)",
  "Bank Jateng (Semarang)",
  "Bank Jatim (Surabaya)",
  "Bank NTB (Mataram)",
  "Bank NTT (Kupang)",
  "Bank Sulteng (Palu)",
  "Bank Sulut (Manado)",
  "Bank BPD Bali (Denpasar)",
  "Bank Papua (Jayapura)",
  "Bank Riau Kepri (Pekanbaru)",
  "Bank Sumsel Babel (Palembang)",
  "Bank Sumut (Medan)",
  "Bank ANZ Indonesia",
  "Bank Commonwealth",
  "Bank Agris",
  "Bank BNP Paribas Indonesia",
  "Bank Capital Indonesia",
  "Bank Chinatrust Indonesia",
  "Bank DBS Indonesia",
  "Bank International Indonesia (BII)",
  "Bank KEB Indonesia",
  "Bank Mizuho Indonesia",
  "Bank Rabobank International Indonesia",
  "Bank Resona Perdania",
  "Bank Sumitomo Mitsui Indonesia",
  "Bank Windu Kentjana International",
  "Bank Woori Indonesia",
  "Bank of Ameriza",
  "Bangkok Bank",
  "Bank of China",
  "Citibank",
  "Deutsche Bank",
  "HSBC",
  "JPMorgan Chase",
  "Royal Bank of Scotland",
  "Standard Chartered",
  "The Bank of Tokyo Mitsubishi UFJ",
  "Bank BNI Syariah",
  "Bank Muamalat Indonesia",
  "Bank Syariah Mandiri",
  "BCA Syariah",
  "Bank BJB Syariah",
  "Bank BRI Syariah",
  "Bank Mega Syariah",
  "Panin Bank Syariah",
  "Bank Syariah Bukopin",
  "Bank Victoria Syariah",
  "Bank Maybank Syariah Indonesia",
  "Bank BTN Syariah",
  "Bank Danamon Syariah",
  "CIMB Niaga Syariah",
  "BII Syariah",
  "OCBC NISP Syariah",
  "Bank Permata Syariah",
  "Bank BPD Aceh Syariah",
  "Bank DKI Syariah",
  "Bank Kalbar Syariah",
  "Bank Kalsel Syariah",
  "Bank NTB Syariah",
  "Bank Riau Kepri Syariah",
  "Bank Sumsel Babel Syariah",
  "Bank Sumut Syariah",
  "HSBC Amanah",
  "Bank Perkreditan Rakyat (BPR KS)"
]
````
