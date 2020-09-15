### [&laquo; Home](README.md)

[Bukalapak Products API](#bukalapak-products-api)
- [List Products](#list-products)
	- [Resource URL](#resource-url)
	- [Parameters](#parameters)
	- [Example Request](#example-request)
	- [Example Response](#example-response)
- [My Lapak](#my-lapak)
	- [Resource URL](#resource-url)
	- [Parameters](#parameters)
	- [Example Request](#example-request)
	- [Example Response](#example-response)
- [Create Product](#create-product)
	- [Resource URL](#resource-url)
	- [Parameters](#parameters)
	- [POST request data](#post-request-data)
	- [Example Request](#example-request)
	- [Example Response](#example-response)
- [Update Product](#update-product)
	- [Resource URL](#resource-url)
	- [Parameters](#parameters)
	- [PUT request data](#put-request-data)
	- [Example Request](#example-request)
	- [Example Response](#example-response)
- [Read Product](#read-product)
	- [Resource URL](#resource-url)
	- [Parameters](#parameters)
	- [Example Request](#example-request)
	- [Example Response](#example-response)
- [Sold Product](#sold-product)
	- [Resource URL](#resource-url)
	- [Parameters](#parameters)
	- [Example Request](#example-request)
	- [Example Response](#example-response)
- [Relist Product](#relist-product)
	- [Resource URL](#resource-url)
	- [Parameters](#parameters)
	- [Example Request](#example-request)
	- [Example Response](#example-response)
- [Delete Product](#delete-product)
	- [Resource URL](#resource-url)
	- [Parameters](#parameters)
	- [Example Request](#example-request)
	- [Example Response](#example-response)
- [Dictionary](#dictionary)

## Bukalapak Products API

### List Products
Get a number of products. If parameter `keywords` exist, this will give a number of products matching with keywords `keywords`

You can optionally set `If-None-Match` header or `Etag` header. If request `Etag` match, server will send `304 Not Modified` response without body.

Server will set `Etag` header to every request to this resource.

+ Use `GET` http method.

##### Resource URL
+ [https://api.bukalapak.com/v2/products.json](). No search parameter provided.
+ [https://api.bukalapak.com/v2/products.json?keywords=mtb](). Show products match with keywords `mtb`.
+ [https://api.bukalapak.com/v2/products.json?page=1&per_page=10](). First ten products.

##### Parameters
+ `keywords` *(optional)*. Keywords use to search products.
+ `page` *(optional)*. Pagination page, default to `0`.
+ `per_page` *(optional)*. Number results per_page, default to `20`. Allowed values `6, 18, 20, 40, 80`.
+ `nego` & `harga_pas` *(optional)*. If searching for negotiable products, set `nego` to `1` and `harga_pas` to `0`. If searching for non-negotiable products, set `nego` to `0` and `harga_pas` to `1`. If given the same values, search result returns both negotiable and non-negotiable products.

##### Example Request by Keywords
```sh
curl -u 67287:lXymG93y83m6RHzZV5FY \
"https://api.bukalapak.com/v2/products.json?keywords=fixie&page=2&per_page=20"

curl -u 67287:lXymG93y83m6RHzZV5FY -H 'If-None-Match: "9c17139c006bd5e543028b12b978967b"' \
"https://api.bukalapak.com/v2/products.json"
```

##### Example Response by Keywords
```json
{
	"status":"OK",
	"products":[{
		"id":"mtvk",
		"category":"Fixie",
		"category_structure":["Sepeda","Frame","Fixie"],
		"name":"Frameset BRAIN Atales (NEW) Pink Sz 52 On SALE!!!",
		"city":"Jakarta Timur",
		"province":"DKI Jakarta",
		"price":850000,
		"images":["https://s4.bukalapak.com/system/images/2/5/9/1/4/2/4/large/image.jpg?1372228356"],
		"small_images":["https://s4.bukalapak.com/system/images/2/5/9/1/4/2/4/small/image.jpg?1372228356"],
		"url":"https://www.bukalapak.com/p/sepeda/frame/fixie-376/mtvk_-frameset-brain-atales-new-pink-sz-52-on-sale",
		"desc":"Frameset BRAIN Atales (NEW) Pink Sz 52 SALE!!!\r\n\r\nIncld:\r\n- frame\r\n- fork\r\n- headset",
		"condition":"new",
		"nego":false,
		"seller_name":"S S",
		"payment_ready":true,
		"stock":1,
		"specs":{
			"brand":"Lain-lain",
			"type":"Track",
			"bahan":"Alloy",
			"ukuran":"52",
			"ukuran_seat_tube":"27,2",
			"ukuran_headtube":"1 1/8 inch (Over Size)"
		},
		"state_description": []
	}],
	"message":null
}
```

##### Example Request by Keywords, Minimum Price and Maximum Price
```sh
curl -u 67287:lXymG93y83m6RHzZV5FY \
"https://api.bukalapak.com/v2/products.json?keywords=galaxy+tab&price_range=on&price_min=3300000&price_max=3500000"
```

##### Example Response by Keywords, Minimum Price and Maximum Price
```json
{
	"status":"OK",
	"products":[{
		"id":"ix45",
		"category":"Handphone (HP)",
		"category_structure":["HP & Elektronik","Handphone (HP)"],
		"name":"Dijual Galaxy Tab 2, 7inch",
		"city":"Jakarta Utara",
		"province":"DKI Jakarta",
		"price":3350000,
		"images":["https://s2.bukalapak.com/system/images/2/1/2/9/3/2/2/large/20130211_143503.jpg?1362242270"],
		"small_images":["https://s2.bukalapak.com/system/images/2/1/2/9/3/2/2/small/20130211_143503.jpg?1362242270"],
		"url":"https://www.bukalapak.com/p/hp-elektronik/handphone-hp/ix45_-dijual-galaxy-tab-2-7inch",
		"desc":"barang lengkap, mulus, pembelian, jadi masi garansi :)",
		"condition":"used",
		"nego":true,
		"seller_name":"hendrik poltak",
		"payment_ready":true,
		"stock":1,
		"specs":{
			"brand":"Samsung",
			"operating_system":"Android",
			"features":[
				"Touchscreen",
				"Wifi",
				"Bluetooth",
				"3G",
				"GPS Navigation",
				"Memory Card Slots",
				"MP3",
				"Message",
				"e-mail",
				"Video Player",
				"Front Camera",
				"QWERT Keyboard",
				""
			],
			"bentuk":"Klasik (Bar)",
			"display_size":"7.0\"",
			"camera":"Camera",
			"garansi":"1-12 bulan",
			"network":"GSM",
			"body_color":"putih"
		},
		"state_description": []
	}],
	"message":null
}
```

##### Example Request by Brand
```sh
curl -u 67287:lXymG93y83m6RHzZV5FY \
"https://api.bukalapak.com/v2/products.json?brand=Polygon"
```

##### Example Response by Brand
```json
{
	"status":"OK",
	"products":[{
		"id":"n2fc",
		"category":"MTB",
		"category_structure":["Sepeda","Fullbike","MTB"],
		"name":"Polygon Cozmic RXX Carbon size:16\" kondisi Baru Groupset XTR",
		"city":"Cilacap",
		"province":"Jawa Tengah",
		"price":21000000,
		"images":["https://s1.bukalapak.com/system2/images/2/6/1/6/0/8/1/large/DSCN6379a.JPG?1372661546"],
		"small_images":["https://s1.bukalapak.com/system2/images/2/6/1/6/0/8/1/small/DSCN6379a.JPG?1372661546"],
		"url":"https://www.bukalapak.com/p/sepeda/fullbike/mtb/n2fc_-polygon-cozmic-rxx-carbon-size16-kondisi-baru-groupset-xtr--3",
		"desc":"Polygon Cozmic RXX Carbon size:16 kondisi Baru Groupset XTR + Fork Mosso...",
		"condition":"new",
		"nego":true,
		"seller_name":
		"Bernadus Hariyanto (Ghober168)",
		"payment_ready":true,
		"stock":1,
		"specs":{
			"brand":"Polygon",
			"type":"XC (Cross Country)",
			"bahan":null,
			"ukuran":null
		},
		"state_description": []
	}],
	"message":null
}
```

##### Example Request by Nego
```sh
curl -u 67287:lXymG93y83m6RHzZV5FY \
"https://api.bukalapak.com/v2/products.json?nego=1
```

##### Example Response by Nego
```json
{
	"status":"OK",
	"products":[{
		"id":"n2he",
		"category":"MTB",
		"category_structure":["Sepeda","Frame","MTB"],
		"name":"frame dartmoor hornet 2013",
		"city":"Tangerang Selatan",
		"province":"Banten",
		"price":2600000,
		"images":["https://s0.bukalapak.com/system2/images/2/6/1/6/2/7/5/large/20130528_103510.jpg?1372663040"],
		"small_images":["https://s0.bukalapak.com/system2/images/2/6/1/6/2/7/5/small/20130528_103510.jpg?1372663040"],
		"url":"https://www.bukalapak.com/p/sepeda/frame/mtb-372/n2he_-frame-dartmoor-hornet-2013--2",
		"desc":"frame dartmoor hornet 2013..kondisi mulus..pemakaian  bln mei 2013..",
		"condition":"used",
		"nego":true,
		"seller_name":"denny irenk",
		"payment_ready":true,
		"stock":1,
		"specs":{
			"brand":"Dartmoor",
			"type":"All Mountain",
			"bahan":"Alloy",
			"ukuran":"14.5",
			"Spacing":null,
			"ukuran_seat_tube":"",
			"ukuran_headtube":"1 1/8 inch (Over Size)"
		},
		"state_description":[]
	}],
	"message":null
}
```

##### Example Request by Keywords and Range Price
```sh
curl -u 67287:lXymG93y83m6RHzZV5FY \
"https://api.bukalapak.com/v2/products.json?keywords=blackberry&price_range=5000000-10000000"
```

##### Example Response by Keywords and Range Price
```json
{
	"status":"OK",
	"products":[
		{
			"id":"n2hf",
			"category":"Handphone (HP)",
			"category_structure":["HP & Elektronik","Handphone (HP)"],
			"name":"BLACKBERRY Q10 GARANSI RESMI SCM (Authorised Distributor)",
			"city":"Jakarta Selatan",
			"province":"DKI Jakarta",
			"price":6999000,
			"images":["https://s4.bukalapak.com/system/images/2/6/1/6/2/7/4/large/q10_scm.jpg?1372662756"],
			"small_images":["https://s4.bukalapak.com/system/images/2/6/1/6/2/7/4/small/q10_scm.jpg?1372662756"],
			"url":"https://www.bukalapak.com/p/hp-elektronik/handphone-hp/n2hf_-blackberry-q10-garansi-resmi-scm-authorised-distributor",
			"desc":"BLACKBERRY Q10\r\nKondisi: BRAND NEW IN BOX (BNIB).\r\nGARANSI: 2 TAHUN dari SCM ...",
			"condition":"new",
			"nego":false,
			"seller_name":"superx07",
			"payment_ready":true,
			"stock":10,
			"specs":{
				"brand":"Blackberry",
				"operating_system":"Blackberry",
				"features":[""],
				"bentuk":"Klasik (Bar)",
				"display_size":"3.2\"",
				"camera":"Camera",
				"garansi":"1-12 bulan",
				"network":"GSM",
				"body_color":"putih"
			},
			"state_description":[]
		}],
	"message":null
}
```

##### Example Request by Keywords and New Condtions
```sh
curl -u 67287:lXymG93y83m6RHzZV5FY \
"https://api.bukalapak.com/v2/products.json?keywords=nikon&conditions\[\]=new"
```

##### Example Response by Keywords and New Condtions
```json
{
	"status":"OK",
	"products":[{
		"id":"n1vh",
		"category":"Digital Camera",
		"category_structure":["Kamera","Digital Camera"],
		"name":"Nikon D7000 KIT",
		"city":"Surabaya",
		"province":"Jawa Timur",
		"price":2250000,
		"images":["https://s0.bukalapak.com/system2/images/2/6/1/4/5/0/5/large/950.jpg?1372648607"],
		"small_images":["https://s0.bukalapak.com/system2/images/2/6/1/4/5/0/5/small/950.jpg?1372648607"],
		"url":"https://www.bukalapak.com/p/kamera/digital-camera/n1vh_-nikon-d7000-kit--39",
		"desc":"Barang 100% asli original\r\nNikon D7000 ...",
		"condition":"new",
		"nego":false,
		"seller_name":"mitra_kamera72",
		"payment_ready":true,
		"stock":1,
		"specs":{
			"type":"D-SLR",
			"brand":"Nikon",
			"megapixel":"<5.00MP",
			"optical_zoom":"0",
			"screen_size":"",
			"garansi":"1-12 bulan",
			"memory_card_type":"MicroSD",
			"body_color":"hitam",
			"video":"Yes",
			"image_stabilization":""
		},
		"state_description":[]
	}],
	"message":null
}
```

##### Example Request by Keywords and Used Condtions
```sh
curl -u 67287:lXymG93y83m6RHzZV5FY \
"https://api.bukalapak.com/v2/products.json?keywords=canon&conditions\[\]=used"
```

##### Example Response by Keywords and Used Condtions
```json
{
	"status":"OK",
	"products":[{
		"id":"n2gn",
		"category":"Digital Camera",
		"category_structure":["Kamera","Digital Camera"],
		"name":"Canon EOS 650D, Sigma 30mm f1.4 EX DC HSM, Canon Speedlite 320EX",
		"city":"Jakarta Selatan",
		"province":"DKI Jakarta",
		"price":11000000,
		"images":["https://s0.bukalapak.com/system2/images/2/6/1/6/1/9/5/large/Objektiv.jpg?1372662175"],
		"small_images":["https://s0.bukalapak.com/system2/images/2/6/1/6/1/9/5/small/Objektiv.jpg?1372662175"],
		"url":"https://www.bukalapak.com/p/kamera/digital-camera/n2gn_-canon-eos-650d-sigma-30mm-f14-ex-dc-hsm-canon-speedlite-320ex",
		"desc":"Dijual paketan ataupun ketengan:\r\n\r\nBody Canon EOS 650D (dus kit) beserta perlengkapannya Rp ensa Sigma 30mm f/1.4 EX DC HSM Rp 5.000.000\r\n\r\nSpeedlite Canon 320EX Rp 1.500.000\r\n\r\nSemuanya beli awal 2013 di JPC, masih bergaransi, mulus.\r\n\r\nBoleh beli paketan komplit  atau dimutilasi dengan harga seperti yang udah ditulis.\r\n\r\nFoto yang ada sementara masih ambil dari internet karena barang di rumah, nanti akan diupdate :)",
		"condition":"used",
		"nego":true,
		"seller_name":"Kevin Oei",
		"payment_ready":true,
		"stock":1,
		"specs":{
			"type":"D-SLR",
			"brand":"Canon",
			"megapixel":"10.0 - 20.0MP",
			"optical_zoom":"0",
			"screen_size":"",
			"garansi":"1-12 bulan",
			"memory_card_type":"MicroSD",
			"body_color":"hitam",
			"video":"Yes",
			"image_stabilization":""
		},
		"state_description":[]
	}],
	"message":null
}
```


### My Lapak
Get current user's store (lapak). Products returned for this request are those which can be purchased.

You can optionally set `If-None-Match` header or `Etag` header. If request `Etag` match, server will send `304 Not Modified` response without body.

Server will set `Etag` header to every request to this resource.

+ Use `GET` http method.

##### Resource URL
+ [https://api.bukalapak.com/v2/products/mylapak.json](). No search parameter available. Get products which **can be purchased**.
+ [https://api.bukalapak.com/v2/products/mylapak.json?not_for_sale_only=1](). Get products which **can not be purchased**.

##### Parameters
+ `not_for_sale_only` *(optional)*. Ask to return products which can not be purchased if set to **1**

##### Example Request
```sh
curl -u 67287:lXymG93y83m6RHzZV5FY \
"https://api.bukalapak.com/v2/products/mylapak.json"
```

##### Example Response
```json
{
	"status":"OK",
	"products":[
		{
		  "id":"mab5",
		  "category":"Suspension",
		  "category_structure":["Sepeda","Fork & Suspension","Suspension"],
		  "name":"Testing BL App",
		  "city":"Jakarta Selatan",
		  "province":"DKI Jakarta",
		  "price":1250000,
		  "image_ids":[123132]
		  "images":["https://s1.bukalapak.com/system/images/2/5/3/2/7/3/6/large/IMG_0205.JPG?1371219033"],
		  "small_images":["https://s1.bukalapak.com/system/images/2/5/3/2/7/3/6/small/IMG_0205.JPG?1371219033"],
		  "url":"https://www.bukalapak.com/p/sepeda/fork-suspension/suspension/mab5_-testing-bl-app",
		  "desc":"Test upload from BL App, please ignore",
		  "condition":"new",
		  "nego":true,
		  "seller_name":"Me Oww",
		  "payment_ready":true,
		  "specs":{
		    "merk_shock":null,
		    "size_shock":null,
		    "spring":null
		  },
		  "state_description":[]
		}
	]
}
```

### Create Product
Create a new product

+ Use `POST` http method.
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/products.json]().

##### Parameters
None

##### POST request data
+ `product` *(required)*. Attributes of new product in JSON. Attributes constructed by following fields:
	+ `category_id` *(required)*. Category of new product. [Check this page for valid categories](categories.md#list-category).
	+ `name` *(required)*. Product name.
	+ `price` *(required)*. Product price.
	+ `weight` *(required)*. Product weight in grams.
	+ `stock` *(required)*. Number new product in stock.
	+ `description_bb` *(required)*. Description for new product. You can use BBCode format.
	+ `new` *(optional)*. Product condition as in *new* or *used*. Possible value are *true* for *new* and *false* for *used* product.
	+ `negotiable` *(optional)*. This field indicate whether new product price is negotiable or not. Possible value are *false* for fixed price and *true* for negotiable price. Default value is *false*.
	+ `product_detail_attributes` *(optional)*. Details attributes for product in JSON. [Attributes are vary based on category of product](categories.md#category-attributes). Some of these fields are:
		+ `type` *(optional)*. Tyoe of product. For product categorized as *fullbike* type can be *MTB*, *Roadbike*, etc.
		+ `brand` *(optional)*. For *Fullbike*, brand can be *United*, *Polygon*, etc.
		+ `ukuran` *(optional)*.
		+ `bahan` *(optional)*.
+ `images` *(required)*. List of images identifier for new product. Required between 1-5 images. Muliple images separated by comma. Image should be created first and image can be used only for one product. More on [images](images.md#create-image)

##### Example Request
```sh
curl -u 67287:lXymG93y83m6RHzZV5FY \
-d '{ \
	"product": { "category_id":"242", "name":"Polygon Helios 200", "new":"true", "price":"2700000", "negotiable":"true", "weight":"5000", "stock":"2", "description_bb":"Sepeda roadbike polygon series helios 200", \
	"product_detail_attributes":{ "type":"Roadbike", "brand":"Polygon", "bahan":"Cromoly" } }, \
	"images":"10820,10822,10283"}' \
"https://api.bukalapak.com/v2/products.json" -H "Content-Type: application/json" -X POST
```

##### Example Response
Failed example
```json
{
	"status":"ERROR",
	"id":null,
	"message":"Image tidak boleh kosong"
}
```
Successfull example
```json
{
	"status":"OK",
	"id":"kxvi",
	"message":"Product Added"
}
```

### Update Product
Update an existing user's product

+ Use `PUT` http method.
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/products/:id.json]().

##### Parameters
+ `id` *(required)*. Identifier for product being updated.

##### PUT request data
+ `product` *(required)*. Attributes of existing product in JSON. Attributes constructed by following fields:
	+ `name` *(optional)*. Product name.
	+ `price` *(optional)*. Product price.
	+ `weight` *(optional)*. Product weight in grams.
	+ `stock` *(optional)*. Number existing product in stock.
	+ `description_bb` *(optional)*. Description for existing product. You can use BBCode format.
	+ `new` *(optional)*. Product condition as in *new* or *used*. Possible value are *true* for *new* and *false* for *used* product.
	+ `negotiable` *(optional)*. This field indicate whether existing product price is negotiable or not. Possible value are *false* for fixed price and *true* for negotiable price. Default value is *false*.
	+ `product_detail_attributes` *(optional)*. Details attributes for product in JSON. [Attributes are vary based on category of product](categories.md#category-attributes). Some of these fields are:
		+ `type` *(optional)*. Tyoe of product. For product categorized as *fullbike* type can be *MTB*, *Roadbike*, etc.
		+ `brand` *(optional)*. For *Fullbike*, brand can be *United*, *Polygon*, etc.
		+ `ukuran` *(optional)*.
		+ `bahan` *(optional)*.
+ `new_images` *(optional)*. List of new images identifier for existing product. There should be between 1-5 images after adding new images . Multiple images separated by comma. Image should be created first and image can be used only for one product. More on [images](images.md#create-image)
+ `removed_images` *(optional)*. List of existing images identifier to be removed from existing product. There should be between 1-5 images after images deletion. Multiple images separated by comma. Image should be asscociated with existing product.

##### Example Request
```sh
curl -u 67287:lXymG93y83m6RHzZV5FY \
-d '{ "product": { "price":"2700000", "stock":"2" }, "new_images": "623525,4552235", "removed_images":"866632" }' \
"https://api.bukalapak.com/v2/products/f3vi.json" -H "Content-Type: application/json" -X PUT
```

##### Example Response
```json
{
	"status":"OK",
	"product": {
		"id":"f3vi",
		"category":"Handphone (HP)",
		"name":"Gemini PALING MAHAL (made in mexico)",
		"city":"Jakarta Selatan",
		"province":"DKI Jakarta",
		"price":2700000,
		"image":"https://s0.bukalapak.com/system/images/1/6/7/6/6/8/0/large/IMG00475-20121105-1431.jpg?1352105447",
		"small_images":"https://s0.bukalapak.com/system/images/1/6/7/6/6/8/0/small/IMG00475-20121105-1431.jpg?1352105447",
		"desc":"blackberry 8520 original\r\nnot fake / KW / grade ori\r\njudge by pic\r\nmade in mexico\r\nmemory card and battery not included\r\nberrindo\r\nbought it 2009 september\r\nbox, charger, etc included",
		"condition":"new",
		"nego":true
		"payment_ready":true
		"specs":{
			"brand":"Blackberry",
			"operating_system":"Blackberry",
			"features":["Wifi","Bluetooth","Memory Card Slots","MP3","Message","e-mail","Video Player","QWERT Keyboard",""],
			"bentuk":"Klasik (Bar)",
			"display_size":"",
			"camera":"Camera",
			"garansi":"Tidak bergaransi",
			"network":"GSM",
			"body_color":"hitam"
		},
		"state_description":[]
	},
	"message": "Product Updated"
}
```

### Read Product
Read a product

You can optionally set `If-None-Match` header or `Etag` header. If request `Etag` match, server will send `304 Not Modified` response without body.

Server will set `Etag` header to every request to this resource.

+ Use `GET` http method.

##### Resource URL
+ [https://api.bukalapak.com/v2/products/:id.json]().

##### Parameters
+ `id` *(required)*. Identifier for product being read.

##### Example Request
```sh
curl -u 67287:lXymG93y83m6RHzZV5FY \
"https://api.bukalapak.com/v2/products/kxvi.json" -H "Content-Type: application/json" -X GET
```

##### Example Response
Successfull example
```json
{
	"status":"OK",
	"product":
	{
		"id":kxvi,
		"category":"Handphone (HP)",
		"name":"NOKIA 5200- Black",
		"city":"Jakarta Selatan",
		"province":"DKI Jakarta",
		"price":2700000,
		"image":"https://s0.bukalapak.com/system/images/1/6/7/6/6/8/0/large/IMG00475-20121105-1431.jpg?1352105447",
		"desc":"blackberry 8520 original\r\nnot fake / KW / grade ori\r\njudge by pic\r\nmade in mexico\r\nmemory card and battery not included\r\nberrindo\r\nbought it 2009 september\r\nbox, charger, etc included",
		"condition":"new",
		"nego":true
		"payment_ready":false
		"specs":{
			"brand":"Blackberry",
			"operating_system":"Blackberry",
			"features":["Wifi","Bluetooth","Memory Card Slots","MP3","Message","e-mail","Video Player","QWERT Keyboard",""],
			"bentuk":"Klasik (Bar)",
			"display_size":"",
			"camera":"Camera",
			"garansi":"Tidak bergaransi",
			"network":"GSM",
			"body_color":"hitam"
		},
		"state_description":["Stok Habis", "Melanggar"]
	},
	"message":null
}
```

### Sold Product
Set Product to Sold

+ Use `PUT` http method.
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/products/:id/sold.json]().

##### Parameters
+ `id` *(required)*. Identifier for product being sold.

##### Example Request
```sh
curl -u 67287:lXymG93y83m6RHzZV5FY \
"https://api.bukalapak.com/v2/products/kxvi/sold.json" -H "Content-Type: application/json" -X PUT
```

##### Example Response
```json
{
	"status":"OK",
	"id": "kxvi",
	"message": "Product has been set to sold"
}
```

### Relist Product
Set Product to Available

+ Use `PUT` http method.
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/products/:id/relist.json]().

##### Parameters
+ `id` *(required)*. Identifier for product being relist.

##### Example Request
```sh
curl -u 67287:lXymG93y83m6RHzZV5FY \
"https://api.bukalapak.com/v2/products/kxvi/relist.json" -H "Content-Type: application/json" -X PUT
```

##### Example Response
```json
{
	"status":"OK",
	"id": "kxvi",
	"message": "Product has been set to available"
}
```

### Delete Product
Delete existing product

+ Use `DELETE` http method.
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v2/products/:id.json]().

##### Parameters
+ `id` *(required)*. Identifier for product being destroy.

##### Example Request
```sh
curl -u 67287:lXymG93y83m6RHzZV5FY \
"https://api.bukalapak.com/v2/products/kxvi.json" -H "Content-Type: application/json" -X DELETE
```

##### Example Response
Successfull example
```json
{
	"status":"OK",
	"id":"kxvi",
	"message": "Product Deleted"
}
```

### Dictionary
- `condition` Denote whether a product is a used item or new. Possible values **new**, **used**.
- `payment_ready` Denote whether a product can be purchase or not. Possible values **true**, **false**.
- `state_description` Explanation why a product can't be purchased. Possible values **Lapak Tutup**, **Stok Habis**, **Melanggar**, **Penjual Tidak Aktif**.
- `nego` Denote whether buyer can negotiate for product price. Possible values **true**, **false**.
