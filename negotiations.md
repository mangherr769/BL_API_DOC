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
<!-- - [Create Negotiation](#create-negotiation)
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
## Bukalapak Negotiations API

### Negotation Listing
Get list of negotiations owned by user

+ Use `GET` http method.
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v1/negotiations.json]().

##### Parameters
+ `page` *(optional)*. 
+ `per_page` *(required)*.

##### Example Request
```sh
curl -u 110677:JheQQS0OKApu3hGJwkRH https://api.bukalapak.com/v1/negotiations.json
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
      "name":"BL Test-17",
      "url":"https://www.bukalapak.com/p/fashion/men/accessories-jewelry-170/fq96_-bl-test-17"
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

### Accept Negotation
Accept incoming negotiation

+ Use `PUT` http method.
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v1/negotiations/:id/accept.json]().

##### Parameters
None

##### Example Request
```sh
curl -u 110677:JheQQS0OKApu3hGJwkRH -d {} https://api.bukalapak.com/v1/negotiations/124/accept.json -X PUT
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
      "name":"BL Test-17",
      "url":"https://www.bukalapak.com/p/fashion/men/accessories-jewelry-170/fq96_-bl-test-17"
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

### Reject Negotation
Reject incoming negotiation

+ Use `PUT` http method.
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v1/negotiations/:id/reject.json]().

##### Parameters
None

##### Example Request
```sh
curl -u 110677:JheQQS0OKApu3hGJwkRH -d {} https://api.bukalapak.com/v1/negotiations/124/reject.json -X PUT
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
      "name":"BL Test-17",
      "url":"https://www.bukalapak.com/p/fashion/men/accessories-jewelry-170/fq96_-bl-test-17"
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

<!-- ### Create Negotation
Create a new negotiation

+ Use `POST` http method.
+ Requires authentication

##### Resource URL
+ [https://api.bukalapak.com/v1/negotiations.json]().

##### Parameters
None

##### POST request data
+ `amount` *(required)*. Ammount of negotiation
+ `product_id` *(required)*. Product ID which negotiation will be addressed
+ `quantity` *(required)*. Quantity of the product to be negotiated

##### Example Request
```sh
curl -u 110677:JheQQS0OKApu3hGJwkRH -d '{ "amount":"1400000", "product_id":"gglq", "quantity":"1" }' https://api.bukalapak.com/v1/negotiations.json -H "Content-Type: application/json" -X POST
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
+ [https://api.bukalapak.com/v1/negotiations/:id.json]().

##### Parameters
None

##### PUT request data
+ `status` *(required)*. can be one of the following: "accept", "reject", "cancel", or "update"
+ `amount` *(required)*. Ammount of negotiation if status is "update"

##### Example Request
Cancel Negotiation, Reject Negotiation, Accept Negotiation:
```sh
curl -u 110677:JheQQS0OKApu3hGJwkRH -d '{ "status":"accept" }' https://api.bukalapak.com/v1/negotiations/10537.json -H "Content-Type: application/json" -X PUT
```
Update Negotiation:
```sh
curl -u 110677:JheQQS0OKApu3hGJwkRH -d '{ "status":"update", "amount":"1350000" }' https://api.bukalapak.com/v1/negotiations/10537.json -H "Content-Type: application/json" -X PUT
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