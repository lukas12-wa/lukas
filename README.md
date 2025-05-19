<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>TokoOnlineKu</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background-color: #f5f5f5;
    }
    header {
      background-color: #4CAF50;
      color: white;
      padding: 1em;
      text-align: center;
    }
    nav {
      background-color: #333;
      display: flex;
      justify-content: center;
      padding: 0.5em;
    }
    nav a {
      color: white;
      padding: 0.5em 1em;
      text-decoration: none;
    }
    nav a:hover {
      background-color: #555;
    }
    .container {
      display: flex;
      flex-wrap: wrap;
      padding: 20px;
      justify-content: center;
    }
    .product {
      background: white;
      border: 1px solid #ccc;
      border-radius: 8px;
      padding: 16px;
      margin: 10px;
      width: 200px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }
    .product img {
      width: 100%;
      height: auto;
      border-radius: 4px;
    }
    .product h3 {
      margin: 0.5em 0 0.2em;
    }
    .product p {
      color: #333;
    }
    .btn {
      background-color: #4CAF50;
      color: white;
      padding: 8px;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      width: 100%;
    }
    .btn:hover {
      background-color: #45a049;
    }
    .login-container {
      max-width: 300px;
      margin: 30px auto;
      background: white;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }
    .login-container h2 {
      text-align: center;
    }
    .login-container input {
      width: 100%;
      padding: 8px;
      margin: 10px 0;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
    .cart {
      max-width: 500px;
      margin: 30px auto;
      background: white;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }
    .cart h2 {
      text-align: center;
    }
    .cart ul {
      list-style: none;
      padding: 0;
    }
    .cart li {
      display: flex;
      justify-content: space-between;
      padding: 10px 0;
      border-bottom: 1px solid #eee;
    }
  </style>
</head>
<body>
  <header>
    <h1>Selamat Datang di TokoOnlineKu</h1>
  </header>

  <nav>
    <a href="#">Beranda</a>
    <a href="#keranjang">Keranjang</a>
    <a href="#login">Login</a>
  </nav>

  <div class="container" id="beranda">
    <div class="product">
      <img src="https://via.placeholder.com/200" alt="Produk 1">
      <h3>Produk 1</h3>
      <p>Rp100.000</p>
      <button class="btn" onclick="tambahKeKeranjang('Produk 1', 100000)">Beli</button>
    </div>
    <div class="product">
      <img src="https://via.placeholder.com/200" alt="Produk 2">
      <h3>Produk 2</h3>
      <p>Rp150.000</p>
      <button class="btn" onclick="tambahKeKeranjang('Produk 2', 150000)">Beli</button>
    </div>
  </div>

  <div class="cart" id="keranjang">
    <h2>Keranjang Belanja</h2>
    <ul id="daftar-keranjang">
      <!-- Item akan ditambahkan dengan JavaScript -->
    </ul>
    <p><strong>Total: Rp<span id="total">0</span></strong></p>
  </div>

  <div class="login-container" id="login">
    <h2>Login</h2>
    <input type="text" placeholder="Username">
    <input type="password" placeholder="Password">
    <button class="btn">Masuk</button>
  </div>

  <script>
    let keranjang = [];

    function tambahKeKeranjang(nama, harga) {
      keranjang.push({ nama, harga });
      renderKeranjang();
    }

    function renderKeranjang() {
      const daftar = document.getElementById('daftar-keranjang');
      const totalEl = document.getElementById('total');
      daftar.innerHTML = '';
      let total = 0;

      keranjang.forEach(item => {
        const li = document.createElement('li');
        li.innerHTML = `<span>${item.nama}</span><span>Rp${item.harga.toLocaleString()}</span>`;
        daftar.appendChild(li);
        total += item.harga;
      });

      totalEl.textContent = total.toLocaleString();
    }
  </script>
</body>
</html>
