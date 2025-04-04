<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mobile Shop</title>
    <style>
        /* CSS styles */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background: #f5f5f5;
        }

        header {
            background: #007bff;
            color: #fff;
            padding: 10px;
            text-align: center;
        }

        h1 {
            margin: 0;
        }

        .container {
            padding: 20px;
            display: flex;
            flex-wrap: wrap;
            justify-content: space-around;
        }

        .product-card {
            background: #fff;
            border: 1px solid #ccc;
            border-radius: 8px;
            padding: 15px;
            margin: 10px;
            width: 300px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            text-align: center;
        }

        .product-card img {
            max-width: 100%;
            height: auto;
            border-radius: 8px;
        }

        .product-card h2 {
            font-size: 20px;
            color: #333;
        }

        .product-card p {
            color: #666;
        }

        .product-card button {
            background: #28a745;
            color: #fff;
            padding: 10px 15px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }

        .product-card button:hover {
            background: #218838;
        }

        #payment-form {
            display: none;
            padding: 20px;
            background: #fff;
            border: 1px solid #ccc;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            max-width: 500px;
            margin: 20px auto;
        }

        #payment-form h2 {
            margin-top: 0;
        }

        .form-group {
            margin-bottom: 15px;
        }

        .form-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }

        .form-group input {
            width: 100%;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }

        footer {
            text-align: center;
            padding: 10px;
            background: #007bff;
            color: #fff;
            position: fixed;
            bottom: 0;
            width: 100%;
        }
    </style>
</head>
<body>

<header>
    <h1>Welcome to Mobile Shop</h1>
</header>

<div class="container" id="product-list">
    <!-- Mobile products will be added dynamically here -->
</div>

<div id="payment-form">
    <h2>Payment Details</h2>
    <p id="selected-product"></p>
    <form onsubmit="processPayment(event)">
        <div class="form-group">
            <label for="name">Full Name</label>
            <input type="text" id="name" required>
        </div>
        <div class="form-group">
            <label for="card-number">Card Number</label>
            <input type="text" id="card-number" placeholder="1234 5678 9123 4567" required>
        </div>
        <div class="form-group">
            <label for="expiry">Expiry Date</label>
            <input type="text" id="expiry" placeholder="MM/YY" required>
        </div>
        <div class="form-group">
            <label for="cvv">CVV</label>
            <input type="text" id="cvv" placeholder="123" required>
        </div>
        <button type="submit">Pay Now</button>
    </form>
</div>

<footer>
    &copy; 2025 Mobile Shop. All rights reserved.
</footer>

<script>
    // JavaScript to handle product listing and payment
    const products = [
        { name: "iPhone 15", price: "$999", image: "iphone.jpg" },
        { name: "Samsung Galaxy S24", price: "$899", image: "Samsung.jpeg" },
        { name: "Google Pixel 8", price: "$799", image: "pic.jpeg" },
        { name: "OnePlus 12", price: "$699", image: "one.jpg" },
    ];

    const productList = document.getElementById("product-list");
    const paymentForm = document.getElementById("payment-form");
    const selectedProduct = document.getElementById("selected-product");

    products.forEach(product => {
        const productCard = document.createElement("div");
        productCard.className = "product-card";
        productCard.innerHTML = `
            <img src="${product.image}" alt="${product.name}">
            <h2>${product.name}</h2>
            <p>Price: ${product.price}</p>
            <button onclick="buyNow('${product.name}', '${product.price}')">Buy Now</button>
        `;
        productList.appendChild(productCard);
    });

    function buyNow(name, price) {
        selectedProduct.innerText = `You are purchasing: ${name} for ${price}`;
        paymentForm.style.display = "block";
    }

    function processPayment(event) {
        event.preventDefault();
        const name = document.getElementById("name").value;
        alert(`Thank you, ${name}! Your payment has been processed.`);
        paymentForm.style.display = "none";
    }
</script>

</body>
</html>
