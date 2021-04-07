# BIGDATA-LAB
db.customer.insertMany([ {cust_id:"A123", amount:500, status:"A" },{ cust_id:"A123", amount:250, status:"A" }, { cust_id:"B212", amount:200, status:"A" }, { cust_id:"A123", amount:300, status:"D" } ] )

db.customer.mapReduce( function(){ emit(this.cust_id, this.amount); },
 function(key,value){
 return Array.sum(value)
 },
{ query:{status:"A"}, out:"order_details"})


This will not work ->

db.customer.mapReduce( function(){ emit(this.cust_id, this.amount); },
 function(key,value){
 return Array.max(value)
 },
{ query:{status:"A"}, out:"order_details"})
