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
