<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Delevri App</title>
    <style>
        * { box-sizing: border-box; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; margin: 0; padding: 0; }
        body { background: #f4f6f9; color: #1e1e24; min-height: 100vh; padding-bottom: 60px; }
        
        /* Navbar */
        nav { background: #ffc244; padding: 15px 20px; display: flex; justify-content: space-between; align-items: center; position: sticky; top: 0; z-index: 100; box-shadow: 0 2px 10px rgba(0,0,0,0.1); }
        .logo { font-size: 24px; font-weight: 800; color: #00a082; display: flex; align-items: center; gap: 8px; cursor: pointer; text-transform: uppercase; }
        .cart-btn { background: #00a082; color: white; border: none; padding: 10px 20px; border-radius: 25px; font-weight: bold; cursor: pointer; display: flex; align-items: center; gap: 10px; transition: 0.2s; }
        .cart-btn:hover { background: #00856c; transform: scale(1.02); }

        /* Hero Header */
        header { background: #ffc244; text-align: center; padding: 50px 20px 80px 20px; border-bottom-left-radius: 40px; border-bottom-right-radius: 40px; }
        header h1 { font-size: 32px; font-weight: 800; margin-bottom: 20px; color: #1e1e24; }
        .search-container { background: white; max-width: 550px; margin: 0 auto; padding: 8px 15px; border-radius: 30px; display: flex; align-items: center; box-shadow: 0 4px 15px rgba(0,0,0,0.1); }
        .search-container input { border: none; width: 100%; padding: 10px; font-size: 16px; outline: none; }

        /* Main Container */
        .container { max-width: 1000px; margin: -40px auto 0 auto; padding: 0 20px; }

        /* Bubble Categories */
        .categories-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(160px, 1fr)); gap: 20px; margin-bottom: 40px; }
        .cat-card { background: white; padding: 20px; border-radius: 24px; text-align: center; box-shadow: 0 8px 20px rgba(0,0,0,0.05); cursor: pointer; transition: 0.3s; border: 2px solid transparent; }
        .cat-card:hover { transform: translateY(-5px); border-color: #ffc244; box-shadow: 0 12px 25px rgba(0,0,0,0.1); }
        .cat-icon { font-size: 50px; margin-bottom: 12px; }
        .cat-name { font-weight: 700; font-size: 16px; color: #1e1e24; }

        /* Store Section */
        .section-title { font-size: 22px; font-weight: 800; margin-bottom: 20px; display: flex; align-items: center; gap: 10px; }
        .products-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 20px; }
        .product-card { background: white; border-radius: 16px; padding: 20px; box-shadow: 0 4px 12px rgba(0,0,0,0.05); display: flex; justify-content: space-between; align-items: center; }
        .product-info h3 { font-size: 16px; font-weight: 700; margin-bottom: 5px; }
        .product-info p { font-size: 14px; color: #6c757d; margin-bottom: 8px; }
        .product-price { font-weight: 700; color: #00a082; font-size: 16px; }
        .add-btn { background: #ffc244; border: none; width: 36px; height: 36px; border-radius: 50%; font-size: 20px; font-weight: bold; cursor: pointer; display: flex; align-items: center; justify-content: center; transition: 0.2s; }
        .add-btn:hover { background: #e0aa34; transform: scale(1.1); }

        /* Cart Sidebar Drawer */
        .cart-drawer { position: fixed; right: -400px; top: 0; width: 100%; max-width: 400px; height: 100vh; background: white; z-index: 200; box-shadow: -5px 0 25px rgba(0,0,0,0.15); transition: 0.3s; padding: 30px 20px; display: flex; flex-direction: column; }
        .cart-drawer.open { right: 0; }
        .cart-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 30px; border-bottom: 1px solid #eee; padding-bottom: 15px; }
        .cart-header h2 { font-size: 20px; font-weight: 800; }
        .close-cart { background: none; border: none; font-size: 24px; cursor: pointer; color: #6c757d; }
        .cart-items { flex: 1; overflow-y: auto; }
        .cart-item { display: flex; justify-content: space-between; align-items: center; margin-bottom: 15px; padding-bottom: 15px; border-bottom: 1px solid #f8f9fa; }
        .cart-item-details h4 { font-size: 14px; font-weight: 700; }
        .cart-item-details p { font-size: 12px; color: #00a082; font-weight: bold; }
        .remove-btn { background: none; border: none; color: #dc3545; cursor: pointer; font-size: 14px; }
        .cart-footer { border-top: 1px solid #eee; padding-top: 20px; }
        .cart-total-row { display: flex; justify-content: space-between; font-size: 16px; margin-bottom: 10px; }
        .cart-total-row.final { font-size: 20px; font-weight: 800; color: #1e1e24; margin-top: 5px; }
        .checkout-btn { background: #00a082; color: white; width: 100%; border: none; padding: 15px; border-radius: 12px; font-size: 16px; font-weight: bold; cursor: pointer; margin-top: 15px; transition: 0.2s; text-align: center; }
        .checkout-btn:hover { background: #00856c; }
        .overlay { position: fixed; top: 0; left: 0; width: 100vw; height: 100vh; background: rgba(0,0,0,0.4); z-index: 150; display: none; }
        .overlay.open { display: block; }
    </style>
</head>
<body>

    <!-- Navigation -->
    <nav>
        <div class="logo" onclick="changeCategory('restaurants')">🚀 Delevri App</div>
        <button class="cart-btn" onclick="toggleCart(true)">
            🛒 Mon Panier (<span id="cart-count">0</span>)
        </button>
    </nav>

    <!-- Header / Recherche -->
    <header>
        <h1>Vos restaurants et courses livrés en un éclair ⚡</h1>
        <div class="search-container">
            <span>📍</span>
            <input type="text" placeholder="Quelle est votre adresse de livraison ?">
        </div>
    </header>

    <div class="container">
        <!-- Bubbles Magiques (Catégories) -->
        <div class="categories-grid">
            <div class="cat-card" onclick="changeCategory('restaurants')">
                <div class="cat-icon">🍔</div>
                <div class="cat-name">Restaurants</div>
            </div>
            <div class="cat-card" onclick="changeCategory('supermarche')">
                <div class="cat-icon">🛒</div>
                <div class="cat-name">Supermarché</div>
            </div>
            <div class="cat-card" onclick="changeCategory('pharmacie')">
                <div class="cat-icon">💊</div>
                <div class="cat-name">Pharmacie</div>
            </div>
            <div class="cat-card" onclick="changeCategory('coursier')">
                <div class="cat-icon">📦</div>
                <div class="cat-name">Coursier</div>
            </div>
        </div>

        <!-- Section Liste des articles -->
        <h2 class="section-title" id="current-category-title">🍔 Restaurants Partenaires</h2>
        <div class="products-grid" id="products-list">
            <!-- Rempli en JavaScript -->
        </div>
    </div>

    <!-- Le Panier latéral (Sidebar Drawer) -->
    <div class="overlay" id="cart-overlay" onclick="toggleCart(false)"></div>
    <div class="cart-drawer" id="cart-drawer">
        <div class="cart-header">
            <h2>Votre Commande</h2>
            <button class="close-cart" onclick="toggleCart(false)">✕</button>
        </div>
        <div class="cart-items" id="cart-items-container">
            <!-- Articles du panier -->
        </div>
        <div class="cart-footer">
            <div class="cart-total-row">
                <span>Sous-total</span>
                <span id="subtotal-price">0.00 €</span>
            </div>
            <div class="cart-total-row">
                <span>Frais de livraison</span>
                <span id="delivery-price">2.50 €</span>
            </div>
            <div class="cart-total-row final">
                <span>Total</span>
                <span id="total-price">0.00 €</span>
            </div>
            <button class="checkout-btn" onclick="commander()">Commander maintenant</button>
        </div>
    </div>

    <script>
        const catalog = {
            restaurants: {
                title: "🍔 Restaurants Partenaires",
                items: [
                    { id: "r1", name: "Le Burger Gourmet", desc: "Steak façon bouchère, cheddar fondu, frites maison", price: 12.50 },
                    { id: "r2", name: "Pizza Di Napoli", desc: "Sauce tomate San Marzano, mozzarella di bufala", price: 11.00 },
                    { id: "r3", name: "Sushi Master", desc: "Plateau assortiment de 16 California et Sashimis", price: 18.90 }
                ]
            },
            supermarche: {
                title: "🛒 Supermarché & Épicerie",
                items: [
                    { id: "s1", name: "Pack de Lait (x6)", desc: "Litres de lait demi-écrémé", price: 6.20 },
                    { id: "s2", name: "Café Arabica Moulu", desc: "Paquet premium de 250g", price: 4.50 },
                    { id: "s3", name: "Sac de Fruits Frais (2kg)", desc: "Mélange de pommes et bananes de saison", price: 5.00 }
                ]
            },
            pharmacie: {
                title: "💊 Parapharmacie & Soins",
                items: [
                    { id: "p1", name: "Gel Hydroalcoolique", desc: "Flacon familial de 500ml", price: 3.50 },
                    { id: "p2", name: "Boite de Pansements", desc: "Multi-tailles, ultra-résistants (x20)", price: 2.90 },
                    { id: "p3", name: "Crème Solaire 50+", desc: "Protection maximale, flacon de 200ml", price: 14.20 }
                ]
            },
            coursier: {
                title: "📦 Coursier Express",
                items: [
                    { id: "c1", name: "Envoi de documents urgents", desc: "Prise en charge et livraison en moins de 30 min", price: 7.00 },
                    { id: "c2", name: "Récupération de clés / colis", desc: "Le coursier va chercher votre objet à l'adresse", price: 9.50 }
                ]
            }
        };

        let cart = [];

        function changeCategory(catKey) {
            const data = catalog[catKey];
            document.getElementById('current-category-title').innerHTML = data.title;
            const container = document.getElementById('products-list');
            container.innerHTML = '';
            
            data.items.forEach(product => {
                const card = document.createElement('div');
                card.className = 'product-card';
                card.innerHTML = `
                    <div class="product-info">
                        <h3>${product.name}</h3>
                        <p>${product.desc}</p>
                        <div class="product-price">${product.price.toFixed(2)} €</div>
                    </div>
                    <button class="add-btn" onclick="addToCart('${product.name}', ${product.price})">+</button>
                `;
                container.appendChild(card);
            });
        }

        function addToCart(name, price) {
            cart.push({ name, price });
            updateCartUI();
            const btn = document.querySelector('.cart-btn');
            btn.style.transform = 'scale(1.1)';
            setTimeout(() => btn.style.transform = 'scale(1)', 200);
        }

        function removeFromCart(index) {
            cart.splice(index, 1);
            updateCartUI();
        }

        function updateCartUI() {
            document.getElementById('cart-count').innerText = cart.length;
            const container = document.getElementById('cart-items-container');
            container.innerHTML = '';
            let subtotal = 0;
            
            cart.forEach((item, index) => {
                subtotal += item.price;
                const div = document.createElement('div');
                div.className = 'cart-item';
                div.innerHTML = `
                    <div class="cart-item-details">
                        <h4>${item.name}</h4>
                        <p>${item.price.toFixed(2)} €</p>
                    </div>
                    <button class="remove-btn" onclick="removeFromCart(${index})">Supprimer</button>
                `;
                container.appendChild(div);
            });

            const deliveryFee = cart.length > 0 ? 2.50 : 0.00;
            const total = subtotal + deliveryFee;

            document.getElementById('subtotal-price').innerText = `${subtotal.toFixed(2)} €`;
            document.getElementById('delivery-price').innerText = `${deliveryFee.toFixed(2)} €`;
            document.getElementById('total-price').innerText = `${total.toFixed(2)} €`;
        }

        function toggleCart(show) {
            if(show) {
                document.getElementById('cart-drawer').classList.add('open');
                document.getElementById('cart-overlay').classList.add('open');
            } else {
                document.getElementById('cart-drawer').classList.remove('open');
                document.getElementById('cart-overlay').classList.remove('open');
            }
        }

        function commander() {
            if(cart.length === 0) {
                alert("Votre panier est vide ! Ajoutez des articles avant de commander.");
                return;
            }
            alert("🎉 Commande validée avec succès ! Un livreur connecté en scooter récupère votre colis.");
            cart = [];
            updateCartUI();
            toggleCart(false);
        }

        window.onload = function() {
            changeCategory('restaurants');
        };
    </script>
</body>
</html>
