<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Boutique Jeune Style</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background-color: #fafafa;
    }
    header {
      background-color: #111;
      color: white;
      padding: 20px;
      text-align: center;
    }
    .container {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 20px;
      padding: 30px;
    }
    .product {
      background-color: white;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
      padding: 20px;
      text-align: center;
    }
    .product img {
      width: 100%;
      max-height: 200px;
      object-fit: cover;
      border-radius: 10px;
    }
    .price {
      font-weight: bold;
      margin: 10px 0;
    }
    .buy-button {
      background-color: #28a745;
      color: white;
      padding: 10px 15px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    .buy-button:hover {
      background-color: #218838;
    }
    #panier {
      background-color: #fff;
      padding: 20px;
      margin: 0 30px 30px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    #whatsapp-btn {
      background-color: #25D366;
      color: white;
      padding: 12px 20px;
      font-size: 16px;
      text-decoration: none;
      border-radius: 5px;
      display: inline-block;
      margin-top: 15px;
    }
  </style>
</head>
<body>

<header>
  <h1>Boutique Jeune Style</h1>
  <p>Vêtements tendance pour les jeunes</p>
</header>

<div class="container">
  <div class="product">
    <img src="https://via.placeholder.com/250x200?text=T-shirt+Stylé" alt="Produit 1">
    <h3>T-shirt Stylé</h3>
    <div class="price">5000 FCFA</div>
    <button class="buy-button" onclick="ajouterAuPanier('T-shirt Stylé', 5000)">Ajouter au panier</button>
  </div>
  <div class="product">
    <img src="https://via.placeholder.com/250x200?text=Jean+Slim" alt="Produit 2">
    <h3>Jean Slim</h3>
    <div class="price">10000 FCFA</div>
    <button class="buy-button" onclick="ajouterAuPanier('Jean Slim', 10000)">Ajouter au panier</button>
  </div>
  <div class="product">
    <img src="https://via.placeholder.com/250x200?text=Casquette+Mode" alt="Produit 3">
    <h3>Casquette Mode</h3>
    <div class="price">3000 FCFA</div>
    <button class="buy-button" onclick="ajouterAuPanier('Casquette Mode', 3000)">Ajouter au panier</button>
  </div>
</div>

<div id="panier">
  <h2>🛒 Mon Panier</h2>
  <ul id="liste-panier"></ul>
  <p><strong>Total :</strong> <span id="total">0</span> FCFA</p>
  <a id="whatsapp-btn" href="#" target="_blank">Commander via WhatsApp</a>
</div>

<script>
  let panier = [];
  let total = 0;

  function ajouterAuPanier(nom, prix) {
    panier.push({ nom, prix });
    total += prix;
    afficherPanier();
  }

  function afficherPanier() {
    const liste = document.getElementById('liste-panier');
    liste.innerHTML = '';
    panier.forEach(item => {
      const li = document.createElement('li');
      li.textContent = `${item.nom} - ${item.prix} FCFA`;
      liste.appendChild(li);
    });
    document.getElementById('total').textContent = total;

    // Génère le message WhatsApp
    let message = "Bonjour, je souhaite commander :%0A";
    panier.forEach(item => {
      message += `- ${item.nom} : ${item.prix} FCFA%0A`;
    });
    message += `Total : ${total} FCFA`;
    
    // Remplace le numéro par ton numéro WhatsApp !
    const numeroWhatsApp = "237698970199";
    document.getElementById('whatsapp-btn').href = `https://wa.me/${numeroWhatsApp}?text=${message}`;
  }
</script>

</body>
</html>
