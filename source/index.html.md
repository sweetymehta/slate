---
title: API Reference

<!-- language_tabs:
  - shell
  - ruby
  - python
  - javascript -->

<!-- toc_footers: -->
  <!-- - <a href='#'>Sign Up for a Developer Key</a> -->
  <!-- - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a> -->

includes:
  - errors

search: true
---

# Authentication

> To authorize, use this api request:

```json
 { "user": 
    {"email": "ida@stoltenbergstiedemann.com", 
      "uname": "", "password": "123456" 
    } 
 }
```


This endpoint do SignIn with user as manager.

### HTTP Request

`POST /api/v1/users/sign_in`

# Items

## Get All Items

> Request Format

```json
 Not Required
```

This endpoint retrieves all items corresponding to an outlet.

### HTTP Request

`GET /api/v1/items?outlet_id=3`

### Query Parameters

Parameter | value   | Description
--------- | ------- | -----------
outlet_id | id      | Get outlets by using index of outlets


## Create an item

> Request Format

```json
{ "item": 
  {
  "name": 390,
  "description": 3,
  "sale_tax": 3,
  "vat": "",
  "typ": "multi" or "item", 
  "price": 50,
  "status": pending/complete/online
  "parent_id": 2 <-- parent_id is required if current item is subcategory
  }
"outlet_id": 1
}
```

This endpoint creates an item.

### HTTP Request

`POST /api/v1/items`
