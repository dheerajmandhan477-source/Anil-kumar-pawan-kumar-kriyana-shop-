<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Anil Kumar Pawan Kumar Kiryana Shop - Grocery Trading</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            overflow-x: hidden;
        }

        /* Header */
        header {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 1rem 0;
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            display: flex;
            align-items: center;
        }

        .logo span {
            background: #ff6b6b;
            padding: 0.3rem 0.8rem;
            border-radius: 50px;
            margin-right: 0.5rem;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav-links a {
            color: white;
            text-decoration: none;
            transition: opacity 0.3s;
        }

        .nav-links a:hover {
            opacity: 0.8;
        }

        .cart-icon {
            position: relative;
            font-size: 1.5rem;
            cursor: pointer;
        }

        .cart-count {
            position: absolute;
            top: -8px;
            right: -8px;
            background: #ff6b6b;
            color: white;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            font-size: 0.8rem;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)), url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 600"><rect fill="%23f8f9fa" width="1200" height="600"/><circle fill="%23e9ecef" cx="200" cy="150" r="80"/><circle fill="%23dee2e6" cx="800" cy="200" r="100"/><rect fill="%23ced4da" x="900" y="300" width="150" height="120"/><path fill="%23adb5bd" d="M100 400 Q200 350 300 400 Q400 450 500 400"/></svg>');
            background-size: cover;
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            color: white;
            margin-top: 80px;
        }

        .hero-content h1 {
            font-size: 3.5rem;
            margin-bottom: 1rem;
            animation: fadeInUp 1s ease;
        }

        .hero-content p {
            font-size: 1.3rem;
            margin-bottom: 2rem;
            animation: fadeInUp 1s ease 0.2s both;
        }

        .cta-button {
            display: inline-block;
            background: #ff6b6b;
            color: white;
            padding: 1rem 2rem;
            border-radius: 50px;
            text-decoration: none;
            font-weight: bold;
            transition: all 0.3s;
            animation: fadeInUp 1s ease 0.4s both;
        }

        .cta-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(255,107,107,0.4);
        }

        /* Sections */
        section {
            padding: 5rem 0;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
        }

        h2 {
            text-align: center;
            font-size: 2.5rem;
            margin-bottom: 3rem;
            color: #333;
        }

        /* Products Grid */
        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .product-card {
            background: white;
            border-radius: 20px;
            padding: 2rem;
            text-align: center;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
        }

        .product-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0,0,0,0.15);
        }

        .product-image {
            width: 120px;
            height: 120px;
            background: linear-gradient(45deg, #ff9a9e, #fecfef);
            border-radius: 50%;
            margin: 0 auto 1rem;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
        }

        .product-card h3 {
            font-size: 1.4rem;
            margin-bottom: 0.5rem;
            color: #333;
        }

        .price {
            font-size: 1.8rem;
            font-weight: bold;
            color: #ff6b6b;
            margin-bottom: 1rem;
        }

        .add-to-cart {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            border: none;
            padding: 0.8rem 2rem;
            border-radius: 25px;
            cursor: pointer;
            font-size: 1rem;
            transition: all 0.3s;
            width: 100%;
        }

        .add-to-cart:hover {
            transform: scale(1.05);
        }

        /* Cart Modal */
        .cart-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.8);
            display: none;
            align-items: center;
            justify-content: center;
            z-index: 2000;
        }

        .cart-content {
            background: white;
            padding: 2rem;
            border-radius: 20px;
            max-width: 500px;
            width: 90%;
            max-height: 80vh;
            overflow-y: auto;
        }

        .cart-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 0;
            border-bottom: 1px solid #eee;
        }

        .remove-item {
            background: #ff6b6b;
            color: white;
            border: none;
            padding: 0.3rem 0.8rem;
            border-radius: 50%;
            cursor: pointer;
        }

        .total {
            font-size: 1.5rem;
            font-weight: bold;
            text-align: center;
            margin-top: 1rem;
            color: #333;
        }

        /* Stats */
        .stats {
            background: #f8f9fa;
            text-align: center;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .stat-item {
            padding: 2rem;
        }

        .stat-number {
            font-size: 3rem;
            font-weight: bold;
            color: #667eea;
        }

        /* Footer */
        footer {
            background: #333;
            color: white;
            text-align: center;
            padding: 3rem 0;
        }

        /* Animations */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Responsive */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }

            .hero-content h1 {
                font-size: 2.5rem;
            }

            .products-grid {
                grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
                gap: 1.5rem;
            }
        }

        /* Scroll animations */
        .fade-in {
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.6s ease;
        }

        .fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <nav>
            <div class="logo">
                <span>🛒</span>
                Anil Kumar Pawan Kumar Kiryana Shop
            </div>
            <ul class="nav-links">
                <li><a href="#home">Home</a></li>
                <li><a href="#products">Products</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
            <div class="cart-icon" onclick="toggleCart()">
                🛒
                <span class="cart-count" id="cartCount">0</span>
            </div>
        </nav>
    </header>

    <!-- Hero Section -->
    <section id="home" class="hero">
        <div class="hero-content">
            <h1>Fresh Groceries Delivered</h1>
            <p>Quality products at best prices. Shop now from Anil Kumar Pawan Kumar Kiryana Shop!</p>
            <a href="#products" class="cta-button">Shop Now</a>
        </div>
    </section>

    <!-- Stats Section -->
    <section class="stats" id="about">
        <div class="container">
            <h2>Why Choose Us?</h2>
            <div class="stats-grid">
                <div class="stat-item fade-in">
                    <div class="stat-number">500+</div>
                    <div>Products Available</div>
                </div>
                <div class="stat-item fade-in">
                    <div class="stat-number">24/7</div>
                    <div>Customer Support</div>
                </div>
                <div class="stat-item fade-in">
                    <div class="stat-number">100%</div>
                    <div>Fresh Guarantee</div>
                </div>
                <div class="stat-item fade-in">
                    <div class="stat-number">5★</div>
                    <div>Customer Rating</div>
                </div>
            </div>
        </div>
    </section>

    <!-- Products Section -->
    <section id="products">
        <div class="container">
            <h2>Our Popular Products</h2>
            <div class="products-grid">
                <div class="product-card fade-in">
                    <div class="product-image">🥛</div>
                    <h3>Amul Milk</h3>
                    <div class="price">₹45</div>
                    <button class="add-to-cart" onclick="addToCart('Amul Milk', 45)">Add to Cart</button>
                </div>
                <div class="product-card fade-in">
                    <div class="product-image">🍚</div>
                    <h3>Basmati Rice (1kg)</h3>
                    <div class="price">₹85</div>
                    <button class="add-to-cart" onclick="addToCart('Basmati Rice (1kg)', 85)">Add to Cart</button>
                </div>
                <div class="product-card fade-in">
                    <div class="product-image">🥦</div>
                    <h3>Fresh Cauliflower</h3>
                    <div class="price">₹35</div>
                    <button class="add-to-cart" onclick="addToCart('Fresh Cauliflower', 35)">Add to Cart</button>
                </div>
                <div class="product-card fade-in">
                    <div class="product-image">🍎</div>
                    <h3>Red Apples (1kg)</h3>
                    <div class="price">₹120</div>
                    <button class="add-to-cart" onclick="addToCart('Red Apples (1kg)', 120)">Add to Cart</button>
                </div>
                <div class="product-card fade-in">
                    <div class="product-image">🥛</div>
                    <h3>Curd (500ml)</h3>
                    <div class="price">₹28</div>
                    <button class="add-to-cart" onclick="addToCart('Curd (500ml)', 28)">Add to Cart</button>
                </div>
                <div class="product-card fade-in">
                    <div class="product-image">🥭</div>
                    <h3>Fresh Mangoes (1kg)</h3>
                    <div class="price">₹180</div>
                    <button class="add-to-cart" onclick="addToCart('Fresh Mangoes (1kg)', 180)">Add to Cart</button>
                </div>
            </div>
        </div>
    </section>

    <!-- Cart Modal -->
    <div class="cart-modal" id="cartModal">
        <div class="cart-content">
            <h2>🛒 Shopping Cart</h2>
            <div id="cartItems"></div>
            <div class="total" id="cartTotal">Total: ₹0</div>
            <div style="text-align: center; margin-top: 1rem;">
                <button onclick="toggleCart()" style="background: #667eea; color: white; border: none; padding: 1rem 2rem; border-radius: 25px; cursor: pointer; font-size: 1rem;">Continue Shopping</button>
                <button onclick="checkout()" style="background: #28a745; color: white; border: none; padding: 1rem 2rem; border-radius: 25px; cursor: pointer; font-size: 1rem; margin-left: 1rem;">Checkout</button>
            </div>
        </div>
    </div>

    <!-- Footer -->
    <footer id="contact">
        <div class="container">
            <h2>Contact Us</h2>
            <p>📍 Local Market Area, Your City<br>
            📞 +91 98765 43210<br>
            ✉️ anilkumarshop@gmail.com</p>
            <p style="margin-top: 2rem;">© 2024 Anil Kumar Pawan Kumar Kiryana Shop. All rights reserved.</p>
        </div>
    </footer>

    <script>
        // Cart functionality
        let cart = [];

        function addToCart(name, price) {
            cart.push({ name, price });
            updateCartCount();
            showNotification(`${name} added to cart!`);
        }

        function removeFromCart(index) {
            cart.splice(index, 1);
            updateCartDisplay();
            updateCartCount();
        }

        function updateCartCount() {
            const count = cart.length;
            document.getElementById('cartCount').textContent = count;
        }

        function updateCartDisplay() {
            const cartItems = document.getElementById('cartItems');
            const total = cart.reduce((sum, item) => sum + item.price, 0);
            
            if (cart.length === 0) {
                cartItems.innerHTML = '<p style="text-align: center; color: #666;">Your cart is empty</p>';
                document.getElementById('cartTotal').textContent = 'Total: ₹0';
            } else {
                cartItems.innerHTML = cart.map((item, index) => `
                    <div class="cart-item">
                        <span>${item.name} - ₹${item.price}</span>
                        <button class="remove-item" onclick="removeFromCart(${index})">×</button>
                    </div>
                `).join('');
                document.getElementById('cartTotal').textContent = `Total: ₹${total}`;
            }
        }

        function toggleCart() {
            const modal = document.getElementById('cartModal');
            modal.style.display = modal.style.display === 'flex' ? 'none' : 'flex';
            if (modal.style.display === 'flex') {
                updateCartDisplay();
            }
        }

        function checkout() {
            if (cart.length === 0) {
                alert('Your cart is empty!');
                return;
            }
            alert('Thank you for your order! Order placed successfully. 🚀');
            cart = [];
            updateCartCount();
            toggleCart();
        }

        function showNotification(message) {
            const notification = document.createElement('div');
            notification.style.cssText = `
                position: fixed;
                top: 100px;
                right: 20px;
                background: #28a745;
                color: white;
                padding: 1rem 2rem;
                border-radius: 10px;
                z-index: 3000;
                animation: slideIn 0.3s ease;
            `;
            notification.textContent = message;
            document.body.appendChild(notification);
            
            setTimeout(() => {
                notification.remove();
            }, 3000);
        }

        // Scroll animations
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, observerOptions);

        document.querySelectorAll('.fade-in').
