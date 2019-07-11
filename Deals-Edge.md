### Products

Get and update product records

#### GET
`/products/`  
`/products/{UUID}`   

Return all or single product records

##### Parameters:
`filter` can be provided with search data following the [JSON filter spec](https://github.com/eliebmobile/crm_pro-wiki/blob/master/Dynamic-Model-Filtering.md).


#### POST
`/products/`  
`/products/{UUID}`  
Create or Update a product record.  


### Deals

Get and update deal and product records

#### GET
`/deals/`  
`/deals/{UUID}`   

Return all or single deal records  

##### Parameters:
`filter` can be provided with search data following the [JSON filter spec](https://github.com/eliebmobile/crm_pro-wiki/blob/master/Dynamic-Model-Filtering.md).


#### POST
`/deals/`  
`/deals/{UUID}`  
Create or Update a deal record.  

 

### Add Deal Products

Products can be added and removed from deals using the following edges:

#### POST
`/deals/{DEAL_UUID}/products/add/{PRODUCT_UUID}/`

##### Parameters
`amount`: *Decimal* The total value of this line item. Defaults to the Product's sale price if not provided.
`quantity`: The quantity of the product in this deal. Defaults to 1
`note`: Any special notes regarding this line item


### Edit Deal Products

Edit the individual product line item details with this edge

#### POST
`/deals/{DEAL_UUID}/products/update/{DEAL_PRODUCT_ID}/`

##### Parameters
`amount`: *Decimal* The total value of this line item. Defaults to the Product's sale price if not provided.
`quantity`: The quantity of the product in this deal. Defaults to 1
`note`: Any special notes regarding this line item

### Remove Deal Products

Remove a product line item or an entire occurrence of a product from a deal

#### POST
`/deals/{DEAL_UUID}/products/remove/`

##### Parameters
Note that either `product_id` or `deal_product_id` are required. 
`product_id`: The product to remove. If this parameter is sent all occurrences of this product will be removed from the deal  
`deal_product_id`: The line item id to remove. If provided only this line item will be removed.

## Get Deal Documents

To return all the documents relating to a deal, use this edge:  

`/deals/{DEAL_UUID}/documents`

