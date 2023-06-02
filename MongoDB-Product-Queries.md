**1. Find all the information about each products**
```sh

db.Products.find()

```

**2. Find the product price which are between 400 to 800**
```sh

db.Products.find({product_price:{"$gte":400,"$lte":800}})

```

**3. Find the product price which are not between 400 to 600**
```sh

db.Products.find({product_price:{"$not":{"$gte":400,"$lte":800}}})

```

**4. List the four product which are grater than 500 in price**
```sh

db.Products.find({product_price:{"$gte":500}})

```

**5. Find the product name and product material of each products**
```sh

db.Product_name:1, product_material:1})

```

**6. Find the product with a row id of 10**
```sh

db.Products.find({"id":"10"})

```

**7. Find only the product name and product material**
```sh

db.Products.find({}, { Product_name: 1, product_material: 1}) 

```

**8. Find all products which contain the value of soft in product material**
```sh

db.Products.find({product_material:'Soft'})

```

**9. Find products which contain product color indigo  and product price 492.00**

    **To find the product_color "indigo"**
```sh

db.Products.find({ product_color: "indigo" })

```

   **To find the product_price "492.00"**
```sh

db.Products.find({product_price: 492.00 })

```

**10. Delete the products which product price value are same**
```sh

db.Products.aggregate([{ $group: { _id: "$product_price", count: { $count: {} } } },{ $match: { _id: { $ne: null }, count: { $gt: 1 } } }]);

```

    After that the result is [36,47] so we delete them from database using below command

```sh

db.Products.deleteMany({ product_price: { $in: [36, 47] } });

```