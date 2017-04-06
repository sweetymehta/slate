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

## Update an item

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

This endpoint updates an item.

### HTTP Request

`PUT /api/v1/items/:id`


# Orders

## Get All Orders for a outlet
> Request Format

```json
NOT REQUIRED
```

### HTTP REQUEST
`GET /api/v1/orders?outlet_id=3`

## Create an Order
> Request Format

```json
{
  "order": {
  "total_amt": 4602.0,
  "total_items": 3,
  "items": [{
    "productDeescription": [{
      "displayName": "Size",
      "displayValue": "12 Inch",
      "id": 1,
      "type": "ItemVariation",
      "value": [3] // 3 is id of option taken from ingredient
      }, {
      "displayName": "Extras",
      "displayValue": "Premiuim Veg, Cheese",
      "id": 1,
      "type": "Customization",
      "value": [{"2": 2}, {"3": 1}] // 2,1 are ids of option taken from ingredient
      }],
      "name": "Choco Chip Muffin",
      "price": "190",
      "count": 2,
      "id": 3
      }, {
    "productDescription": [{
      "displayName": "Size",
      "displayValue": "12 Inch",
      "id": 12,
      "type": "ItemVariation",
      "value": ["7"]
      }, {
      "displayName": "Extras",
      "displayValue": "Premiuim Veg, Multigrain",
      "id": 3,
      "type": "Customization",
      "value": [{"7": 8}, {"9": 1}] // 8,1 are ids of option taken from ingredient
  }],
"count": 1,
"price": "200",
"id": 5,
"name": "Frosted Muffin"}]
},         
"outlet_id": 3
}
```

### HTTP REQUEST

`POST /api/v1/orders`


## Update an order
