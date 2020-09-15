### [&laquo; Home](README.md)

[Bukalapak Image API](#bukalapak-image-api)
- [Create Image](#create-image)
    - [Resource URL](#resource-url)
    - [Parameters](#parameters)
    - [Example Request](#example-request)
    - [Example Response](#example-response)

- [Image Status](#image-status)
    - [Resource URL](#resource-url)
    - [Parameters](#parameters)
    - [Example Request](#example-request)
    - [Example Response](#example-response)

- [Delete Image](#delete-image)
    - [Resource URL](#resource-url)
    - [Parameters](#parameters)
    - [Example Request](#example-request)
    - [Example Response](#example-response)

## Bukalapak Image API

### Create Image
Create Image
+ Use `POST` http method.

##### Resource URL
+ [https://api.bukalapak.com/v2/images.json]()

##### Parameters
None

##### POST request data
None

##### Example Request
````sh
curl -u 15:wcrG8WPPWaq9Ndiesbjn https://api.bukalapak.com/v2/images.json -F file=@product-image.png -X POST

````

##### Example Response
Success response:
````json
{
  "status":"OK",
  "id": "157324",
  "message":null
}
````

Failed response
````json
{
  "status":"ERROR",
  "user_id":"null",
  "message":"Harus berupa file gambar"
}
````

### Image Status
Check image status whether it has been assigned to a product or not.
+ Use `GET` http method.

##### Resource URL
+ [https://api.bukalapak.com/v2/images/status/:id.json]()

##### Parameters
+ `id` *(required)*. Image identifier.

##### Example Request
````sh
curl -u 15:wcrG8WPPWaq9Ndiesbjn https://api.bukalapak.com/v2/images/status/181244.json

````

##### Example Response
Response for image without product:
````json
{
  "status":"OK",
  "id":1838301,
  "message":"Orphaned"
}
````

Response for image that has been assigned to product.
````json
{
  "status":"ERROR",
  "user_id":1838301,
  "message":"Assigned"
}
````

### Delete Image
Delete image.
+ Use `DELETE` http method.

##### Resource URL
+ [https://api.bukalapak.com/v2/images/:id.json]()

##### Parameters
+ `id` *(required)*. Image identifier.

##### Example Request
````sh
curl -u 15:wcrG8WPPWaq9Ndiesbjn -X DELETE https://api.bukalapak.com/v2/images/181244.json

````

##### Example Response
Response when deleting image:
````json
{
  "status":"OK",
  "id":1838301,
  "message":"Image deleted"
}
````

Response for nonexistent image.
````json
{
  "status":"ERROR",
  "user_id":1838301,
  "message":"Failed to delete image"
}
````

Response when trying to delete another user's image.
````json
{
  "status":"ERROR",
  "user_id":1838301,
  "message":"Can't delete another user's image"
}
````
