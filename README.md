<!DOCTYPE html>
<html lang="si">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>BE NAROTO | Products</title>
<style>
body { font-family:Poppins,sans-serif; background:#f9f9f9; margin:0; padding:0; text-align:center; }
header { background:linear-gradient(90deg,#ff3333,#ff9900); color:white; padding:25px; }
header h1 { margin:0; }
.products { display:grid; grid-template-columns:repeat(auto-fit,minmax(250px,1fr)); gap:20px; padding:20px; }
.card { background:white; border-radius:12px; box-shadow:0 4px 12px rgba(0,0,0,0.1); overflow:hidden; transition:0.3s; }
.card:hover { transform:translateY(-5px); }
.card img { width:100%; height:180px; object-fit:cover; }
.card h3 { color:#ff3333; margin:10px 0 5px; }
.price { color:#ff9900; font-weight:bold; margin-bottom:10px; }
.btn { background:linear-gradient(90deg,#ff3333,#ff9900); color:white; border:none; padding:10px 25px; border-radius:25px; cursor:pointer; margin-bottom:15px; display:inline-block; text-decoration:none; }
.btn:hover { transform:scale(1.05); }
footer { background:#222; color:white; padding:15px 0; margin-top:40px; font-size:0.9em; }
</style>
</head>
<body>

<header>
<h1>BE NAROTO</h1>
<p>Delivering Quality — Only in Sri Lanka 🇱🇰</p>
</header>

<section class="products">
<div class="card">
<img src="product1.jpg" alt="Product 1">
<h3>Product 01</h3>
<p class="price">Rs. 2500</p>
<a href="payment.html?product=Product+01&price=2500" class="btn">Buy Now</a>
</div>

<div class="card">
<img src="product2.jpg" alt="Product 2">
<h3>Product 02</h3>
<p class="price">Rs. 1800</p>
<a href="payment.html?product=Product+02&price=1800" class="btn">Buy Now</a>
</div>

<div class="card">
<img src="product3.jpg" alt="Product 3">
<h3>Product 03</h3>
<p class="price">Rs. 3200</p>
<a href="payment.html?product=Product+03&price=3200" class="btn">Buy Now</a>
</div>
</section>

<footer>
<p>© 2025 BE NAROTO — All Rights Reserved | Only in Sri Lanka 🇱🇰</p>
</footer>

</body>
</html>
<!DOCTYPE html>
<html lang="si">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>BE NAROTO | Payment</title>
<style>
:root {
  --primary:#ff3333;
  --secondary:#ff9900;
  --bg-light:#f9f9f9;
  --bg-dark:#121212;
  --text-light:#222;
  --text-dark:#eee;
}
body { font-family:Poppins,sans-serif; margin:0; padding:0; background:var(--bg-light); color:var(--text-light); transition:0.4s; text-align:center; }
header { background:linear-gradient(90deg,var(--primary),var(--secondary)); color:white; padding:20px; }
header h1 { margin:0; }
form, .crypto { background:white; max-width:400px; margin:20px auto; padding:25px; border-radius:12px; box-shadow:0 4px 12px rgba(0,0,0,0.1); text-align:center; transition:0.4s; }
body.dark form, body.dark .crypto { background:#222; color:var(--text-dark); }
input { width:90%; padding:10px; margin:8px 0; border-radius:8px; border:1px solid #ccc; font-size:1em; }
.btn { background:linear-gradient(90deg,var(--primary),var(--secondary)); color:white; border:none; padding:10px 25px; border-radius:25px; cursor:pointer; margin-top:10px; }
.btn:hover { transform:scale(1.05); }
#notification { display:none; background:#4BB543; color:white; padding:15px 20px; border-radius:12px; position:fixed; top:20px; right:20px; z-index:9999; transition:0.3s; }
.crypto-address { font-weight:bold; margin:10px 0; word-break:break-all; }
.copy-btn { background:#ff9900; color:white; border:none; padding:6px 12px; border-radius:8px; cursor:pointer; margin-bottom:10px; }
.copy-btn:hover { background:#ff3333; }
.toggle-mode { position:fixed; bottom:20px; right:20px; background:var(--primary); color:white; border:none; padding:10px 14px; border-radius:50%; cursor:pointer; font-size:1.2em; box-shadow:0 4px 10px rgba(0,0,0,0.3); }
.toggle-mode:hover { transform:scale(1.1); }
footer { text-align:center; padding:15px 0; margin-top:30px; font-size:0.9em; }
@media(max-width:500px){
  input{width:95%;}
  form, .crypto{padding:20px;}
}
</style>
</head>
<body>

<header>
<h1>BE NAROTO Payment</h1>
</header>

<div id="notification">ඔබේ Order එක සාර්ථකයි! ✅</div>

<h3 id="productName">Product Name</h3>
<p id="productPrice">Rs. XXXX</p>

<!-- Card Payment Form -->
<form id="paymentForm">
<input type="text" placeholder="Card Number" required>
<input type="text" placeholder="Expiry MM/YY" required>
<input type="text" placeholder="CVV" required>
<input type="text" placeholder="Name on Card" required>
<button type="submit" class="btn">Pay Now</button>
</form>

<!-- Crypto Payment Section -->
<div class="crypto">
<h3>💰 Crypto Payment</h3>
<p>Send to our wallet:</p>
<p class="crypto-address" id="walletAddress">0x123456789ABCDEF123456789ABCDEF123456789A</p>
<button class="copy-btn" onclick="copyWallet()">Copy Address</button>
<p>After sending, click Pay Now</p>
<button class="btn" onclick="cryptoPay()">Pay Now</button>
</div>

<button class="toggle-mode" onclick="toggleDark()">🌙</button>

<footer>
<p>© 2025 BE NAROTO — Only in Sri Lanka 🇱🇰</p>
</footer>

<script>
// Get product info from URL
const urlParams = new URLSearchParams(window.location.search);
const product = urlParams.get('product');
const price = urlParams.get('price');
document.getElementById('productName').innerText = product;
document.getElementById('productPrice').innerText = 'Rs. ' + price;

// Card Payment submit
document.getElementById('paymentForm').addEventListener('submit', function(e){
    e.preventDefault();
    showNotification();
});

// Crypto copy
function copyWallet(){
    const wallet = document.getElementById('walletAddress').innerText;
    navigator.clipboard.writeText(wallet);
    alert("Wallet address copied! ✅");
}

// Crypto pay
function cryptoPay(){ showNotification(); }

// Notification
function showNotification(){
    const notification = document.getElementById('notification');
    notification.style.display='block';
    setTimeout(()=>{notification.style.display='none';},3000);
}

// Dark Mode Toggle
function toggleDark(){
    document.body.classList.toggle('dark');
}
</script>

</body>
</html>
