# E-Commerce-web-application-
# project
ecommerce-app
│
├── index.html
├── products.html
├── cart.html
├── checkout.html
├── login.html
├── register.html
├── style.css
├── app.js
└── images

# FILE 1: index.html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>E-Commerce Store</title>

<link rel="stylesheet" href="style.css">
</head>


<body>

<header>

<h1>Braj E-Commerce Store</h1>

<nav>
<a href="index.html">Home</a>
<a href="products.html">Products</a>
<a href="cart.html">Cart</a>
<a href="login.html">Login</a>
</nav>

</header>

<section class="hero">

<h2>Welcome to Our Store</h2>

<p>Best Products at Affordable Prices</p>

<a href="products.html">
<button>Shop Now</button>
</a>

</section>

<footer>

<p>© 2026 Braj E-Commerce Store</p>

</footer>

</body>
</html>

# FILE 2: style.css
body{
font-family:Arial;
margin:0;
padding:0;
}

header{
background:#007bff;
color:white;
padding:15px;
text-align:center;
}

nav a{
color:white;
text-decoration:none;
margin:10px;
}

.hero{
text-align:center;
padding:100px;
}

button{
background:#007bff;
color:white;
border:none;
padding:10px 20px;
cursor:pointer;
}

footer{
background:#222;
color:white;
text-align:center;
padding:10px;
position:fixed;
bottom:0;
width:100%;
}

# FILE 3: products.html
<!DOCTYPE html>
<html>

<head>
<title>Products</title>
<link rel="stylesheet" href="style.css">
</head>

<body>

<header>

<h1>Products</h1>

<a href="cart.html">Cart</a>

</header>

<div class="product">

<h2>Laptop</h2>

<p>₹50,000</p>

<button onclick="addToCart('Laptop',50000)">
Add to Cart
</button>

</div>

<div class="product">

<h2>Mobile</h2>

<p>₹20,000</p>

<button onclick="addToCart('Mobile',20000)">
Add to Cart
</button>

</div>

<script src="app.js"></script>

</body>
</html>

# FILE 4: app.js
function addToCart(name, price){

let cart = JSON.parse(localStorage.getItem("cart")) || [];

cart.push({
name:name,
price:price
});

localStorage.setItem(
"cart",
JSON.stringify(cart)
);

alert("Added To Cart");

}

# FILE 5: cart.html
<!DOCTYPE html>
<html>

<head>
    <title>Shopping Cart</title>
    <link rel="stylesheet" href="style.css">
</head>

<body>

<header>
    <h1>Your Cart</h1>
    <a href="products.html">Continue Shopping</a>
</header>

<div id="cart-items"></div>

<h2 id="total"></h2>

<a href="checkout.html">
    <button>Proceed To Checkout</button>
</a>

<script>

let cart = JSON.parse(localStorage.getItem("cart")) || [];

let cartDiv = document.getElementById("cart-items");

let total = 0;

cart.forEach(item => {

    total += item.price;

    cartDiv.innerHTML += `
        <div>
            <h3>${item.name}</h3>
            <p>₹${item.price}</p>
        </div>
        <hr>
    `;
});

document.getElementById("total").innerText =
"Total: ₹" + total;

</script>

</body>
</html>

# FILE 6: checkout.html
<!DOCTYPE html>
<html>

<head>
    <title>Checkout</title>
    <link rel="stylesheet" href="style.css">
</head>

<body>

<header>
    <h1>Checkout</h1>
</header>

<form id="checkoutForm">

<input type="text"
placeholder="Full Name"
required>

<br><br>

<input type="text"
placeholder="Address"
required>

<br><br>

<input type="text"
placeholder="Phone Number"
required>

<br><br>

<button type="submit">
Place Order
</button>

</form>

<script>

document.getElementById("checkoutForm")
.addEventListener("submit", function(e){

e.preventDefault();

alert("Order Placed Successfully!");

localStorage.removeItem("cart");

window.location.href="index.html";

});

</script>

</body>
</html>

# FILE 7: login.html
<!DOCTYPE html>
<html>

<head>
<title>Login</title>

<link rel="stylesheet"
href="style.css">

</head>

<body>

<header>
<h1>User Login</h1>
</header>

<form>

<input type="email"
placeholder="Email"
required>

<br><br>

<input type="password"
placeholder="Password"
required>

<br><br>

<button>
Login
</button>

</form>

</body>
</html>

# FILE 8: register.html
<!DOCTYPE html>
<html>

<head>

<title>Register</title>

<link rel="stylesheet"
href="style.css">

</head>

<body>

<header>
<h1>Create Account</h1>
</header>

<form>

<input type="text"
placeholder="Full Name"
required>

<br><br>

<input type="email"
placeholder="Email"
required>

<br><br>

<input type="password"
placeholder="Password"
required>

<br><br>

<button>
Register
</button>

</form>

</body>
</html>

# FILE 9: admin.html
<!DOCTYPE html>
<html>

<head>
<title>Admin Dashboard</title>
<link rel="stylesheet" href="style.css">
</head>

<body>

<header>
<h1>Admin Dashboard</h1>
</header>

<h2>Add Product</h2>

<form id="productForm">

<input type="text"
id="name"
placeholder="Product Name"
required>

<br><br>

<input type="number"
id="price"
placeholder="Price"
required>

<br><br>

<button type="submit">
Add Product
</button>

</form>

<h2>Product List</h2>

<div id="productList"></div>

<script>

let products =
JSON.parse(localStorage.getItem("products")) || [];

function showProducts(){

let list =
document.getElementById("productList");

list.innerHTML="";

products.forEach((product,index)=>{

list.innerHTML += `
<div>
<h3>${product.name}</h3>
<p>₹${product.price}</p>
<button onclick="deleteProduct(${index})">
Delete
</button>
</div>
<hr>
`;

});

}

function deleteProduct(index){

products.splice(index,1);

localStorage.setItem(
"products",
JSON.stringify(products)
);

showProducts();

}

document.getElementById("productForm")
.addEventListener("submit",function(e){

e.preventDefault();

let name =
document.getElementById("name").value;

let price =
document.getElementById("price").value;

products.push({
name,
price
});

localStorage.setItem(
"products",
JSON.stringify(products)
);

showProducts();

});

showProducts();

</script>

</body>
</html>

# FILE 10: package.json
{
  "name": "ecommerce-app",
  "version": "1.0.0",
  "description": "E-Commerce Application",
  "main": "server.js",
  "scripts": {
    "start": "node server.js"
  },
  "dependencies": {
    "express": "^4.18.2",
    "mongoose": "^8.0.0",
    "cors": "^2.8.5",
    "bcryptjs": "^2.4.3",
    "jsonwebtoken": "^9.0.2"
  }
}

# FILE 11: server.js
const express = require("express");
const cors = require("cors");

const app = express();

app.use(cors());
app.use(express.json());

app.get("/", (req,res)=>{
res.send("E-Commerce API Running");
});

app.listen(5000,()=>{
console.log("Server Running On Port 5000");
});

# FILE 12: config/db.js
config
└── db.js
# Create db.js
const mongoose = require("mongoose");

const connectDB = async()=>{

try{

await mongoose.connect(
"mongodb://127.0.0.1:27017/ecommerce"
);

console.log("MongoDB Connected");

}catch(error){

console.log(error);

}

};

module.exports = connectDB;

# FILE 13: models/Product.js
const mongoose = require("mongoose");

const ProductSchema =
new mongoose.Schema({

name:{
type:String,
required:true
},

price:{
type:Number,
required:true
},

description:{
type:String
},

image:{
type:String
}

});

module.exports =
mongoose.model(
"Product",
ProductSchema
);

# FILE 14: models/User.js
const mongoose = require("mongoose");

const UserSchema =
new mongoose.Schema({

name:String,

email:String,

password:String,

role:{
type:String,
default:"user"
}

});

module.exports =
mongoose.model(
"User",
UserSchema
);

# FILE 15: models/Order.js
const mongoose = require("mongoose");

const OrderSchema =
new mongoose.Schema({

userId:String,

products:Array,

total:Number,

status:{
type:String,
default:"Pending"
}

});

module.exports =
mongoose.model(
"Order",
OrderSchema
);

# FILE 16: routes/products.js
routes
└── products.js

const express = require("express");
const router = express.Router();

const Product = require("../models/Product");

router.get("/", async(req,res)=>{

const products =
await Product.find();

res.json(products);

});

router.post("/", async(req,res)=>{

const product =
new Product(req.body);

await product.save();

res.json(product);

});

router.delete("/:id", async(req,res)=>{

await Product.findByIdAndDelete(
req.params.id
);

res.json({
message:"Product Deleted"
});

});

module.exports = router;

# FILE 17: routes/users.js
const express = require("express");
const router = express.Router();

const User = require("../models/User");

router.post("/register", async(req,res)=>{

const user =
new User(req.body);

await user.save();

res.json({
message:"User Registered"
});

});

router.post("/login", async(req,res)=>{

const {email,password} =
req.body;

const user =
await User.findOne({
email,
password
});

if(user){

res.json({
message:"Login Successful"
});

}else{

res.status(401).json({
message:"Invalid Credentials"
});

}

});

module.exports = router;

# FILE 18: routes/orders.js
const express = require("express");
const router = express.Router();

const Order = require("../models/Order");

router.get("/", async(req,res)=>{

const orders =
await Order.find();

res.json(orders);

});

router.post("/", async(req,res)=>{

const order =
new Order(req.body);

await order.save();

res.json(order);

});

module.exports = router;

# UPDATE FILE 11: server.js
const express = require("express");
const cors = require("cors");

const connectDB =
require("./config/db");

const productRoutes =
require("./routes/products");

const userRoutes =
require("./routes/users");

const orderRoutes =
require("./routes/orders");

const app = express();

connectDB();

app.use(cors());
app.use(express.json());

app.use(
"/api/products",
productRoutes
);

app.use(
"/api/users",
userRoutes
);

app.use(
"/api/orders",
orderRoutes
);

app.get("/",(req,res)=>{

res.send(
"E-Commerce Backend Running"
);

});

app.listen(5000,()=>{

console.log(
"Server Running On Port 5000"
);

});

# FILE 19: README.md
# E-Commerce Web Application

## Features

- User Registration
- User Login
- Product Management
- Shopping Cart
- Checkout
- Order Tracking
- Admin Dashboard
- MongoDB Database

## Technologies

- HTML
- CSS
- JavaScript
- Node.js
- Express.js
- MongoDB

## Installation

npm install

npm start

Server runs on:

http://localhost:5000

## Author

Braj Kishor Das
