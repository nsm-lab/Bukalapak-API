### [Bukalapak API](README.md) Forked from [orihalcum](https://github.com/orihalcum/api_doc)

Notes: URI changed from /v1 to /v2.

## Introduction

Some of resources and url require authentication.
Authentication uses `user_id` and `token` which can be obtained in two ways.
+ By API call to [Authentication for Bukalapak API](authenticate.md#authentication-for-bukalapak-api).
  You need to specify `username` or `email` and `password` of your Bukalapak account.
+ By manually visiting [API Secret Page](https://www.bukalapak.com/users/api_secret) at Bukalapak.

## Resources
+ [Authentication for Bukalapak API](authenticate.md#-home)
+ [Bukalapak Products API](products.md#-home)
+ [Bukalapak Product Category API](categories.md#-home)
+ [Bukalapak Image API](images.md#-home)
+ [Bukalapak Transaction API](transactions.md#-home)
+ [Bukalapak BukaDompet API](dompet.md#-home)
+ [Bukalapak Negotiation API](negotiations.md#-home)
+ [Bukalapak Message API](messages.md#-home)
+ [Bukalapak User API](users.md#-home)

## Debugging
+ We provide logging to store your API request parameters. Find it in [API Secret Page](https://www.bukalapak.com/users/api_secret)
+ Tips: turn on `verbose` flag to inspect response from server, i.e. `curl -v https://api.bukalapak.com/v2/object.json`
