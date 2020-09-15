### [&laquo; Home](README.md)

[Bukalapak Product Category API](#bukalapak-product-category-api)
- [List Category](#list-category)
    - [Resource URL](#resource-url)
    - [Parameters](#parameters)
    - [Example Request](#example-request)
    - [Example Response](#example-response)
- [Category Attributes](#category-attributes)
    - [Resource URL](#resource-url)
    - [Parameters](#parameters)
    - [Example Request](#example-request)
    - [Example Response](#example-response)
- [Dictionary](#dictionary)

## Bukalapak Product Category API

### List Category
Get all `product's category`

You can optionally set `If-None-Match` header or `Etag` header. If request `Etag` match, server will send `304 Not Modified` response without body.

Server will set `Etag` header to every request to this resource.

+ Use `GET` http method.

##### Resource URL
+ [https://api.bukalapak.com/v2/categories.json]()

##### Parameters
None

##### Example Request
````sh
curl -u 67287:lXymG93y83m6RHzZV5FY https://api.bukalapak.com/v2/categories.json

````

##### Example Response
````json
{
  "status": "OK",
  "categories": [
    {
      "id": 64,
      "name": "Sepeda",
      "children": [
        {
          "id": 242,
          "name": "Fullbike",
          "children": [
            {
              "id": 370,
              "name": "MTB"
            },
            {
              "id": 371,
              "name": "Roadbike"
            }
          ]
        },
        {
          "id": 85,
          "name": "Frame",
          "children": [
            {
              "id": 372,
              "name": "MTB"
            },
            {
              "id": 373,
              "name": "Roadbike"
            }
          ]
        }
      ]
    },
    {
      "id": 10,
      "name": "Kamera",
      "children": [
        {
          "id": 186,
          "name": "Kamera Digital"
        },
        {
          "id": 350,
          "name": "Kamera Analog"
        }
      ]
    },
  ]
}
````

### Category Attributes
Get attributes for a category

You can optionally set `If-None-Match` header or `Etag` header. If request `Etag` match, server will send `304 Not Modified` response without body.

Server will set `Etag` header to every request to this resource.

+ Use `GET` http method.

##### Resource URL
+ [https://api.bukalapak.com/v2/categories/:id/attributes.json]()

##### Parameters
None

##### Example Request
````sh
curl -u 67287:lXymG93y83m6RHzZV5FY https://api.bukalapak.com/v2/categories/8/attributes.json

````

##### Example Response
````json
{
    "status": "OK",
    "attributes": [
        {
            "fieldName": "brand",
            "displayName": "Merek",
            "inputType": "select",
            "options": [
                "Oppo",
                "Andromax",
                "iPhone",
                "Acer",
                "Advan",
                "Nokia",
                "Samsung",
                "Sony Ericsson",
                "TiPhone",
                "Lain-lain"
            ],
            "required": true
        },
        {
            "fieldName": "operating_system",
            "displayName": "Operating System",
            "inputType": "select",
            "options": [
                "Blackberry",
                "Android",
                "iOS",
                "Windows Phone",
                "Symbian",
                "Linux",
                "Non Smartphone"
            ],
            "required": true
        },
        {
            "fieldName": "features",
            "displayName": "Features",
            "inputType": "check_boxes",
            "options": [
                "Touchscreen",
                "Wifi",
                "Bluetooth",
                "3G",
                "GPS Navigation",
                "Video Player",
                "Front Camera",
                "QWERT Keyboard",
                "Dual Sim Card"
            ],
            "required": true
        },
        {
            "fieldName": "bentuk",
            "displayName": "Bentuk",
            "inputType": "select",
            "options": [
                "Klasik (Bar)",
                "Sliding",
                "Flip"
            ],
            "required": true
        },
        {
            "fieldName": "display_size",
            "displayName": "Display Size",
            "inputType": "select",
            "options": [
                "1.8\"",
                "4.5\"",
                "5.0\"",
                "7.0\""
            ],
            "required": false
        },
        {
            "fieldName": "camera",
            "displayName": "Camera",
            "inputType": "select",
            "options": [
                "Camera",
                "No Camera"
            ],
            "required": true
        },
        {
            "fieldName": "garansi",
            "displayName": "Garansi",
            "inputType": "select",
            "options": [
                "Tidak bergaransi",
                "1-12 bulan",
                "2 tahun"
            ],
            "required": true
        },
        {
            "fieldName": "network",
            "displayName": "Network",
            "inputType": "select",
            "options": [
                "CDMA",
                "GSM",
                "Dual GSM-CDMA",
                "Dual GSM-GSM"
            ],
            "required": true
        },
        {
            "fieldName": "body_color",
            "displayName": "Body Color",
            "inputType": "check_boxes",
            "options": [
                "Hitam",
                "Putih",
                "Silver",
                "Emas kuning",
                "Hijau",
                "Ungu"
            ],
            "required": true
        }
    ],
    "message": null
}
````

### Dictionary
- `inputType` Type of input. *No shit Sherlock*. Possible value are
    - `string`, equivalent to `input` type `text` tag in html
    - `text`, equivalnet to `textarea`
    - `select`, `combo_select`, equivalent to `select`
    - `boolean`, `check_boxes`, equivalent to `input` type `checkbox`
    - `radio_buttons`, equivalent to `input` type `radio`
