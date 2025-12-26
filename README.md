# Ventor.-Jewellery-
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Ventor Jewelry Shop</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body {
    margin: 0;
    font-family: Arial, sans-serif;
    background: #f4f4f4;
}

header {
    background: #111;
    color: gold;
    padding: 20px;
    text-align: center;
}

.logo {
    font-size: 32px;
    font-weight: bold;
    letter-spacing: 2px;
}

nav {
    background: #222;
    display: flex;
    justify-content: center;
    gap: 20px;
    padding: 10px;
}

nav button {
    background: none;
    border: none;
    color: white;
    font-size: 16px;
    cursor: pointer;
}

nav button:hover {
    color: gold;
}

section {
    display: none;
    padding: 30px;
}

.active {
    display: block;
}

.products {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 20px;
}

.product {
    background: white;
    padding: 15px;
    border-radius: 10px;
    text-align: center;
}

.product img {
    width: 100%;
    height: 180px;
    object-fit: cover;
    border-radius: 10px;
}

button.action {
    background: gold;
    border: none;
    padding: 10px;
    font-weight: bold;
    border-radius: 5px;
    cursor: pointer;
}

input {
    width: 100%;
    padding: 10px;
    margin: 8px 0;
}

.cart {
    background: white;
    padding: 20px;
    border-radius: 10px;
}

footer {
    background: #111;
    color: white;
    text-align: center;
    padding: 15px;
}
</style>
</head>

<body>

<header>
    <div class="logo">VENTOR ✦ JEWELRY</div>
    <p>Luxury That Shines</p>
</header>

<nav>
    <button onclick="showSection('shop')">Shop</button>
    <button onclick="showSection('cart')">Cart</button>
    <button onclick="showSection('checkout')">Checkout</button>
    <button onclick="showSection('login')">Login</button>
    <button onclick="showSection('admin')">Admin</button>
</nav>

<!-- SHOP -->
<section id="shop" class="active">
<h2>Shop Jewelry</h2>
<div class="products" id="productList">
    <div class="product">
        <img src="https://images.unsplash.com/photo-1600185365483-26d7a4cc7519">
        <h3>Gold Ring</h3>
        <p>$120</p>
        <button class="action" onclick="addToCart('Gold Ring',120)">Add to Cart</button>
    </div>
</div>
</section>

<!-- CART -->
<section id="cart">
<h2>Your Cart</h2>
<div class="cart">
<ul id="cartItems"></ul>
<h3>Total: $<span id="total">0</span></h3>
</div>
</section>

<!-- CHECKOUT -->
<section id="checkout">
<h2>Checkout</h2>
<input placeholder="Full Name">
<input placeholder="Address">
<input placeholder="Card Number">
<button class="action" onclick="alert('Order Placed Successfully!')">Place Order</button>
</section>

<!-- LOGIN -->
<section id="login">
<h2>Login / Signup</h2>
<input placeholder="Email">
<input type="password" placeholder="Password">
<button class="action" onclick="alert('Logged in (Demo)')">Login</button>
</section>

<!-- ADMIN -->
<section id="admin">
<h2>Admin Panel</h2>
<input id="pname" placeholder="Product Name">
<input id="pprice" placeholder="Price">
<input id="pimg" placeholder="Image URL">
<button class="action" onclick="addProduct()">Add Product</button>
</section>

<footer>
<p>© 2025 Ventor Jewelry Shop</p>
</footer>

<script>
let total = 0;

function showSection(id) {
    document.querySelectorAll("section").forEach(s => s.classList.remove("active"));
    document.getElementById(id).classList.add("active");
}

function addToCart(name, price) {
    let li = document.createElement("li");
    li.textContent = name + " - $" + price;
    document.getElementById("cartItems").appendChild(li);
    total += price;
    document.getElementById("total").textContent = total;
}

function addProduct() {
    let name = document.getElementById("pname").value;
    let price = document.getElementById("pprice").value;
    let img = document.getElementById("pimg").value;

    let div = document.createElement("div");
    div.className = "product";
    div.innerHTML = `
        <img src="${img}">
        <h3>${name}</h3>
        <p>$${price}</p>
        <button class="action" onclick="addToCart('${name}',${price})">Add to Cart</button>
    `;
    document.getElementById("productList").appendChild(div);
    alert("Product Added!");
}
</script>

</body>
</html>

