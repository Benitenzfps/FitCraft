<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FitCraft- Fitness Shop</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: url('fondo-fitness.jpg') no-repeat center center fixed;
            background-size: cover;
            margin: 0;
            color: #333;
            transition: all 0.3s ease-in-out;
        }
        .header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px 20px;
            background: rgba(255, 255, 255, 0.9);
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }
        .logo {
            font-size: 24px;
            font-weight: bold;
            color: #007BFF;
        }
        .nav {
            list-style: none;
            display: flex;
            gap: 20px;
        }
        .nav li {
            display: inline;
        }
        .nav a {
            text-decoration: none;
            color: #333;
            padding: 10px 15px;
            border-radius: 5px;
            transition: background-color 0.3s, color 0.3s;
        }
        .nav a:hover {
            background-color: #007BFF;
            color: #fff;
        }
        .user-options a {
            text-decoration: none;
            color: #007BFF;
            margin-left: 10px;
            transition: color 0.3s;
            cursor: pointer;
        }
        .user-options a:hover {
            color: #0056b3;
        }
        .filters {
            display: flex;
            flex-direction: column;
            padding: 20px;
            background: rgba(255, 255, 255, 0.8);
            margin: 20px;
            border-radius: 10px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            max-width: 300px;
        }
        .products {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            padding: 20px;
            justify-content: center;
        }
        .product {
            border: 1px solid #ddd;
            padding: 10px;
            width: 200px;
            border-radius: 10px;
            background: rgba(255, 255, 255, 0.9);
            transition: transform 0.3s, box-shadow 0.3s;
        }
        .product:hover {
            transform: translateY(-10px);
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2);
        }
        .product img {
            width: 100%;
            height: auto;
            border-radius: 10px;
        }
        .price {
            color: red;
            font-weight: bold;
        }
        .old-price {
            text-decoration: line-through;
            color: #777;
        }
        .hidden {
            display: none;
        }
        #price-range {
            width: 100%;
        }
        #price-range-display {
            text-align: center;
            margin-top: 10px;
            font-weight: bold;
        }
        .filters h2, .filters h3 {
            margin: 10px 0;
            color: #007BFF;
        }
        /* Modal Styles */
        .modal {
            display: none;
            position: fixed;
            z-index: 1;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            overflow: auto;
            background-color: rgb(0,0,0);
            background-color: rgba(0,0,0,0.4);
            padding-top: 60px;
            transition: opacity 0.3s ease;
        }
        .modal-content {
            background-color: #fefefe;
            margin: 5% auto;
            padding: 20px;
            border: 1px solid #888;
            width: 80%;
            max-width: 400px;
            border-radius: 10px;
        }
        .close {
            color: #aaa;
            float: right;
            font-size: 28px;
            font-weight: bold;
        }
        .close:hover,
        .close:focus {
            color: black;
            text-decoration: none;
            cursor: pointer;
        }
        .modal-header {
            font-size: 24px;
            font-weight: bold;
            color: #007BFF;
            text-align: center;
            margin-bottom: 20px;
        }
        .modal-input {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        .modal-button {
            background-color: #007BFF;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            width: 100%;
            margin: 10px 0;
        }
        .modal-button:hover {
            background-color: #0056b3;
        }
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
        }
        header {
            background-color: #333;
            color: #fff;
            text-align: center;
            padding: 1em 0;
        }
        h1 {
            margin: 0;
            font-size: 2em;
        }
        .filter {
            background-color: #fff;
            padding: 1em;
            margin: 1em;
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        .filter h3 {
            margin-top: 0;
            font-size: 1.5em;
            animation: fadeIn 1s;
        }
        .filter ul {
            list-style: none;
            padding: 0;
        }
        .filter li {
            margin-bottom: 0.5em;
            font-size: 1.2em;
            animation: slideIn 0.5s ease-out;
        }
        .products {
            display: flex;
            flex-wrap: wrap;
            gap: 1em;
            padding: 1em;
        }
        .product {
            background-color: #fff;
            border: 1px solid #ddd;
            border-radius: 5px;
            overflow: hidden;
            width: calc(33% - 2em);
            margin: 1em;
            transition: transform 0.3s;
            animation: fadeIn 1s;
        }
        .product img {
            width: 100%;
            display: block;
        }
        .product h3 {
            margin: 0.5em;
            font-size: 1.2em;
            animation: slideIn 0.5s ease-out;
        }
        .product .price {
            margin: 0.5em;
            font-size: 1.1em;
            color: #333;
        }
        .product:hover {
            transform: scale(1.05);
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        @keyframes slideIn {
            from { transform: translateY(-20px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
        /* Nuevos estilos para el modal del carrito de compras */
        .modal {
            display: none;
            position: fixed;
            z-index: 1;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            overflow: auto;
            background-color: rgb(0,0,0);
            background-color: rgba(0,0,0,0.4);
            padding-top: 60px;
            transition: opacity 0.3s ease;
        }
        .modal-content {
            background-color: #fefefe;
            margin: 5% auto;
            padding: 20px;
            border: 1px solid #888;
            width: 80%;
            max-width: 400px;
            border-radius: 10px;
        }
        .close {
            color: #aaa;
            float: right;
            font-size: 28px;
            font-weight: bold;
        }
        .close:hover,
        .close:focus {
            color: black;
            text-decoration: none;
            cursor: pointer;
        }
        .modal-header {
            font-size: 24px;
            font-weight: bold;
            color: #007BFF;
            text-align: center;
            margin-bottom: 20px;
        }
        .modal-input {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        .modal-button {
            background-color: #007BFF;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            width: 100%;
            margin: 10px 0;
        }
        .modal-button:hover {
            background-color: #0056b3;
        }
        .cart-item {
            display: flex;
            justify-content: space-between;
            margin-bottom: 10px;
        }
        .cart-item-name {
            font-weight: bold;
        }
        .cart-item-quantity {
            margin-left: 10px;
        }
        #cartSubtotal, #cartTotal {
            font-weight: bold;
            margin-top: 10px;
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% {
                transform: translateY(0);
            }
            40% {
                transform: translateY(-30px);
            }
            60% {
                transform: translateY(-15px);
            }
        }

        @keyframes pulse {
            0% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.05);
            }
            100% {
                transform: scale(1);
            }
        }

        .product {
            animation: bounce 2s infinite, pulse 5s infinite;
        }

</style>
    
</head>
<body>

    <div class="header">
        <div class="logo">FitCraft- Fitness Shop</div>
        <ul class="nav">
            <li><a href="#" onclick="filterCategory('Accesorios')">Accesorios</a></li>
            <li><a href="#" onclick="filterCategory('Equipo')">Equipo de gimnasio</a></li>
            <li><a href="#" onclick="filterCategory('Ropa')">Ropa de entrenamiento</a></li>
            <li><a href="#" onclick="filterCategory('Suplementos')">Suplementos</a></li>
            <li><a href="#" onclick="filterCategory('Electrónica')">Electrónica para fitness</a></li>
        </ul>
        <div class="user-options">
            <a id="loginBtn">Iniciar Sesión</a> |
            <a id="signupBtn">Crear Cuenta</a>  |
            <a id="cartBtn">Carrito de Compras</a>
        </div>
    </div>
    <div class="filters">
        <h2>Filtros</h2>
        <div class="filter">
            <h3>Categoría</h3>
            <ul>
                <li><input type="checkbox" id="category1" value="Accesorios" onchange="filterCheckboxes()"> <label for="category1">Accesorios</label></li>
                <li><input type="checkbox" id="category2" value="Equipo" onchange="filterCheckboxes()"> <label for="category2">Equipo de gimnasio</label></li>
                <li><input type="checkbox" id="category3" value="Ropa" onchange="filterCheckboxes()"> <label for="category3">Ropa de entrenamiento</label></li>
                <li><input type="checkbox" id="category4" value="Suplementos" onchange="filterCheckboxes()"> <label for="category4">Suplementos</label></li>
                <li><input type="checkbox" id="category5" value="Electrónica" onchange="filterCheckboxes()"> <label for="category5">Electrónica para fitness</label></li>
            </ul>
        </div>

        <div class="filter">
            <h3>Rango de Precio</h3>
            <input type="range" id="price-range" min="0" max="500" step="10" oninput="updatePriceRange()">
            <div id="price-range-display">$0 - $500</div>
        </div>
    </div>
    <div class="products">
        <!-- Categoría: Accesorios -->
        <div class="product" data-category="Accesorios" data-price="20">
            <img src="banda-acondicionamiento.jpg" alt="Banda de acondicionamiento físico">
            <h3>Banda de Acondicionamiento</h3>
            <p class="price">$20.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Banda de Acondicionamiento', 20)">Agregar al Carrito</button>
        </div>
        <div class="product" data-category="Accesorios" data-price="15">
            <img src="guantes.jpg" alt="Guantes de entrenamiento">
            <h3>Guantes de Entrenamiento</h3>
            <p class="price">$15.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Guantes Everlast', 20)">Agregar al Carrito</button>
        </div>
        <div class="product" data-category="Accesorios" data-price="40">
            <img src="cinturon.jpg" alt="Cinturón para levantamiento de pesas">
            <h3>Cinturón para levantamiento de pesas</h3>
            <p class="price">$40.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Cinturón para levantamiento de pesas', 20)">Agregar al Carrito</button>
        </div>
        <div class="product" data-category="Accesorio" data-price="50">
            <img src="faja.webp" alt="Faja de ejercicio">
            <h3>Faja de ejercicio</h3>
            <p class="price">$50.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Faja de ejercicio', 20)">Agregar al Carrito</button>
        </div>
        <div class="product" data-category="Accesorios" data-price="12">
            <img src="cuerda-saltar.jpg" alt="Cuerda de saltar">
            <h3>Cuerda de saltar</h3>
            <p class="price">$12.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Cuerda de saltar', 20)">Agregar al Carrito</button>
        </div>
        <div class="product" data-category="Accesorios" data-price="15">
            <img src="codera.webp" alt="Codera">
            <h3>Codera</h3>
            <p class="price">$15.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Codera', 20)">Agregar al Carrito</button>
        </div>
        <div class="product" data-category="Accesorios" data-price="18">
            <img src="empuñadora.jpg" alt="Empuñadura">
            <h3>Empuñadura</h3>
            <p class="price">$18.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Empuñadura', 20)">Agregar al Carrito</button>
        </div>

        <!-- Categoría: Equipo -->
        <div class="product" data-category="Equipo" data-price="45">
            <img src="espaldera.jpg" alt="Espaldera">
            <h3>Espaldera</h3>
            <p class="price">$45.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Espaldera', 20)">Agregar al Carrito</button>
        </div>
        <div class="product" data-category="Equipo" data-price="300">
            <img src="maquina_remo.jpg" alt="Máquina de Remo">
            <h3>Máquina de Remo</h3>
            <p class="price">$300.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Máquina de Remo', 20)">Agregar al Carrito</button>
        </div>
        <div class="product" data-category="Equipo" data-price="150">
            <img src="pesas.jpg" alt="Juego de Pesas">
            <h3>Juego de Pesas</h3>
            <p class="price">$150.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Juego de Pesas', 20)">Agregar al Carrito</button>
        </div>
        <div class="product" data-category="Equipo" data-price="100">
            <img src="escalera-agilidad.webp" alt="Escalera de agilidad">
            <h3>Escalera de agilidad</h3>
            <p class="price">$100.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Escalera de agilidad', 20)">Agregar al Carrito</button>
        </div>
        <div class="product" data-category="Equipo" data-price="80">
            <img src="escalon.jpg" alt="Escalón para ejercicios">
            <h3>Escalón para ejercicios</h3>
            <p class="price">$80.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Escalón para ejercicios', 20)">Agregar al Carrito</button>
        </div>
        <div class="product" data-category="Equipo" data-price="30">
            <img src="esterilla.jpg" alt="Esterilla de gym">
            <h3>Esterilla de gym</h3>
            <p class="price">$30.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Esterilla de gym', 20)">Agregar al Carrito</button>
        </div>
        <div class="product" data-category="Equipo" data-price="30">
            <img src="bicicleta-eliptica.jpg" alt="Esterilla de gym">
            <h3>Bicicleta eliptica</h3>
            <p class="price">$260.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Bicicleta eliptica', 20)">Agregar al Carrito</button>
        </div>

        <!-- Categoría: Ropa -->
        <div class="product" data-category="Ropa" data-price="30">
            <img src="camiseta.jpg" alt="Camiseta de entrenamiento">
            <h3>Camiseta de Entrenamiento</h3>
            <p class="price">$30.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Camiseta de Entrenamiento', 20)">Agregar al Carrito</button>
        </div>
        <div class="product" data-category="Ropa" data-price="25">
            <img src="pantalones.jpg" alt="Pantalones de entrenamiento">
            <h3>Pantalones de Entrenamiento</h3>
            <p class="price">$25.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Pantalones de Entrenamiento', 20)">Agregar al Carrito</button>
        </div>
        <div class="product" data-category="Ropa" data-price="100">
            <img src="zapatillas.jpg" alt="Zapatillas deportivas">
            <h3>Zapatillas everlast</h3>
            <p class="price">$80.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Zapatillas everlast', 20)">Agregar al Carrito</button>
        </div>
        <div class="product" data-category="Ropa" data-price="100">
            <img src="zapatillas-nike.png" alt="Zapatillas deportivas">
            <h3>Zapatillas nike</h3>
            <p class="price">$150.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Zapatillas nike', 20)">Agregar al Carrito</button>
        </div>
        <div class="product" data-category="Ropa" data-price="100">
            <img src="zapatillas-puma.jpg" alt="Zapatillas deportivas">
            <h3>Zapatillas puma</h3>
            <p class="price">$100.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Zapatillas puma', 20)">Agregar al Carrito</button>
        </div>
        <div class="product" data-category="Ropa" data-price="100">
            <img src="zapatillas-adidas.jpg" alt="Zapatillas deportivas">
            <h3>Zapatillas adidas</h3>
            <p class="price">$110.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Zapatillas adidas', 20)">Agregar al Carrito</button>
        </div>
        <div class="product" data-category="Ropa" data-price="100">
            <img src="zapatillas-travis.jpg" alt="Zapatillas deportivas">
            <h3>Air Jordan 1 High "Travis Scott" </h3>
            <p class="price">$300.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Air Jordan 1 High Travis Scott, 20')">Agregar al Carrito</button>
        </div>
        <div class="product" data-category="Ropa" data-price="25">
            <img src="guantes-adidas.avif" alt="Guantes para gym adidas">
            <h3>Guantes para gym adidas</h3>
            <p class="price">$25.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Guantes para gym adidas', 20)">Agregar al Carrito</button>
        </div>
        <div class="product" data-category="Ropa" data-price="20">
            <img src="guantes-nike.jpg" alt="Guantes de gym nike">
            <h3>Guantes para gym nike</h3>
            <p class="price">$20.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Guantes para gym nike', 20)">Agregar al Carrito</button>
        </div>
        <div class="product" data-category="Ropa" data-price="22">
            <img src="guantes-reebok.webp" alt="Guantes de gym reebok">
            <h3>Guantes para gym reebok</h3>
            <p class="price">$22.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Guantes para gym reebok', 20)">Agregar al Carrito</button>
        </div>

        <!-- Categoría: Suplementos -->
        <div class="product" data-category="Suplementos" data-price="40">
            <img src="proteina.jpg" alt="Proteína en polvo">
            <h3>Proteína en Polvo</h3>
            <p class="price">$40.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Proteína en Polvo', 20)">Agregar al Carrito</button>
        </div>
        <div class="product" data-category="Suplementos" data-price="30">
            <img src="vitaminas.webp" alt="Vitaminas">
            <h3>Vitaminas</h3>
            <p class="price">$30.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Vitaminas', 20)">Agregar al Carrito</button>
        </div>
        <div class="product" data-category="Suplementos" data-price="25">
            <img src="suplemento.webp" alt="Suplemento de aminoácidos">
            <h3>Suplemento de aminoácidos</h3>
            <p class="price">$25.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Suplemento de aminoácidos', 20)">Agregar al Carrito</button>
        </div>

        <!-- Categoría: Electrónica -->
        <div class="product" data-category="Electrónica" data-price="80">
            <img src="reloj-inteligente.webp" alt="Monitor de Fitness">
            <h3>Cubitt CT4</h3>
            <p class="price">$90.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Cubitt CT4', 20)">Agregar al Carrito</button>
        </div>
        <div class="product" data-category="Electrónica" data-price="200">
            <img src="Sony-WH-XB910N-1024x576-1.webp" alt="Auriculares Bluetooth">
            <h3>Auriculares Bluetooth</h3>
            <p class="price">$200.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Auriculares Bluetooth', 20)">Agregar al Carrito</button>
        </div>
        
        <div class="product" data-category="Electrónica" data-price="60">
            <img src="monitor-frecuencia.jpg" alt="Monitor de frecuencia cardíaca">
            <h3>Monitor de frecuencia cardíaca</h3>
            <p class="price">$60.00</p>
            <input type="number" value="1" min="1" class="quantity">
            <button class="add-to-cart" onclick="addToCart('Monitor de frecuencia cardíaca', 20)">Agregar al Carrito</button>
        </div>
    </div>

    <!-- Modal de inicio de sesión -->
    <div id="loginModal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeModal('loginModal')">&times;</span>
            <div class="modal-header">Iniciar Sesión</div>
            <input type="text" class="modal-input" placeholder="Correo electrónico">
            <input type="password" class="modal-input" placeholder="Contraseña">
            <button class="modal-button">Iniciar Sesión</button>
        </div>
    </div>

    <!-- Modal de registro -->
    <div id="signupModal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="closeModal('signupModal')">&times;</span>
            <div class="modal-header">Crear Cuenta</div>
            <input type="text" class="modal-input" placeholder="Nombre completo">
            <input type="text" class="modal-input" placeholder="Correo electrónico">
            <input type="password" class="modal-input" placeholder="Contraseña">
            <button class="modal-button">Crear Cuenta</button>
        </div>
    </div>

          <!-- Modal del carrito de compras -->
          <div id="cartModal" class="modal">
            <div class="modal-content">
                <span class="close" onclick="closeModal('cartModal')">&times;</span>
                <div class="modal-header">Carrito de Compras</div>
                <div id="cartItems">
                    <!-- Los artículos del carrito se mostrarán aquí -->
                </div>
                <div id="cartSubtotal">Subtotal: $0.00</div>
                <div id="cartTotal">Total: $0.00</div>
                <button class="modal-button" onclick="checkout()">Checkout</button>
            </div>   
    </div>

    <script>
        let selectedCheckboxes = [];

        function filterCategory(category) {
            const products = document.querySelectorAll('.product');
            products.forEach(product => {
                const productCategory = product.getAttribute('data-category');
                if (category === 'Todos' || productCategory === category) {
                    product.classList.remove('hidden');
                } else {
                    product.classList.add('hidden');
                }
            });
        }

        function filterCheckboxes() {
            selectedCheckboxes = Array.from(document.querySelectorAll('.filters input[type="checkbox"]:checked'))
                                      .map(checkbox => checkbox.value);
            filterProducts();
        }

        function filterProducts() {
            const products = document.querySelectorAll('.product');
            const priceRange = document.getElementById('price-range').value;
            const minPrice = 0;
            const maxPrice = parseInt(priceRange);

            products.forEach(product => {
                const productCategory = product.getAttribute('data-category');
                const productPrice = parseInt(product.getAttribute('data-price'));
                
                const categoryMatch = selectedCheckboxes.length === 0 || selectedCheckboxes.includes(productCategory);
                const priceMatch = productPrice >= minPrice && productPrice <= maxPrice;

                if (categoryMatch && priceMatch) {
                    product.classList.remove('hidden');
                } else {
                    product.classList.add('hidden');
                }
            });

            updatePriceRange();
        }

        function updatePriceRange() {
            const priceRange = document.getElementById('price-range');
            const priceDisplay = document.getElementById('price-range-display');
            const minPrice = 0;
            const maxPrice = parseInt(priceRange.value);

            priceDisplay.textContent = `$${minPrice} - $${maxPrice}`;
            filterProducts();
        }

        function openModal(modalId) {
            document.getElementById(modalId).style.display = 'block';
        }

        function closeModal(modalId) {
            document.getElementById(modalId).style.display = 'none';
        }

        document.getElementById('loginBtn').addEventListener('click', () => openModal('loginModal'));
        document.getElementById('signupBtn').addEventListener('click', () => openModal('signupModal'));
        let cart = [];

function addToCart(productName, productPrice) {
    const quantityInput = event.target.previousElementSibling;
    const quantity = parseInt(quantityInput.value);
    const existingItem = cart.find(item => item.name === productName);

    if (existingItem) {
        existingItem.quantity += quantity;
    } else {
        cart.push({ name: productName, price: productPrice, quantity: quantity });
    }
    updateCartModal();
}

function updateCartModal() {
    const cartItemsContainer = document.getElementById('cartItems');
    const cartSubtotalElement = document.getElementById('cartSubtotal');
    const cartTotalElement = document.getElementById('cartTotal');
    
    cartItemsContainer.innerHTML = '';

    let subtotal = 0;

    cart.forEach(item => {
        const cartItem = document.createElement('div');
        cartItem.className = 'cart-item';

        const itemName = document.createElement('span');
        itemName.className = 'cart-item-name';
        itemName.textContent = item.name;

        const itemQuantity = document.createElement('span');
        itemQuantity.className = 'cart-item-quantity';
        itemQuantity.textContent = `x${item.quantity}`;

        const itemTotalPrice = item.price * item.quantity;
        subtotal += itemTotalPrice;

        cartItem.appendChild(itemName);
        cartItem.appendChild(itemQuantity);
        cartItemsContainer.appendChild(cartItem);
    });

    const total = subtotal; // Aquí puedes añadir impuestos u otros cargos si lo deseas

    cartSubtotalElement.textContent = `Subtotal: $${subtotal.toFixed(2)}`;
    cartTotalElement.textContent = `Total: $${total.toFixed(2)}`;
}

function openModal(modalId) {
    document.getElementById(modalId).style.display = 'block';
}

function closeModal(modalId) {
    document.getElementById(modalId).style.display = 'none';
}

document.getElementById('loginBtn').addEventListener('click', () => openModal('loginModal'));
document.getElementById('signupBtn').addEventListener('click', () => openModal('signupModal'));
document.getElementById('cartBtn').addEventListener('click', () => openModal('cartModal'));

function checkout() {
    alert('Procediendo al pago...');
    cart = [];
    updateCartModal();
    closeModal('cartModal');
}

</script>

</body>
</html>
