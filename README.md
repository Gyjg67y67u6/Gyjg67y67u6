<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Boutique en ligne pour acheter des Agni Puffs de qualité">
    <title>Agni Puff Online</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #fff; /* Arrière-plan blanc */
            color: pink; /* Texte en rose */
        }

        header {
            background-color: #333;
            color: #fff;
            padding: 20px;
            text-align: center;
        }

        #site-title {
            animation: colorChange 3s infinite alternate;
        }

        @keyframes colorChange {
            from { color: pink; }
            to { color: #ff69b4; }
        }

        nav ul {
            list-style-type: none;
            margin: 0;
            padding: 0;
        }

        nav ul li {
            display: inline;
            margin: 0 10px;
        }

        nav ul li a {
            color: #fff;
            text-decoration: none;
        }

        #upload-button {
            position: fixed;
            top: 10px;
            right: 10px;
            background: transparent;
            border: none;
            color: transparent;
            padding: 1px; /* Très petit bouton */
            cursor: pointer;
        }

        section {
            padding: 20px;
        }

        .product-grid {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
        }

        .product-item {
            background-color: #fff;
            padding: 10px;
            border: 1px solid #ddd;
            width: calc(33% - 40px);
        }

        .product-item img {
            width: 100%;
            height: auto;
        }

        .product-item h3,
        .product-item p {
            color: pink; /* Texte en rose */
        }

        .product-item .price {
            color: red; /* Prix en rouge */
        }

        .comment-section {
            margin-top: 20px;
        }

        .comment-section form {
            display: flex;
            flex-direction: column;
        }

        .comment-section label, 
        .comment-section textarea,
        .comment-section input {
            margin-bottom: 10px;
        }

        .comment-list {
            margin-top: 20px;
        }

        .comment {
            border-bottom: 1px solid #ddd;
            padding: 10px 0;
        }

        footer {
            background-color: #333;
            color: #fff;
            text-align: center;
            padding: 10px;
            position: fixed;
            width: 100%;
            bottom: 0;
        }
    </style>
</head>
<body>
    <!-- En-tête du site avec animation 2D -->
    <header>
        <h1 id="site-title">Agni Puff Online</h1>
        <nav>
            <ul>
                <li><a href="#home">Accueil</a></li>
                <li><a href="#products">Produits</a></li>
                <li><a href="#contact">Contact</a></li>
                <li><a href="#cart">Panier</a></li>
            </ul>
        </nav>
    </header>

    <!-- Bouton discret pour poster des photos et prix des produits -->
    <button id="upload-button" title="Poster des photos et prix"></button>

    <!-- Section Accueil -->
    <section id="home">
        <h2>Bienvenue dans notre boutique</h2>
        <p>Découvrez nos délicieux Agni Puffs.</p>
    </section>

    <!-- Section Produits -->
    <section id="products">
        <h2>Nos Produits</h2>
        <div class="product-grid">
            <!-- Exemple de produit -->
            <div class="product-item">
                <img src="product1.jpg" alt="Produit 1">
                <h3>Produit 1</h3>
                <p class="price">Prix : 20 €</p>
                <button onclick="orderOnWhatsApp('Produit 1', 20)">Commander via WhatsApp</button>
            </div>
            <!-- Ajoutez plus de produits ici -->
        </div>
    </section>

    <!-- Section Contact -->
    <section id="contact">
        <h2>Contactez-nous</h2>
        <form>
            <label for="name">Nom:</label>
            <input type="text" id="name" name="name" required>
            <label for="email">Email:</label>
            <input type="email" id="email" name="email" required>
            <label for="message">Message:</label>
            <textarea id="message" name="message" required></textarea>
            <button type="submit">Envoyer</button>
        </form>
    </section>

    <!-- Section Panier -->
    <section id="cart">
        <h2>Votre Panier</h2>
        <div class="cart-items">
            <!-- Les articles du panier seront affichés ici -->
        </div>
        <button>Procéder au paiement</button>
    </section>

    <!-- Section Commentaires -->
    <section class="comment-section">
        <h2>Commentaires</h2>
        <form id="comment-form">
            <label for="comment-name">Nom:</label>
            <input type="text" id="comment-name" name="comment-name" required>
            <label for="comment-text">Commentaire:</label>
            <textarea id="comment-text" name="comment-text" required></textarea>
            <button type="submit">Poster un commentaire</button>
        </form>
        <div class="comment-list" id="comment-list">
            <!-- Commentaires affichés ici -->
        </div>
    </section>

    <!-- Pied de page -->
    <footer>
        <p>&copy; 2024 Agni Puff Online. Tous droits réservés.</p>
    </footer>

    <script>
        // Fonction pour ajouter des produits au panier
        document.querySelectorAll('.product-item button').forEach(button => {
            button.addEventListener('click', (event) => {
                const product = event.target.closest('.product-item');
                const productName = product.querySelector('h3').innerText;
                const productPrice = product.querySelector('.price').innerText;
                addToCart(productName, productPrice);
            });
        });

        function addToCart(name, price) {
            const cartItems = document.querySelector('.cart-items');
            const cartItem = document.createElement('div');
            cartItem.innerHTML = `<p>${name} - ${price}</p>`;
            cartItems.appendChild(cartItem);
        }

        // Fonction pour commander via WhatsApp
        function orderOnWhatsApp(productName, productPrice) {
            const phone = "225594540820";
            const message = encodeURIComponent(`Bonjour, je voudrais commander ${productName} au prix de ${productPrice}€.`);
            window.open(`https://wa.me/${phone}?text=${message}`, '_blank');
        }

        // Gestion des commentaires
        document.getElementById('comment-form').addEventListener('submit', function(event) {
            event.preventDefault();
            const name = document.getElementById('comment-name').value;
            const text = document.getElementById('comment-text').value;

            const commentList = document.getElementById('comment-list');
            const comment = document.createElement('div');
            comment.classList.add('comment');
            comment.innerHTML = `<strong>${name}</strong><p>${text}</p>`;
            commentList.appendChild(comment);

            // Réinitialiser le formulaire
            document.getElementById('comment-form').reset();
        });
    </script>
</body>
</html>
