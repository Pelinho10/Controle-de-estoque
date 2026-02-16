<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
    <title>Controle do Barracão - Estoque e Empréstimos</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: #f5f5f5;
        }

        /* Tela de Login */
        .login-container {
            max-width: 400px;
            margin: 50px auto;
            padding: 20px;
            background: white;
            border-radius: 15px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }

        .login-header {
            text-align: center;
            margin-bottom: 30px;
        }

        .login-header h1 {
            color: #2c3e50;
            font-size: 28px;
        }

        .login-header p {
            color: #7f8c8d;
            font-size: 14px;
        }

        .login-form {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .input-group {
            display: flex;
            flex-direction: column;
            gap: 5px;
        }

        .input-group label {
            font-weight: 600;
            color: #34495e;
            font-size: 14px;
        }

        .input-group input {
            padding: 15px;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            font-size: 16px;
            transition: border-color 0.3s;
        }

        .input-group input:focus {
            outline: none;
            border-color: #3498db;
        }

        .login-btn {
            background-color: #3498db;
            color: white;
            padding: 15px;
            border: none;
            border-radius: 10px;
            font-size: 18px;
            font-weight: 600;
            cursor: pointer;
            transition: background-color 0.3s;
            margin-top: 10px;
        }

        .login-btn:hover {
            background-color: #2980b9;
        }

        .login-options {
            display: flex;
            justify-content: space-between;
            margin-top: 15px;
        }

        .login-options button {
            background: none;
            border: none;
            color: #3498db;
            font-size: 14px;
            cursor: pointer;
            padding: 5px;
        }

        .login-options button:hover {
            text-decoration: underline;
        }

        /* Tela Principal */
        .app-container {
            max-width: 500px;
            margin: 0 auto;
            background: #f5f5f5;
            min-height: 100vh;
            position: relative;
            padding-bottom: 80px;
        }

        .header {
            background: #2c3e50;
            color: white;
            padding: 20px;
            text-align: center;
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .header h1 {
            font-size: 24px;
        }

        .dashboard, .products-list, .movements-list {
            padding: 15px;
        }

        /* Cards do Dashboard */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
            margin-bottom: 20px;
        }

        .stat-card {
            background: white;
            padding: 20px;
            border-radius: 12px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            text-align: center;
        }

        .stat-card h3 {
            color: #7f8c8d;
            font-size: 14px;
            margin-bottom: 10px;
        }

        .stat-card .number {
            font-size: 32px;
            font-weight: bold;
            color: #2c3e50;
        }

        .stat-card .small {
            font-size: 12px;
            color: #7f8c8d;
            margin-top: 5px;
        }

        /* Estatísticas por Categoria */
        .category-stats {
            background: white;
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 20px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        .category-stats h3 {
            color: #2c3e50;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 5px;
        }

        .category-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 10px;
        }

        .category-item {
            background: #f8f9fa;
            padding: 10px;
            border-radius: 8px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .category-name {
            font-weight: 600;
            color: #34495e;
            font-size: 13px;
        }

        .category-count {
            background: #3498db;
            color: white;
            padding: 2px 8px;
            border-radius: 12px;
            font-size: 12px;
        }

        /* Alertas */
        .alert-card {
            background: #fff3cd;
            border: 1px solid #ffc107;
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 20px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        .alert-card h3 {
            color: #856404;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            gap: 5px;
        }

        .alert-item {
            background: white;
            padding: 12px;
            border-radius: 8px;
            margin-bottom: 8px;
            border-left: 4px solid #dc3545;
        }

        .alert-item small {
            display: block;
            color: #7f8c8d;
            margin-top: 5px;
        }

        /* Alertas de Empréstimo */
        .loan-alert {
            background: #cce5ff;
            border: 1px solid #17a2b8;
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 20px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        .loan-alert h3 {
            color: #0c5460;
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            gap: 5px;
        }

        .loan-item {
            background: white;
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 10px;
            border-left: 4px solid #17a2b8;
        }

        .loan-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 8px;
        }

        .loan-user {
            font-weight: bold;
            color: #17a2b8;
            font-size: 16px;
        }

        .loan-product {
            font-weight: 600;
            margin: 5px 0;
        }

        .return-btn {
            background-color: #28a745;
            color: white;
            border: none;
            padding: 10px;
            border-radius: 5px;
            cursor: pointer;
            font-weight: 600;
            margin-top: 10px;
            width: 100%;
            font-size: 14px;
        }

        .return-btn:hover {
            background-color: #218838;
        }

        /* Resumo de Movimentações */
        .movements-summary {
            background: white;
            padding: 15px;
            border-radius: 10px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        .movements-summary h3 {
            color: #2c3e50;
            margin-bottom: 15px;
        }

        .summary-stats {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 10px;
            text-align: center;
        }

        .summary-item {
            background: #f8f9fa;
            padding: 10px;
            border-radius: 8px;
        }

        .summary-item .label {
            font-size: 12px;
            color: #7f8c8d;
        }

        .summary-item .value {
            font-size: 20px;
            font-weight: bold;
            color: #2c3e50;
        }

        /* Menu Inferior */
        .bottom-menu {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: white;
            display: flex;
            justify-content: space-around;
            padding: 10px 0;
            border-top: 2px solid #e0e0e0;
            max-width: 500px;
            margin: 0 auto;
            width: 100%;
            z-index: 100;
        }

        .menu-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            color: #7f8c8d;
            font-size: 12px;
            background: none;
            border: none;
            cursor: pointer;
            padding: 5px 15px;
            transition: all 0.3s;
        }

        .menu-item.active {
            color: #3498db;
            transform: translateY(-2px);
        }

        .menu-item span {
            font-size: 24px;
            margin-bottom: 4px;
        }

        /* Barra de Pesquisa e Filtros */
        .search-box {
            width: 100%;
            padding: 15px;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            font-size: 16px;
            margin-bottom: 15px;
            background: white;
        }

        .category-filter {
            display: flex;
            gap: 10px;
            margin-bottom: 15px;
            overflow-x: auto;
            padding: 5px 0 15px;
            -webkit-overflow-scrolling: touch;
        }

        .category-filter button {
            padding: 10px 20px;
            border: none;
            border-radius: 25px;
            background: white;
            color: #2c3e50;
            font-weight: 600;
            cursor: pointer;
            white-space: nowrap;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            transition: all 0.3s;
        }

        .category-filter button.active {
            background: #3498db;
            color: white;
            transform: scale(1.05);
        }

        /* Botões de Ação */
        .add-btn {
            background-color: #27ae60;
            color: white;
            border: none;
            padding: 15px;
            border-radius: 10px;
            font-size: 16px;
            font-weight: 600;
            width: 100%;
            margin-bottom: 15px;
            cursor: pointer;
            transition: background-color 0.3s;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        .add-btn:hover {
            background-color: #219a52;
        }

        .action-buttons {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
        }

        .action-buttons button {
            flex: 1;
            padding: 15px;
            border: none;
            border-radius: 10px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            transition: transform 0.2s;
        }

        .action-buttons button:hover {
            transform: translateY(-2px);
        }

        .loan-action-btn {
            background-color: #17a2b8;
            color: white;
        }

        /* Cards de Produto */
        .product-card {
            background: white;
            padding: 15px;
            border-radius: 12px;
            margin-bottom: 15px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            transition: transform 0.2s;
        }

        .product-card:hover {
            transform: translateY(-2px);
        }

        .product-card.low-stock {
            border-left: 4px solid #dc3545;
        }

        .product-card.on-loan {
            border-left: 4px solid #17a2b8;
            background-color: #f0f9ff;
        }

        .product-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
            flex-wrap: wrap;
            gap: 10px;
        }

        .product-name {
            font-size: 18px;
            font-weight: 600;
            color: #2c3e50;
        }

        .product-category {
            color: #7f8c8d;
            font-size: 12px;
            background: #f0f0f0;
            padding: 4px 12px;
            border-radius: 20px;
            font-weight: 600;
        }

        .product-local {
            color: #7f8c8d;
            font-size: 13px;
            background: #e8f4fd;
            padding: 4px 12px;
            border-radius: 20px;
            display: inline-block;
            margin-bottom: 10px;
        }

        .loan-badge {
            background-color: #17a2b8;
            color: white;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
            display: inline-block;
            margin-bottom: 10px;
        }

        .product-details {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 10px;
            margin: 15px 0;
            background: #f8f9fa;
            padding: 10px;
            border-radius: 8px;
        }

        .product-detail {
            text-align: center;
        }

        .product-detail label {
            font-size: 11px;
            color: #7f8c8d;
            display: block;
            margin-bottom: 3px;
        }

        .product-detail span {
            font-size: 18px;
            font-weight: 700;
        }

        .product-actions {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 8px;
            margin-top: 15px;
        }

        .product-actions button {
            padding: 10px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            font-size: 13px;
            transition: all 0.2s;
        }

        .product-actions button:hover {
            transform: translateY(-2px);
            filter: brightness(1.1);
        }

        .edit-btn {
            background-color: #3498db;
            color: white;
        }

        .delete-btn {
            background-color: #e74c3c;
            color: white;
        }

        .loan-btn {
            background-color: #17a2b8;
            color: white;
        }

        /* Modais */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0,0,0,0.5);
            justify-content: center;
            align-items: center;
            z-index: 1000;
            padding: 20px;
        }

        .modal.active {
            display: flex;
        }

        .modal-content {
            background: white;
            padding: 25px;
            border-radius: 20px;
            max-width: 100%;
            width: 450px;
            max-height: 90vh;
            overflow-y: auto;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .modal-header h2 {
            color: #2c3e50;
            font-size: 22px;
        }

        .close-btn {
            background: none;
            border: none;
            font-size: 28px;
            cursor: pointer;
            color: #7f8c8d;
            padding: 0 10px;
        }

        .close-btn:hover {
            color: #2c3e50;
        }

        .modal-form {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .modal-form input,
        .modal-form select,
        .modal-form textarea {
            padding: 15px;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            font-size: 16px;
            transition: border-color 0.3s;
        }

        .modal-form input:focus,
        .modal-form select:focus,
        .modal-form textarea:focus {
            outline: none;
            border-color: #3498db;
        }

        .modal-form textarea {
            min-height: 100px;
            resize: vertical;
        }

        .submit-btn {
            background-color: #27ae60;
            color: white;
            padding: 15px;
            border: none;
            border-radius: 10px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            margin-top: 10px;
            transition: background-color 0.3s;
        }

        .submit-btn:hover {
            background-color: #219a52;
        }

        /* Filtro de Data */
        .filter-section {
            background: white;
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 20px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        .filter-section input {
            width: 100%;
            padding: 12px;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            font-size: 16px;
        }

        /* Perfil */
        .profile-section {
            padding: 15px;
        }

        .profile-card {
            background: white;
            padding: 30px;
            border-radius: 15px;
            text-align: center;
            margin-bottom: 20px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        .profile-avatar {
            font-size: 80px;
            margin-bottom: 15px;
        }

        .profile-name {
            font-size: 24px;
            font-weight: 600;
            color: #2c3e50;
            margin-bottom: 5px;
        }

        .profile-email {
            color: #7f8c8d;
            margin-bottom: 20px;
        }

        .logout-btn {
            background-color: #e74c3c;
            color: white;
            border: none;
            padding: 15px;
            border-radius: 10px;
            font-size: 16px;
            font-weight: 600;
            width: 100%;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .logout-btn:hover {
            background-color: #c0392b;
        }

        /* Utilitários */
        .text-success { color: #27ae60; }
        .text-danger { color: #e74c3c; }
        .text-info { color: #17a2b8; }
        .text-warning { color: #f39c12; }
        
        .mb-2 { margin-bottom: 10px; }
        .mt-2 { margin-top: 10px; }
        .text-center { text-align: center; }
    </style>
</head>
<body>
    <!-- Tela de Login -->
    <div id="loginScreen" class="login-container">
        <div class="login-header">
            <h1>🔧 Controle do Barracão</h1>
            <p>Gerencie seu estoque e empréstimos</p>
        </div>
        
        <div class="login-form">
            <div class="input-group">
                <label>👤 Nome de usuário</label>
                <input type="text" id="username" placeholder="Digite seu nome" value="Admin">
            </div>
            
            <div class="input-group">
                <label>🔑 Senha</label>
                <input type="password" id="password" placeholder="Digite sua senha" value="123456">
            </div>
            
            <button class="login-btn" onclick="login()">Entrar</button>
            
            <div class="login-options">
                <button onclick="showRegister()">📝 Cadastrar</button>
                <button onclick="showRecover()">🔐 Recuperar senha</button>
            </div>
        </div>
    </div>

    <!-- Aplicativo Principal -->
    <div id="appScreen" class="app-container" style="display: none;">
        <div class="header">
            <h1 id="screenTitle">Dashboard</h1>
        </div>

        <!-- Dashboard -->
        <div id="dashboardScreen" class="dashboard">
            <div class="stats-grid">
                <div class="stat-card">
                    <h3>📦 Total Itens</h3>
                    <div class="number" id="totalProducts">0</div>
                    <div class="small">produtos cadastrados</div>
                </div>
                <div class="stat-card">
                    <h3>📊 Unidades</h3>
                    <div class="number" id="totalStock">0</div>
                    <div class="small">em estoque</div>
                </div>
            </div>

            <!-- Estatísticas por Categoria -->
            <div class="category-stats">
                <h3>📋 Itens por Categoria</h3>
                <div class="category-grid" id="categoryStats"></div>
            </div>

            <!-- Alerta de Empréstimos -->
            <div class="loan-alert" id="loanAlert" style="display: none;">
                <h3>🔧 Itens Emprestados</h3>
                <div id="loanList"></div>
            </div>

            <!-- Alerta de Estoque Baixo -->
            <div class="alert-card" id="lowStockAlert">
                <h3>⚠️ Estoque Baixo</h3>
                <div id="lowStockList"></div>
            </div>

            <!-- Resumo do Dia -->
            <div class="movements-summary">
                <h3>📅 Movimentações de Hoje</h3>
                <div class="summary-stats">
                    <div class="summary-item">
                        <div class="label">Entradas</div>
                        <div class="value" id="todayEntries">0</div>
                    </div>
                    <div class="summary-item">
                        <div class="label">Saídas</div>
                        <div class="value" id="todayExits">0</div>
                    </div>
                    <div class="summary-item">
                        <div class="label">Empréstimos</div>
                        <div class="value" id="todayLoans">0</div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Produtos -->
        <div id="productsScreen" style="display: none;">
            <div class="products-list">
                <button class="add-btn" onclick="openProductModal()">+ Novo Item</button>
                
                <input type="text" class="search-box" id="searchProduct" 
                       placeholder="🔍 Buscar por nome ou local..." onkeyup="filterProducts()">
                
                <div class="category-filter" id="categoryFilter"></div>
                
                <div class="action-buttons">
                    <button class="loan-action-btn" onclick="openLoanModal()">
                        🔧 Novo Empréstimo
                    </button>
                </div>
                
                <div id="productsList"></div>
            </div>
        </div>

        <!-- Movimentações -->
        <div id="movementsScreen" style="display: none;">
            <div class="movements-list">
                <div class="filter-section">
                    <input type="date" id="movementDate" onchange="filterMovements()">
                </div>
                
                <div class="action-buttons">
                    <button class="add-btn" onclick="openEntryModal()" style="background-color: #27ae60;">
                        📥 Entrada
                    </button>
                    <button class="add-btn" onclick="openExitModal()" style="background-color: #e74c3c;">
                        📤 Saída
                    </button>
                </div>
                
                <div id="movementsList"></div>
            </div>
        </div>

        <!-- Perfil -->
        <div id="profileScreen" style="display: none;">
            <div class="profile-section">
                <div class="profile-card">
                    <div class="profile-avatar">👤</div>
                    <div class="profile-name" id="profileName">Usuário</div>
                    <div class="profile-email">usuario@email.com</div>
                </div>
                
                <button class="logout-btn" onclick="logout()">🚪 Sair da conta</button>
            </div>
        </div>

        <!-- Menu Inferior -->
        <div class="bottom-menu">
            <button class="menu-item active" onclick="changeScreen('dashboard')">
                <span>🏠</span>
                Início
            </button>
            <button class="menu-item" onclick="changeScreen('products')">
                <span>📦</span>
                Itens
            </button>
            <button class="menu-item" onclick="changeScreen('movements')">
                <span>📊</span>
                Mov.
            </button>
            <button class="menu-item" onclick="changeScreen('profile')">
                <span>👤</span>
                Perfil
            </button>
        </div>
    </div>

    <!-- Modal de Produto -->
    <div id="productModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2 id="modalTitle">Novo Item</h2>
                <button class="close-btn" onclick="closeModal('productModal')">&times;</button>
            </div>
            
            <div class="modal-form">
                <input type="text" id="productName" placeholder="Nome do item *" required>
                <input type="text" id="productLocal" placeholder="Local (ex: Prateleira A1) *" required>
                
                <select id="productCategory" required>
                    <option value="">Selecione uma categoria *</option>
                    <option value="Elétrica">⚡ Elétrica</option>
                    <option value="Jardim">🌿 Jardim</option>
                    <option value="Hidráulica">💧 Hidráulica</option>
                    <option value="Ferramentas">🔨 Ferramentas</option>
                    <option value="Parafusos">🔩 Parafusos e Porcas</option>
                    <option value="EPI">🪖 EPI (Segurança)</option>
                    <option value="Tintas">🎨 Tintas</option>
                    <option value="Limpeza">🧹 Limpeza</option>
                    <option value="Madeira">🪵 Madeira</option>
                    <option value="Geral">📋 Geral</option>
                    <option value="Outros">📦 Outros</option>
                </select>
                
                <input type="number" id="productQuantity" placeholder="Quantidade *" min="0" required>
                <input type="number" id="productMinQuantity" placeholder="Quantidade mínima *" min="0" required>
                
                <input type="hidden" id="editingProductId">
                <button class="submit-btn" onclick="saveProduct()">💾 Salvar Item</button>
            </div>
        </div>
    </div>

    <!-- Modal de Movimentação -->
    <div id="movementModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2 id="movementModalTitle">Nova Movimentação</h2>
                <button class="close-btn" onclick="closeModal('movementModal')">&times;</button>
            </div>
            
            <div class="modal-form">
                <select id="movementProduct" required>
                    <option value="">Selecione um item *</option>
                </select>
                
                <input type="number" id="movementQuantity" placeholder="Quantidade *" min="1" required>
                <input type="date" id="movementDateField" required>
                <textarea id="movementObservation" placeholder="Observação (opcional)"></textarea>
                
                <input type="hidden" id="movementType">
                <button class="submit-btn" onclick="saveMovement()">📝 Registrar</button>
            </div>
        </div>
    </div>

    <!-- Modal de Empréstimo -->
    <div id="loanModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2>Novo Empréstimo</h2>
                <button class="close-btn" onclick="closeModal('loanModal')">&times;</button>
            </div>
            
            <div class="modal-form">
                <input type="text" id="loanUserName" placeholder="Nome de quem está pegando *" required>
                
                <select id="loanProduct" required>
                    <option value="">Selecione um item *</option>
                </select>
                
                <input type="number" id="loanQuantity" placeholder="Quantidade *" value="1" min="1" required>
                <input type="date" id="loanDate" required>
                <textarea id="loanObservation" placeholder="Observação (opcional)"></textarea>
                
                <button class="submit-btn" onclick="saveLoan()">🔧 Registrar Empréstimo</button>
            </div>
        </div>
    </div>

    <!-- Modal de Devolução -->
    <div id="returnModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2>Registrar Devolução</h2>
                <button class="close-btn" onclick="closeModal('returnModal')">&times;</button>
            </div>
            
            <div class="modal-form">
                <div style="background: #f8f9fa; padding: 15px; border-radius: 8px; margin-bottom: 15px;">
                    <p id="returnInfo" style="line-height: 1.6;"></p>
                </div>
                
                <input type="date" id="returnDate" required>
                <textarea id="returnObservation" placeholder="Observação (opcional)"></textarea>
                
                <input type="hidden" id="returnLoanId">
                <button class="submit-btn" onclick="saveReturn()">✅ Confirmar Devolução</button>
            </div>
        </div>
    </div>

    <!-- Modal de Cadastro/Recuperação -->
    <div id="authModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2 id="authModalTitle">Cadastro</h2>
                <button class="close-btn" onclick="closeModal('authModal')">&times;</button>
            </div>
            
            <div class="modal-form" id="authForm">
                <input type="text" id="registerName" placeholder="Nome completo *">
                <input type="email" id="registerEmail" placeholder="E-mail *">
                <input type="password" id="registerPassword" placeholder="Senha *">
                <input type="password" id="registerConfirmPassword" placeholder="Confirmar senha *">
                <button class="submit-btn" onclick="registerUser()">📝 Cadastrar</button>
            </div>
        </div>
    </div>

    <script>
        // ============================================
        // DADOS INICIAIS - ESTOQUE COMPLETO DO BARRACÃO
        // ============================================
        let products = JSON.parse(localStorage.getItem('products')) || [
            // ⚡ ELÉTRICA
            { id: 101, name: 'Fio Elétrico 2.5mm (rolo 100m)', local: 'Prateleira A1', category: 'Elétrica', quantity: 15, minQuantity: 5, date: '2024-01-15' },
            { id: 102, name: 'Fio Elétrico 1.5mm (rolo 100m)', local: 'Prateleira A1', category: 'Elétrica', quantity: 20, minQuantity: 5, date: '2024-01-15' },
            { id: 103, name: 'Fio Elétrico 4mm (rolo 100m)', local: 'Prateleira A2', category: 'Elétrica', quantity: 8, minQuantity: 3, date: '2024-01-15' },
            { id: 104, name: 'Cabo Flexível 2.5mm (rolo 100m)', local: 'Prateleira A2', category: 'Elétrica', quantity: 12, minQuantity: 4, date: '2024-01-15' },
            { id: 105, name: 'Disjuntor 10A', local: 'Gaveta 1', category: 'Elétrica', quantity: 45, minQuantity: 20, date: '2024-01-15' },
            { id: 106, name: 'Disjuntor 16A', local: 'Gaveta 1', category: 'Elétrica', quantity: 38, minQuantity: 20, date: '2024-01-15' },
            { id: 107, name: 'Disjuntor 20A', local: 'Gaveta 1', category: 'Elétrica', quantity: 42, minQuantity: 20, date: '2024-01-15' },
            { id: 108, name: 'Interruptor Simples', local: 'Gaveta 3', category: 'Elétrica', quantity: 60, minQuantity: 30, date: '2024-01-15' },
            { id: 109, name: 'Tomada 2P+T 10A', local: 'Gaveta 4', category: 'Elétrica', quantity: 80, minQuantity: 30, date: '2024-01-15' },
            { id: 110, name: 'Fita Isolante (rolo)', local: 'Gaveta 6', category: 'Elétrica', quantity: 45, minQuantity: 20, date: '2024-01-15' },

            // 🌿 JARDIM
            { id: 201, name: 'Cortador de Grama Elétrico', local: 'Galpão Ferramentas', category: 'Jardim', quantity: 3, minQuantity: 1, date: '2024-01-15' },
            { id: 202, name: 'Roçadeira Costal', local: 'Galpão Ferramentas', category: 'Jardim', quantity: 2, minQuantity: 1, date: '2024-01-15' },
            { id: 203, name: 'Mangueira 1/2" (rolo 50m)', local: 'Prateleira B1', category: 'Jardim', quantity: 8, minQuantity: 3, date: '2024-01-15' },
            { id: 204, name: 'Mangueira 3/4" (rolo 50m)', local: 'Prateleira B1', category: 'Jardim', quantity: 6, minQuantity: 2, date: '2024-01-15' },
            { id: 205, name: 'Pá de Jardinagem', local: 'Prateleira B2', category: 'Jardim', quantity: 10, minQuantity: 3, date: '2024-01-15' },
            { id: 206, name: 'Tesoura de Poda', local: 'Gaveta 8', category: 'Jardim', quantity: 6, minQuantity: 2, date: '2024-01-15' },
            { id: 207, name: 'Saco de Terra 20kg', local: 'Estoque externo', category: 'Jardim', quantity: 25, minQuantity: 10, date: '2024-01-15' },
            { id: 208, name: 'Adubo NPK (kg)', local: 'Estoque externo', category: 'Jardim', quantity: 40, minQuantity: 15, date: '2024-01-15' },

            // 💧 HIDRÁULICA
            { id: 301, name: 'Tubo PVC 25mm (barra 6m)', local: 'Cantinho dos tubos', category: 'Hidráulica', quantity: 20, minQuantity: 8, date: '2024-01-15' },
            { id: 302, name: 'Tubo PVC 32mm (barra 6m)', local: 'Cantinho dos tubos', category: 'Hidráulica', quantity: 15, minQuantity: 6, date: '2024-01-15' },
            { id: 303, name: 'Joelho 90° 25mm', local: 'Caixa 10', category: 'Hidráulica', quantity: 80, minQuantity: 30, date: '2024-01-15' },
            { id: 304, name: 'Tê 25mm', local: 'Caixa 11', category: 'Hidráulica', quantity: 45, minQuantity: 15, date: '2024-01-15' },
            { id: 305, name: 'Cola para PVC (tubo)', local: 'Gaveta 12', category: 'Hidráulica', quantity: 22, minQuantity: 8, date: '2024-01-15' },
            { id: 306, name: 'Fita Veda-rosca (rolo)', local: 'Gaveta 12', category: 'Hidráulica', quantity: 35, minQuantity: 15, date: '2024-01-15' },

            // 🔨 FERRAMENTAS
            { id: 401, name: 'Furadeira de Impacto', local: 'Armário Ferramentas', category: 'Ferramentas', quantity: 4, minQuantity: 2, date: '2024-01-15' },
            { id: 402, name: 'Parafusadeira', local: 'Armário Ferramentas', category: 'Ferramentas', quantity: 5, minQuantity: 2, date: '2024-01-15' },
            { id: 403, name: 'Esmerilhadeira', local: 'Armário Ferramentas', category: 'Ferramentas', quantity: 3, minQuantity: 1, date: '2024-01-15' },
            { id: 404, name: 'Martelo', local: 'Prateleira C1', category: 'Ferramentas', quantity: 12, minQuantity: 4, date: '2024-01-15' },
            { id: 405, name: 'Chave de Fenda (kit)', local: 'Gaveta 14', category: 'Ferramentas', quantity: 8, minQuantity: 3, date: '2024-01-15' },
            { id: 406, name: 'Alicate Universal', local: 'Gaveta 15', category: 'Ferramentas', quantity: 10, minQuantity: 4, date: '2024-01-15' },
            { id: 407, name: 'Trena 5m', local: 'Gaveta 17', category: 'Ferramentas', quantity: 15, minQuantity: 5, date: '2024-01-15' },

            // 🔩 PARAFUSOS
            { id: 501, name: 'Parafuso Madeira 3x30mm (caixa)', local: 'Gaveta 18', category: 'Parafusos', quantity: 25, minQuantity: 8, date: '2024-01-15' },
            { id: 502, name: 'Parafuso Madeira 4x40mm (caixa)', local: 'Gaveta 18', category: 'Parafusos', quantity: 22, minQuantity: 8, date: '2024-01-15' },
            { id: 503, name: 'Porca Sextavada 6mm (caixa)', local: 'Gaveta 20', category: 'Parafusos', quantity: 30, minQuantity: 10, date: '2024-01-15' },
            { id: 504, name: 'Arruela Lisa 6mm (caixa)', local: 'Gaveta 21', category: 'Parafusos', quantity: 40, minQuantity: 15, date: '2024-01-15' },
            { id: 505, name: 'Bucha S6 (caixa)', local: 'Gaveta 22', category: 'Parafusos', quantity: 35, minQuantity: 12, date: '2024-01-15' },

            // 🪖 EPI
            { id: 601, name: 'Capacete de Segurança', local: 'Armário EPI', category: 'EPI', quantity: 25, minQuantity: 10, date: '2024-01-15' },
            { id: 602, name: 'Óculos de Proteção', local: 'Armário EPI', category: 'EPI', quantity: 30, minQuantity: 15, date: '2024-01-15' },
            { id: 603, name: 'Protetor Auricular', local: 'Armário EPI', category: 'EPI', quantity: 28, minQuantity: 12, date: '2024-01-15' },
            { id: 604, name: 'Luva de Raspa (par)', local: 'Armário EPI', category: 'EPI', quantity: 35, minQuantity: 15, date: '2024-01-15' },
            { id: 605, name: 'Máscara PFF2', local: 'Armário EPI', category: 'EPI', quantity: 50, minQuantity: 20, date: '2024-01-15' },

            // 🎨 TINTAS
            { id: 701, name: 'Tinta Lata 18L Branco', local: 'Estoque Tintas', category: 'Tintas', quantity: 12, minQuantity: 4, date: '2024-01-15' },
            { id: 702, name: 'Esmalte Sintético (galão)', local: 'Estoque Tintas', category: 'Tintas', quantity: 15, minQuantity: 5, date: '2024-01-15' },
            { id: 703, name: 'Rolo de Pintura', local: 'Prateleira D1', category: 'Tintas', quantity: 18, minQuantity: 6, date: '2024-01-15' },
            { id: 704, name: 'Pincel 2"', local: 'Prateleira D1', category: 'Tintas', quantity: 25, minQuantity: 8, date: '2024-01-15' },

            // 🧹 LIMPEZA
            { id: 801, name: 'Vassoura', local: 'Prateleira E1', category: 'Limpeza', quantity: 15, minQuantity: 5, date: '2024-01-15' },
            { id: 802, name: 'Rodo', local: 'Prateleira E1', category: 'Limpeza', quantity: 12, minQuantity: 4, date: '2024-01-15' },
            { id: 803, name: 'Balde 10L', local: 'Prateleira E2', category: 'Limpeza', quantity: 10, minQuantity: 3, date: '2024-01-15' },
            { id: 804, name: 'Detergente 5L', local: 'Prateleira E3', category: 'Limpeza', quantity: 18, minQuantity: 5, date: '2024-01-15' },

            // 🪵 MADEIRA
            { id: 901, name: 'Tábua Pinho 2,5x10x300cm', local: 'Estoque Madeiras', category: 'Madeira', quantity: 25, minQuantity: 8, date: '2024-01-15' },
            { id: 902, name: 'Sarrafos 2x5x300cm', local: 'Estoque Madeiras', category: 'Madeira', quantity: 40, minQuantity: 15, date: '2024-01-15' },
            { id: 903, name: 'Compensado 15mm (placa)', local: 'Estoque Madeiras', category: 'Madeira', quantity: 12, minQuantity: 4, date: '2024-01-15' },

            // 📋 GERAL (Materiais diversos)
            { id: 1001, name: 'Corda Nylon 10mm (rolo 50m)', local: 'Prateleira F1', category: 'Geral', quantity: 8, minQuantity: 2, date: '2024-01-15' },
            { id: 1002, name: 'Lona Plástica 4x6m', local: 'Prateleira F1', category: 'Geral', quantity: 15, minQuantity: 5, date: '2024-01-15' },
            { id: 1003, name: 'Fita Crepe (rolo)', local: 'Gaveta 23', category: 'Geral', quantity: 30, minQuantity: 10, date: '2024-01-15' },
            { id: 1004, name: 'Fita Dupla Face (rolo)', local: 'Gaveta 23', category: 'Geral', quantity: 20, minQuantity: 5, date: '2024-01-15' },
            { id: 1005, name: 'Cola Branca 1kg', local: 'Gaveta 24', category: 'Geral', quantity: 12, minQuantity: 4, date: '2024-01-15' },
            { id: 1006, name: 'Cola Instantânea (tubo)', local: 'Gaveta 24', category: 'Geral', quantity: 25, minQuantity: 8, date: '2024-01-15' },
            { id: 1007, name: 'Pilhas AA (pacote 4un)', local: 'Gaveta 25', category: 'Geral', quantity: 40, minQuantity: 15, date: '2024-01-15' },
            { id: 1008, name: 'Pilhas AAA (pacote 4un)', local: 'Gaveta 25', category: 'Geral', quantity: 35, minQuantity: 15, date: '2024-01-15' },
            { id: 1009, name: 'Lanterna Média', local: 'Prateleira F2', category: 'Geral', quantity: 10, minQuantity: 3, date: '2024-01-15' },
            { id: 1010, name: 'Extensão 10m', local: 'Prateleira F2', category: 'Geral', quantity: 8, minQuantity: 2, date: '2024-01-15' },
            { id: 1011, name: 'Adaptador Tomada', local: 'Gaveta 26', category: 'Geral', quantity: 20, minQuantity: 6, date: '2024-01-15' },
            { id: 1012, name: 'Multímetro Digital', local: 'Gaveta 26', category: 'Geral', quantity: 4, minQuantity: 1, date: '2024-01-15' },

            // 📦 OUTROS (Itens diversos)
            { id: 1101, name: 'Cadeado Médio', local: 'Gaveta 27', category: 'Outros', quantity: 15, minQuantity: 5, date: '2024-01-15' },
            { id: 1102, name: 'Cadeado Grande', local: 'Gaveta 27', category: 'Outros', quantity: 10, minQuantity: 3, date: '2024-01-15' },
            { id: 1103, name: 'Dobradiça 3" (par)', local: 'Gaveta 28', category: 'Outros', quantity: 30, minQuantity: 10, date: '2024-01-15' },
            { id: 1104, name: 'Fecho para Portão', local: 'Gaveta 28', category: 'Outros', quantity: 8, minQuantity: 2, date: '2024-01-15' },
            { id: 1105, name: 'Rodízio para Móvel', local: 'Gaveta 29', category: 'Outros', quantity: 24, minQuantity: 8, date: '2024-01-15' },
            { id: 1106, name: 'Cantoneira de Metal', local: 'Gaveta 29', category: 'Outros', quantity: 50, minQuantity: 20, date: '2024-01-15' },
            { id: 1107, name: 'Abraçadeira Nylon (pacote)', local: 'Gaveta 30', category: 'Outros', quantity: 15, minQuantity: 5, date: '2024-01-15' },
            { id: 1108, name: 'Arame Galvanizado (rolo)', local: 'Prateleira G1', category: 'Outros', quantity: 6, minQuantity: 2, date: '2024-01-15' },
            { id: 1109, name: 'Cabo de Aço 3mm (rolo)', local: 'Prateleira G1', category: 'Outros', quantity: 4, minQuantity: 1, date: '2024-01-15' },
            { id: 1110, name: 'Gancho para Parede', local: 'Gaveta 31', category: 'Outros', quantity: 40, minQuantity: 15, date: '2024-01-15' },
            { id: 1111, name: 'Suporte para TV', local: 'Prateleira G2', category: 'Outros', quantity: 5, minQuantity: 1, date: '2024-01-15' },
            { id: 1112, name: 'Ventilador de Parede', local: 'Prateleira G2', category: 'Outros', quantity: 3, minQuantity: 1, date: '2024-01-15' }
        ];
        
        let movements = JSON.parse(localStorage.getItem('movements')) || [];
        let loans = JSON.parse(localStorage.getItem('loans')) || [];
        let users = JSON.parse(localStorage.getItem('users')) || [
            { name: 'Admin', email: 'admin@email.com', password: '123456' }
        ];
        
        let currentUser = null;
        let currentCategory = 'todos';
        let currentSearchTerm = '';

        // ============================================
        // FUNÇÕES DE AUTENTICAÇÃO
        // ============================================
        function login() {
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            
            const user = users.find(u => u.name === username && u.password === password);
            
            if (user) {
                currentUser = user;
                document.getElementById('loginScreen').style.display = 'none';
                document.getElementById('appScreen').style.display = 'block';
                document.getElementById('profileName').textContent = user.name;
                updateDashboard();
                loadProducts();
                loadMovements();
                loadProductSelect();
                loadLoanProductSelect();
                loadCategoryFilter();
            } else {
                alert('Usuário ou senha inválidos! Use Admin/123456');
            }
        }

        function showRegister() {
            document.getElementById('authModalTitle').textContent = 'Cadastro de Usuário';
            document.getElementById('authForm').innerHTML = `
                <input type="text" id="registerName" placeholder="Nome completo *">
                <input type="email" id="registerEmail" placeholder="E-mail *">
                <input type="password" id="registerPassword" placeholder="Senha *">
                <input type="password" id="registerConfirmPassword" placeholder="Confirmar senha *">
                <button class="submit-btn" onclick="registerUser()">📝 Cadastrar</button>
            `;
            document.getElementById('authModal').classList.add('active');
        }

        function registerUser() {
            const name = document.getElementById('registerName').value;
            const email = document.getElementById('registerEmail').value;
            const password = document.getElementById('registerPassword').value;
            const confirmPassword = document.getElementById('registerConfirmPassword').value;
            
            if (!name || !email || !password) {
                alert('Preencha todos os campos!');
                return;
            }
            
            if (password !== confirmPassword) {
                alert('As senhas não coincidem!');
                return;
            }
            
            if (users.find(u => u.email === email)) {
                alert('E-mail já cadastrado!');
                return;
            }
            
            users.push({ name, email, password });
            localStorage.setItem('users', JSON.stringify(users));
            alert('Usuário cadastrado com sucesso!');
            closeModal('authModal');
        }

        function showRecover() {
            document.getElementById('authModalTitle').textContent = 'Recuperar Senha';
            document.getElementById('authForm').innerHTML = `
                <input type="email" id="recoverEmail" placeholder="Digite seu e-mail">
                <button class="submit-btn" onclick="recoverPassword()">🔐 Recuperar</button>
            `;
            document.getElementById('authModal').classList.add('active');
        }

        function recoverPassword() {
            const email = document.getElementById('recoverEmail').value;
            const user = users.find(u => u.email === email);
            
            if (user) {
                alert(`Sua senha é: ${user.password}`);
            } else {
                alert('E-mail não encontrado!');
            }
            closeModal('authModal');
        }

        // ============================================
        // FUNÇÕES DO DASHBOARD
        // ============================================
        function updateDashboard() {
            document.getElementById('totalProducts').textContent = products.length;
            
            const totalStock = products.reduce((sum, p) => sum + p.quantity, 0);
            document.getElementById('totalStock').textContent = totalStock;
            
            updateCategoryStats();
            updateLowStockAlerts();
            updateLoanAlerts();
            updateTodayMovements();
        }

        function updateCategoryStats() {
            const categories = {};
            products.forEach(p => {
                categories[p.category] = (categories[p.category] || 0) + 1;
            });
            
            const statsDiv = document.getElementById('categoryStats');
            statsDiv.innerHTML = Object.entries(categories)
                .sort((a, b) => b[1] - a[1])
                .map(([cat, count]) => `
                    <div class="category-item">
                        <span class="category-name">${cat}</span>
                        <span class="category-count">${count}</span>
                    </div>
                `).join('');
        }

        function updateLowStockAlerts() {
            const lowStock = products.filter(p => p.quantity <= p.minQuantity);
            const lowStockList = document.getElementById('lowStockList');
            
            if (lowStock.length > 0) {
                lowStockList.innerHTML = lowStock.map(p => `
                    <div class="alert-item">
                        <strong>${p.name}</strong> - ${p.quantity} / ${p.minQuantity}
                        <small>📍 ${p.local} | 🏷️ ${p.category}</small>
                    </div>
                `).join('');
                
                if (Notification.permission === 'granted') {
                    new Notification('⚠️ Estoque Baixo', {
                        body: `${lowStock.length} item(ns) precisam de reposição`
                    });
                }
            } else {
                lowStockList.innerHTML = '<p style="text-align: center; color: #27ae60;">✅ Todos os itens estão com estoque adequado</p>';
            }
        }

        function updateLoanAlerts() {
            const activeLoans = loans.filter(l => !l.returned);
            const loanAlert = document.getElementById('loanAlert');
            const loanList = document.getElementById('loanList');
            
            if (activeLoans.length > 0) {
                loanAlert.style.display = 'block';
                loanList.innerHTML = activeLoans.map(l => `
                    <div class="loan-item">
                        <div class="loan-header">
                            <span class="loan-user">👤 ${l.userName}</span>
                            <small>${l.date}</small>
                        </div>
                        <div class="loan-product">🔧 ${l.productName}</div>
                        <div><small>📍 ${l.productLocal}</small></div>
                        <div>📦 Quantidade: ${l.quantity}</div>
                        ${l.observation ? `<small>📝 ${l.observation}</small>` : ''}
                        <button class="return-btn" onclick="openReturnModal(${l.id})">
                            ↩️ Registrar Devolução
                        </button>
                    </div>
                `).join('');
            } else {
                loanAlert.style.display = 'none';
            }
        }

        function updateTodayMovements() {
            const today = new Date().toISOString().split('T')[0];
            const todayMovements = movements.filter(m => m.date === today);
            const todayLoans = loans.filter(l => l.date === today && !l.returned);
            
            document.getElementById('todayEntries').textContent = todayMovements
                .filter(m => m.type === 'entry')
                .reduce((sum, m) => sum + m.quantity, 0);
            
            document.getElementById('todayExits').textContent = todayMovements
                .filter(m => m.type === 'exit')
                .reduce((sum, m) => sum + m.quantity, 0);
                
            document.getElementById('todayLoans').textContent = todayLoans.length;
        }

        // ============================================
        // FUNÇÕES DE PRODUTOS
        // ============================================
        function loadCategoryFilter() {
            const categories = ['todos', ...new Set(products.map(p => p.category))];
            const filterDiv = document.getElementById('categoryFilter');
            
            filterDiv.innerHTML = categories.map(cat => {
                const displayName = cat === 'todos' ? 'Todos' : cat;
                return `<button class="${cat === 'todos' ? 'active' : ''}" 
                        onclick="filterByCategory('${cat}')">${displayName}</button>`;
            }).join('');
        }

        function filterByCategory(category) {
            currentCategory = category;
            
            document.querySelectorAll('#categoryFilter button').forEach(btn => {
                btn.classList.remove('active');
                if (btn.textContent === (category === 'todos' ? 'Todos' : category)) {
                    btn.classList.add('active');
                }
            });
            
            filterProducts();
        }

        function filterProducts() {
            const searchTerm = document.getElementById('searchProduct').value.toLowerCase();
            
            const filtered = products.filter(p => {
                const matchesCategory = currentCategory === 'todos' || p.category === currentCategory;
                const matchesSearch = p.name.toLowerCase().includes(searchTerm) ||
                                     p.local.toLowerCase().includes(searchTerm) ||
                                     p.category.toLowerCase().includes(searchTerm);
                return matchesCategory && matchesSearch;
            });
            
            displayProducts(filtered);
        }

        function displayProducts(productsToShow) {
            const list = document.getElementById('productsList');
            const activeLoans = loans.filter(l => !l.returned);
            
            if (productsToShow.length === 0) {
                list.innerHTML = '<p style="text-align: center; padding: 30px;">🔍 Nenhum item encontrado</p>';
                return;
            }
            
            list.innerHTML = productsToShow.map(p => {
                const productLoans = activeLoans.filter(l => l.productId === p.id);
                const loanedQuantity = productLoans.reduce((sum, l) => sum + l.quantity, 0);
                const availableQuantity = p.quantity - loanedQuantity;
                
                return `
                    <div class="product-card ${p.quantity <= p.minQuantity ? 'low-stock' : ''} ${productLoans.length > 0 ? 'on-loan' : ''}">
                        <div class="product-header">
                            <span class="product-name">${p.name}</span>
                            <span class="product-category">${p.category}</span>
                        </div>
                        <span class="product-local">📍 ${p.local}</span>
                        
                        ${productLoans.length > 0 ? 
                            `<div class="loan-badge">🔧 ${loanedQuantity} emprestado(s)</div>` : ''}
                        
                        <div class="product-details">
                            <div class="product-detail">
                                <label>Disponível</label>
                                <span style="color: ${availableQuantity <= p.minQuantity ? '#e74c3c' : '#27ae60'}">
                                    ${availableQuantity}
                                </span>
                            </div>
                            <div class="product-detail">
                                <label>Total</label>
                                <span>${p.quantity}</span>
                            </div>
                            <div class="product-detail">
                                <label>Mínimo</label>
                                <span>${p.minQuantity}</span>
                            </div>
                        </div>
                        
                        <div class="product-actions">
                            <button class="edit-btn" onclick="editProduct(${p.id})">✏️ Editar</button>
                            <button class="loan-btn" onclick="openLoanModal(${p.id})">🔧 Emprestar</button>
                            <button class="delete-btn" onclick="deleteProduct(${p.id})">🗑️ Excluir</button>
                        </div>
                    </div>
                `;
            }).join('');
        }

        function loadProducts() {
            filterProducts();
        }

        function openProductModal() {
            document.getElementById('modalTitle').textContent = 'Novo Item';
            document.getElementById('productName').value = '';
            document.getElementById('productLocal').value = '';
            document.getElementById('productCategory').value = '';
            document.getElementById('productQuantity').value = '';
            document.getElementById('productMinQuantity').value = '';
            document.getElementById('editingProductId').value = '';
            document.getElementById('productModal').classList.add('active');
        }

        function editProduct(id) {
            const product = products.find(p => p.id === id);
            if (product) {
                document.getElementById('modalTitle').textContent = 'Editar Item';
                document.getElementById('productName').value = product.name;
                document.getElementById('productLocal').value = product.local;
                document.getElementById('productCategory').value = product.category;
                document.getElementById('productQuantity').value = product.quantity;
                document.getElementById('productMinQuantity').value = product.minQuantity;
                document.getElementById('editingProductId').value = id;
                document.getElementById('productModal').classList.add('active');
            }
        }

        function saveProduct() {
            const id = document.getElementById('editingProductId').value;
            const productData = {
                name: document.getElementById('productName').value,
                local: document.getElementById('productLocal').value,
                category: document.getElementById('productCategory').value,
                quantity: parseInt(document.getElementById('productQuantity').value) || 0,
                minQuantity: parseInt(document.getElementById('productMinQuantity').value) || 0,
                date: new Date().toISOString().split('T')[0]
            };
            
            if (!productData.name || !productData.category || !productData.local) {
                alert('Preencha todos os campos obrigatórios!');
                return;
            }
            
            if (id) {
                const index = products.findIndex(p => p.id == id);
                products[index] = { ...products[index], ...productData };
            } else {
                productData.id = Date.now();
                products.push(productData);
            }
            
            localStorage.setItem('products', JSON.stringify(products));
            closeModal('productModal');
            loadProducts();
            updateDashboard();
            loadProductSelect();
            loadLoanProductSelect();
            loadCategoryFilter();
        }

        function deleteProduct(id) {
            if (confirm('Tem certeza que deseja excluir este item?')) {
                products = products.filter(p => p.id !== id);
                movements = movements.filter(m => m.productId !== id);
                loans = loans.filter(l => l.productId !== id);
                
                localStorage.setItem('products', JSON.stringify(products));
                localStorage.setItem('movements', JSON.stringify(movements));
                localStorage.setItem('loans', JSON.stringify(loans));
                
                loadProducts();
                updateDashboard();
                loadProductSelect();
                loadLoanProductSelect();
                loadCategoryFilter();
            }
        }

        // ============================================
        // FUNÇÕES DE MOVIMENTAÇÕES
        // ============================================
        function openEntryModal() {
            document.getElementById('movementModalTitle').textContent = 'Entrada de Mercadoria';
            document.getElementById('movementType').value = 'entry';
            document.getElementById('movementQuantity').value = '';
            document.getElementById('movementDateField').value = new Date().toISOString().split('T')[0];
            document.getElementById('movementObservation').value = '';
            document.getElementById('movementModal').classList.add('active');
        }

        function openExitModal() {
            document.getElementById('movementModalTitle').textContent = 'Saída de Mercadoria';
            document.getElementById('movementType').value = 'exit';
            document.getElementById('movementQuantity').value = '';
            document.getElementById('movementDateField').value = new Date().toISOString().split('T')[0];
            document.getElementById('movementObservation').value = '';
            document.getElementById('movementModal').classList.add('active');
        }

        function loadProductSelect() {
            const select = document.getElementById('movementProduct');
            select.innerHTML = '<option value="">Selecione um item *</option>' +
                products.map(p => `<option value="${p.id}">${p.name} - ${p.local} (Estoque: ${p.quantity})</option>`).join('');
        }

        function saveMovement() {
            const productId = parseInt(document.getElementById('movementProduct').value);
            const quantity = parseInt(document.getElementById('movementQuantity').value);
            const date = document.getElementById('movementDateField').value;
            const observation = document.getElementById('movementObservation').value;
            const type = document.getElementById('movementType').value;
            
            if (!productId || !quantity || !date) {
                alert('Preencha todos os campos obrigatórios!');
                return;
            }
            
            const product = products.find(p => p.id === productId);
            
            if (type === 'exit' && quantity > product.quantity) {
                alert('Quantidade insuficiente em estoque!');
                return;
            }
            
            if (type === 'entry') {
                product.quantity += quantity;
            } else {
                product.quantity -= quantity;
            }
            
            const movement = {
                id: Date.now(),
                productId,
                productName: product.name,
                productLocal: product.local,
                category: product.category,
                type,
                quantity,
                date,
                observation,
                timestamp: new Date().toISOString()
            };
            
            movements.push(movement);
            
            localStorage.setItem('products', JSON.stringify(products));
            localStorage.setItem('movements', JSON.stringify(movements));
            
            closeModal('movementModal');
            loadProducts();
            updateDashboard();
            loadMovements();
            loadProductSelect();
            loadLoanProductSelect();
            
            alert('✅ Movimentação registrada com sucesso!');
        }

        // ============================================
        // FUNÇÕES DE EMPRÉSTIMOS
        // ============================================
        function openLoanModal(productId = null) {
            document.getElementById('loanUserName').value = '';
            document.getElementById('loanQuantity').value = '1';
            document.getElementById('loanDate').value = new Date().toISOString().split('T')[0];
            document.getElementById('loanObservation').value = '';
            
            if (productId) {
                document.getElementById('loanProduct').value = productId;
            }
            
            document.getElementById('loanModal').classList.add('active');
        }

        function loadLoanProductSelect() {
            const select = document.getElementById('loanProduct');
            const activeLoans = loans.filter(l => !l.returned);
            
            select.innerHTML = '<option value="">Selecione um item *</option>' +
                products.map(p => {
                    const loanedQuantity = activeLoans
                        .filter(l => l.productId === p.id)
                        .reduce((sum, l) => sum + l.quantity, 0);
                    const availableQuantity = p.quantity - loanedQuantity;
                    
                    return `<option value="${p.id}" ${availableQuantity <= 0 ? 'disabled' : ''}>
                        ${p.name} - ${p.local} (Disponível: ${availableQuantity})
                    </option>`;
                }).join('');
        }

        function saveLoan() {
            const userName = document.getElementById('loanUserName').value;
            const productId = parseInt(document.getElementById('loanProduct').value);
            const quantity = parseInt(document.getElementById('loanQuantity').value);
            const date = document.getElementById('loanDate').value;
            const observation = document.getElementById('loanObservation').value;
            
            if (!userName || !productId || !quantity || !date) {
                alert('Preencha todos os campos obrigatórios!');
                return;
            }
            
            const product = products.find(p => p.id === productId);
            const activeLoans = loans.filter(l => !l.returned && l.productId === productId);
            const loanedQuantity = activeLoans.reduce((sum, l) => sum + l.quantity, 0);
            const availableQuantity = product.quantity - loanedQuantity;
            
            if (quantity > availableQuantity) {
                alert(`Quantidade indisponível! Disponível: ${availableQuantity}`);
                return;
            }
            
            const loan = {
                id: Date.now(),
                userId: currentUser?.name || 'Sistema',
                userName,
                productId,
                productName: product.name,
                productLocal: product.local,
                quantity,
                date,
                observation,
                returned: false,
                timestamp: new Date().toISOString()
            };
            
            loans.push(loan);
            
            const movement = {
                id: Date.now() + 1,
                productId,
                productName: product.name,
                productLocal: product.local,
                category: product.category,
                type: 'loan',
                quantity,
                date,
                observation: `Emprestado para ${userName} - ${observation}`,
                timestamp: new Date().toISOString()
            };
            
            movements.push(movement);
            
            localStorage.setItem('loans', JSON.stringify(loans));
            localStorage.setItem('movements', JSON.stringify(movements));
            
            closeModal('loanModal');
            loadProducts();
            updateDashboard();
            loadMovements();
            loadProductSelect();
            loadLoanProductSelect();
            
            alert(`✅ Empréstimo registrado para ${userName}!`);
        }

        function openReturnModal(loanId) {
            const loan = loans.find(l => l.id === loanId);
            if (loan) {
                document.getElementById('returnInfo').innerHTML = `
                    <strong>Devolução de:</strong><br>
                    👤 <strong>${loan.userName}</strong><br>
                    🔧 ${loan.productName}<br>
                    📍 ${loan.productLocal}<br>
                    📦 Quantidade: ${loan.quantity}
                `;
                document.getElementById('returnDate').value = new Date().toISOString().split('T')[0];
                document.getElementById('returnObservation').value = '';
                document.getElementById('returnLoanId').value = loanId;
                document.getElementById('returnModal').classList.add('active');
            }
        }

        function saveReturn() {
            const loanId = parseInt(document.getElementById('returnLoanId').value);
            const returnDate = document.getElementById('returnDate').value;
            const observation = document.getElementById('returnObservation').value;
            
            const loanIndex = loans.findIndex(l => l.id === loanId);
            if (loanIndex === -1) return;
            
            loans[loanIndex].returned = true;
            loans[loanIndex].returnDate = returnDate;
            
            const movement = {
                id: Date.now(),
                productId: loans[loanIndex].productId,
                productName: loans[loanIndex].productName,
                productLocal: loans[loanIndex].productLocal,
                category: loans[loanIndex].category,
                type: 'return',
                quantity: loans[loanIndex].quantity,
                date: returnDate,
                observation: `Devolvido por ${loans[loanIndex].userName} - ${observation}`,
                timestamp: new Date().toISOString()
            };
            
            movements.push(movement);
            
            localStorage.setItem('loans', JSON.stringify(loans));
            localStorage.setItem('movements', JSON.stringify(movements));
            
            closeModal('returnModal');
            loadProducts();
            updateDashboard();
            loadMovements();
            loadProductSelect();
            loadLoanProductSelect();
            
            alert('✅ Devolução registrada com sucesso!');
        }

        // ============================================
        // FUNÇÕES DE MOVIMENTAÇÕES (LISTA)
        // ============================================
        function loadMovements() {
            const list = document.getElementById('movementsList');
            const selectedDate = document.getElementById('movementDate').value;
            
            let filteredMovements = movements;
            if (selectedDate) {
                filteredMovements = movements.filter(m => m.date === selectedDate);
            }
            
            if (filteredMovements.length === 0) {
                list.innerHTML = '<p style="text-align: center; padding: 30px;">📭 Nenhuma movimentação encontrada</p>';
                return;
            }
            
            list.innerHTML = filteredMovements.sort((a, b) => new Date(b.timestamp) - new Date(a.timestamp))
                .map(m => {
                    let typeColor = '#27ae60';
                    let typeIcon = '📥';
                    let typeText = 'Entrada';
                    
                    if (m.type === 'exit') {
                        typeColor = '#e74c3c';
                        typeIcon = '📤';
                        typeText = 'Saída';
                    } else if (m.type === 'loan') {
                        typeColor = '#17a2b8';
                        typeIcon = '🔧';
                        typeText = 'Empréstimo';
                    } else if (m.type === 'return') {
                        typeColor = '#28a745';
                        typeIcon = '↩️';
                        typeText = 'Devolução';
                    }
                    
                    return `
                        <div class="product-card">
                            <div class="product-header">
                                <span class="product-name">${m.productName}</span>
                                <span style="color: ${typeColor}; font-weight: 600;">
                                    ${typeIcon} ${typeText}
                                </span>
                            </div>
                            <span class="product-local">📍 ${m.productLocal} | 🏷️ ${m.category}</span>
                            
                            <div class="product-details">
                                <div class="product-detail">
                                    <label>Quantidade</label>
                                    <span>${m.quantity}</span>
                                </div>
                                <div class="product-detail">
                                    <label>Data</label>
                                    <span>${m.date}</span>
                                </div>
                            </div>
                            ${m.observation ? `<small>📝 ${m.observation}</small>` : ''}
                        </div>
                    `;
                }).join('');
        }

        function filterMovements() {
            loadMovements();
        }

        // ============================================
        // FUNÇÕES DE NAVEGAÇÃO E UTILITÁRIOS
        // ============================================
        function changeScreen(screen) {
            document.querySelectorAll('.menu-item').forEach(item => item.classList.remove('active'));
            event.target.closest('.menu-item').classList.add('active');
            
            document.getElementById('dashboardScreen').style.display = 'none';
            document.getElementById('productsScreen').style.display = 'none';
            document.getElementById('movementsScreen').style.display = 'none';
            document.getElementById('profileScreen').style.display = 'none';
            
            document.getElementById(screen + 'Screen').style.display = 'block';
            
            const titles = {
                'dashboard': '📊 Dashboard',
                'products': '📦 Itens do Estoque',
                'movements': '📋 Movimentações',
                'profile': '👤 Meu Perfil'
            };
            document.getElementById('screenTitle').textContent = titles[screen];
            
            if (screen === 'movements') {
                loadMovements();
                document.getElementById('movementDate').value = '';
            } else if (screen === 'products') {
                loadProducts();
                document.getElementById('searchProduct').value = '';
                currentCategory = 'todos';
                loadCategoryFilter();
            }
        }

        function closeModal(modalId) {
            document.getElementById(modalId).classList.remove('active');
        }

        function logout() {
            currentUser = null;
            document.getElementById('loginScreen').style.display = 'block';
            document.getElementById('appScreen').style.display = 'none';
        }

        // Inicialização
        if (Notification.permission !== 'granted' && Notification.permission !== 'denied') {
            Notification.requestPermission();
        }

        window.onclick = function(event) {
            if (event.target.classList.contains('modal')) {
                event.target.classList.remove('active');
            }
        }
    </script>
</body>
</html>
