# BIGDATA-LAB
db.customer.aggregate([ { $match: {status:"A"} }, {$group: { _id:"cust_id" , total: {$sum:"$amount"} } } ])
{ "_id" : "B212", "total" : 200 }
{ "_id" : "A123", "total" : 750 }



 db.customer.aggregate([
    { $match: { status: "A" } },
    { $group: { _id: "$cust_id", total: { $sum: "$amount" } } }
 ])
{ "_id" : "B212", "total" : 200 }
{ "_id" : "A123", "total" : 750 }




db.customer.aggregate( { $match: {status: "A"} })
{ "_id" : ObjectId("606beb16663c1514aac09ea5"), "cust_id" : "A123", "amount" : 500, "status" : "A" }
{ "_id" : ObjectId("606beb16663c1514aac09ea6"), "cust_id" : "A123", "amount" : 250, "status" : "A" }
{ "_id" : ObjectId("606beb16663c1514aac09ea7"), "cust_id" : "B212", "amount" : 200, "status" : "A" }




 db.customer.aggregate([
   { $group: { _id:"$cust_id", "max_value": {$max:"$amount"} } }
 ])

{ "_id" : "B212", "max_value" : 200 }
{ "_id" : "A123", "max_value" : 500 }



db.customer.aggregate([
 { $project: {cust_id:1,status:1} }
])
{ "_id" : ObjectId("606beb16663c1514aac09ea5"), "cust_id" : "A123", "status" : "A" }
{ "_id" : ObjectId("606beb16663c1514aac09ea6"), "cust_id" : "A123", "status" : "A" }
{ "_id" : ObjectId("606beb16663c1514aac09ea7"), "cust_id" : "B212", "status" : "A" }
{ "_id" : ObjectId("606beb16663c1514aac09ea8"), "cust_id" : "A123", "status" : "D" }



db.customer.aggregate({$limit:3})
{ "_id" : ObjectId("606beb16663c1514aac09ea5"), "cust_id" : "A123", "amount" : 500, "status" : "A" }
{ "_id" : ObjectId("606beb16663c1514aac09ea6"), "cust_id" : "A123", "amount" : 250, "status" : "A" }
{ "_id" : ObjectId("606beb16663c1514aac09ea7"), "cust_id" : "B212", "amount" : 200, "status" : "A" }



 db.customer.aggregate([
  { $project: {cust_id:1,status:1,_id:0} }
 ])
{ "cust_id" : "A123", "status" : "A" }
{ "cust_id" : "A123", "status" : "A" }
{ "cust_id" : "B212", "status" : "A" }
{ "cust_id" : "A123", "status" : "D" }



> db.customer.aggregate([
...  { $match: {status:"A"}}, { $group: {_id:"$cust_id", "total_sum" :{ $sum:"$amount" } } }
... ])

{ "_id" : "B212", "total_sum" : 200 }
{ "_id" : "A123", "total_sum" : 750 }


