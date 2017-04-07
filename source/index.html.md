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

## SIGN IN

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

## Switch user via pin
> Request Format

```json
  {"user": 
      {"uname": "SL", "pin": "1235"}
   }
```

### HTTP REQUEST
`POST /api/v1/users/verify_pin`

## Get all roles
> Request Format

```json
 Not Required
```
### HTTP Request
`GET /api/v1/users/roles?outlet_id=3`

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

# Outlets

## Get All outlets for a organization
> Request Format

```json
NOT REQUIRED
```
### HTTP REQUEST
`GET api/v1/outlets?organization_id=1`

## Create an outlet
> Request Format

```json
    {"outlet": 
      {
         "name": "MCD", 
         "address": "Sec 29",  
         "typ": "outlet"  // typ can be multi or outlet
      }
    }
```

### HTTP REQUEST
`POST api/v1/outlets`

## Update an outlet
> Request Format

```json
    {"outlet": 
      {
         "name": "MCD", 
         "address": "Sec 29",  
         "typ": "outlet"  // typ can be multi or outlet
      }
    }
```

### HTTP REQUEST
`PUT api/v1/outlets/:id`

## Delete an outlet
> Request Format

```json
    Not required
```

### HTTP REQUEST
`Delete api/v1/outlets/:id`


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
      "value": [{"7": 8}, {"9": 1}] // 8,1 are ids of option taken from ingredient`
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

> Request Format

```json
 same as create
```

### HTTP REQUEST
`PUT /api/v1/orders/:id`



# Item Variation

## Get All item_variations for an item
> Request Format

```json
NOT REQUIRED
```

### HTTP REQUEST
`GET /api/v1/items/:item_id/item_variations`

## Create an item variation
> Request Format

```json
  {"item_variation": {
          "name": "size",
          "min": 0,
          "max": 1,
          "default": "small",
          "options_attributes": [
            {"name": "small", "price": 20},
            {"name": "medium", "price": 30},
            {"name": "lrg", "price": 70}
          ]
      }
  }
```

### HTTP REQUEST
`POST /api/v1/items/:item_id/item_variations`

## delete an item variation
> Request Format

```json
NOT REQUIRED
```

### HTTP REQUEST
`DELETE /api/v1/items/:item_id/item_variation/:id`

# Customizations

## GET customizations for an item
```json
NOT REQUIRED
```

### HTTP REQUEST
`GET /api/v1/items/:item_id/customizations`

## Create an customization
> Request Format

```json
{ "customization": {
          "name": "Toppings",
          "free": false,
          "min": 3,
          "max": 4,
          "ingredients_attributes": [
              {
                  "name": "mushroom",
                  "options": {"3": 45, "4": 56}
              },       {
                  "name": "onion",
                  "options": {"3": 65, "4": 79}
              }
          ]
  }
}
```

### HTTP REQUEST
`POST /api/v1/items/:item_id/customizations`

## Update an customizations
> Request Format

```json
      { "customization": {
          "name": "qwe",
          "free": true,
          "min": 3,
          "max": 4,
          "ingredients_attributes": [
              {
                  "id": "73",
                  "name": "eew",
                  "options": {"73": 458, "74": 56}
              },       {
                  "id": "74",
                  "name": "543wwe",
                  "options": {"73": 65, "74": 79}
              }
          ]
      }
      }
```

### HTTP REQUEST
`PUT /api/v1/items/:item_id/customizations/:id`

## Delete an customization
> Request Format

```json
Not Required
```

### HTTP REQUEST
`DELETE /api/v1/items/:item_id/customizations/:id`






