<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
    <title>HWT Manutenção - Controle de Estoque</title>
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
            margin-top: 5px;
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

        .dashboard {
            padding: 15px;
        }

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
        }

        .stat-card h3 {
            color: #7f8c8d;
            font-size: 14px;
            margin-bottom: 10px;
        }

        .stat-card .number {
            font-size: 28px;
            font-weight: bold;
            color: #2c3e50;
        }

        .alert-card {
            background: #fff3cd;
            border: 1px solid #ffc107;
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 20px;
        }

        .alert-card h3 {
            color: #856404;
            margin-bottom: 10px;
        }

        .alert-item {
            background: white;
            padding: 10px;
            border-radius: 8px;
            margin-bottom: 8px;
            border-left: 4px solid #dc3545;
        }

        .loan-alert {
            background: #cce5ff;
            border: 1px solid #17a2b8;
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 20px;
        }

        .loan-alert h3 {
            color: #0c5460;
            margin-bottom: 10px;
        }

        .loan-item {
            background: white;
            padding: 12px;
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
        }

        .return-btn {
            background-color: #28a745;
            color: white;
            border: none;
            padding: 8px 15px;
            border-radius: 5px;
            cursor: pointer;
            font-weight: 600;
            margin-top: 8px;
            width: 100%;
        }

        .movements-summary {
            background: white;
            padding: 15px;
            border-radius: 10px;
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
            border-top: 1px solid #e0e0e0;
            max-width: 500px;
            margin: 0 auto;
            width: 100%;
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
            padding: 5px;
        }

        .menu-item.active {
            color: #3498db;
        }

        .menu-item span {
            font-size: 20px;
            margin-bottom: 4px;
        }

        /* Lista de Produtos */
        .products-list, .movements-list {
            padding: 15px;
        }

        .search-box {
            width: 100%;
            padding: 12px;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            font-size: 16px;
            margin-bottom: 15px;
        }

        .category-filter {
            display: flex;
            gap: 10px;
            margin-bottom: 15px;
            overflow-x: auto;
            padding: 5px 0;
        }

        .category-filter button {
            padding: 8px 15px;
            border: none;
            border-radius: 20px;
            background: white;
            color: #2c3e50;
            font-weight: 600;
            cursor: pointer;
            white-space: nowrap;
            box-shadow: 0 1px 3px rgba(0,0,0,0.1);
        }

        .category-filter button.active {
            background: #3498db;
            color: white;
        }

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
        }

        .action-buttons {
            display: flex;
            gap: 10px;
            margin-bottom: 15px;
        }

        .action-buttons button {
            flex: 1;
            padding: 15px;
            border: none;
            border-radius: 10px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
        }

        .loan-action-btn {
            background-color: #17a2b8;
            color: white;
        }

        .product-card {
            background: white;
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 10px;
            box-shadow: 0 1px 3px rgba(0,0,0,0.1);
        }

        .product-card.low-stock {
            border-left: 4px solid #dc3545;
        }

        .product-card.on-loan {
            border-left: 4px solid #17a2b8;
            background-color: #e1f5fe;
        }

        .product-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
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
            padding: 3px 8px;
            border-radius: 12px;
        }

        .product-local {
            color: #7f8c8d;
            font-size: 12px;
            background: #e8f4fd;
            padding: 3px 8px;
            border-radius: 12px;
            display: inline-block;
            margin-bottom: 8px;
        }

        .loan-badge {
            background-color: #17a2b8;
            color: white;
            padding: 3px 8px;
            border-radius: 12px;
            font-size: 11px;
            font-weight: 600;
            display: inline-block;
            margin-bottom: 8px;
        }

        .product-details {
            display: flex;
            gap: 15px;
            margin: 10px 0;
        }

        .product-detail {
            flex: 1;
        }

        .product-detail label {
            font-size: 12px;
            color: #7f8c8d;
            display: block;
        }

        .product-detail span {
            font-size: 16px;
            font-weight: 600;
        }

        .product-actions {
            display: flex;
            gap: 10px;
            border-top: 1px solid #e0e0e0;
            padding-top: 10px;
        }

        .product-actions button {
            flex: 1;
            padding: 8px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-weight: 600;
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

        /* Modal */
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
        }

        .modal.active {
            display: flex;
        }

        .modal-content {
            background: white;
            padding: 20px;
            border-radius: 15px;
            max-width: 90%;
            width: 400px;
            max-height: 80vh;
            overflow-y: auto;
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .modal-header h2 {
            color: #2c3e50;
            font-size: 20px;
        }

        .close-btn {
            background: none;
            border: none;
            font-size: 24px;
            cursor: pointer;
            color: #7f8c8d;
        }

        .modal-form {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .modal-form input, .modal-form select, .modal-form textarea {
            padding: 12px;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            font-size: 16px;
        }

        .submit-btn {
            background-color: #27ae60;
            color: white;
            padding: 15px;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
        }

        .filter-section {
            background: white;
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 15px;
        }

        .filter-section input {
            width: 100%;
            padding: 12px;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            font-size: 16px;
        }

        .profile-section {
            padding: 15px;
        }

        .profile-card {
            background: white;
            padding: 20px;
            border-radius: 10px;
            text-align: center;
            margin-bottom: 20px;
        }

        .profile-avatar {
            font-size: 60px;
            margin-bottom: 10px;
        }

        .profile-name {
            font-size: 20px;
            font-weight: 600;
            color: #2c3e50;
        }

        .logout-btn {
            background-color: #e74c3c;
            color: white;
            border: none;
            padding: 12px;
            border-radius: 8px;
            font-size: 16px;
            font-weight: 600;
            width: 100%;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <!-- Tela de Login -->
    <div id="loginScreen" class="login-container">
        <div class="login-header">
            <h1>🔧 HWT Manutenção</h1>
            <p>Controle de Estoque e Empréstimos</p>
        </div>
        
        <div class="login-form">
            <div class="input-group">
                <label>Usuário</label>
                <input type="text" id="username" placeholder="Digite o usuário" value="admin">
            </div>
            
            <div class="input-group">
                <label>Senha</label>
                <input type="password" id="password" placeholder="Digite a senha" value="hwtmanutençao">
            </div>
            
            <button class="login-btn" onclick="login()">Entrar</button>
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
                </div>
                <div class="stat-card">
                    <h3>📊 Unidades</h3>
                    <div class="number" id="totalStock">0</div>
                </div>
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
                <h3>📋 Movimentações de Hoje</h3>
                <div style="margin-top: 15px;">
                    <p>Entradas: <strong id="todayEntries">0</strong></p>
                    <p>Saídas: <strong id="todayExits">0</strong></p>
                    <p>Empréstimos: <strong id="todayLoans">0</strong></p>
                </div>
            </div>
        </div>

        <!-- Produtos -->
        <div id="productsScreen" style="display: none;">
            <div class="products-list">
                <button class="add-btn" onclick="openProductModal()">+ Novo Item</button>
                
                <input type="text" class="search-box" id="searchProduct" placeholder="🔍 Buscar item..." onkeyup="filterProducts()">
                
                <div class="category-filter" id="categoryFilter"></div>
                
                <div class="action-buttons">
                    <button class="loan-action-btn" onclick="openLoanModal()">🔧 Novo Empréstimo</button>
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
                    <button class="add-btn" onclick="openEntryModal()">📥 Entrada</button>
                    <button class="add-btn" onclick="openExitModal()" style="background-color: #e74c3c;">📤 Saída</button>
                </div>
                
                <div id="movementsList"></div>
            </div>
        </div>

        <!-- Perfil -->
        <div id="profileScreen" style="display: none;">
            <div class="profile-section">
                <div class="profile-card">
                    <div class="profile-avatar">👤</div>
                    <div class="profile-name" id="profileName">admin</div>
                    <div class="profile-email">hwtmanutençao</div>
                </div>
                
                <button class="logout-btn" onclick="logout()">Sair da conta</button>
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
                    <option value="Jardim">🌱 Jardim</option>
                    <option value="Elétrica">⚡ Elétrica</option>
                    <option value="Ferramentas">🔨 Ferramentas</option>
                    <option value="EPI">🪖 EPI</option>
                    <option value="Hidráulica">💧 Hidráulica</option>
                    <option value="Geral">📋 Geral</option>
                </select>
                
                <input type="number" id="productQuantity" placeholder="Quantidade *" required>
                <input type="number" id="productMinQuantity" placeholder="Quantidade mínima *" required>
                
                <input type="hidden" id="editingProductId">
                <button class="submit-btn" onclick="saveProduct()">Salvar Item</button>
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
                
                <input type="number" id="movementQuantity" placeholder="Quantidade *" required>
                <input type="date" id="movementDateField" required>
                <textarea id="movementObservation" placeholder="Observação (opcional)"></textarea>
                
                <input type="hidden" id="movementType">
                <button class="submit-btn" onclick="saveMovement()">Registrar</button>
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
                
                <button class="submit-btn" onclick="saveLoan()">Registrar Empréstimo</button>
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
                    <p id="returnInfo"></p>
                </div>
                
                <input type="date" id="returnDate" required>
                <textarea id="returnObservation" placeholder="Observação (opcional)"></textarea>
                
                <input type="hidden" id="returnLoanId">
                <button class="submit-btn" onclick="saveReturn()">Confirmar Devolução</button>
            </div>
        </div>
    </div>

    <script>
        // DADOS INICIAIS - TODOS OS ITENS (COM GERAL, SEM OUTROS)
        let products = JSON.parse(localStorage.getItem('products')) || [
            // 🌱 JARDIM
            { id: 1, name: 'Tesoura de Poda', local: 'Prateleira A1', category: 'Jardim', quantity: 8, minQuantity: 3 },
            { id: 2, name: 'Pá (Vanga)', local: 'Prateleira A1', category: 'Jardim', quantity: 5, minQuantity: 2 },
            { id: 3, name: 'Pá de Mão', local: 'Gaveta 1', category: 'Jardim', quantity: 10, minQuantity: 4 },
            { id: 4, name: 'Enxada', local: 'Prateleira A2', category: 'Jardim', quantity: 4, minQuantity: 2 },
            { id: 5, name: 'Ancinho (Rastelo)', local: 'Prateleira A2', category: 'Jardim', quantity: 6, minQuantity: 2 },
            { id: 6, name: 'Cortador de Grama Elétrico', local: 'Galpão Externo', category: 'Jardim', quantity: 2, minQuantity: 1 },
            { id: 7, name: 'Mangueira 30m', local: 'Prateleira A3', category: 'Jardim', quantity: 5, minQuantity: 2 },
            { id: 8, name: 'Regador 5L', local: 'Prateleira A3', category: 'Jardim', quantity: 4, minQuantity: 2 },
            { id: 9, name: 'Carrinho de Mão', local: 'Estoque Externo', category: 'Jardim', quantity: 3, minQuantity: 1 },
            { id: 10, name: 'Roçadeira', local: 'Galpão Externo', category: 'Jardim', quantity: 2, minQuantity: 1 },
            
            // ⚡ ELÉTRICA
            { id: 11, name: 'Alicate Universal', local: 'Gaveta 10', category: 'Elétrica', quantity: 8, minQuantity: 3 },
            { id: 12, name: 'Alicate de Corte', local: 'Gaveta 10', category: 'Elétrica', quantity: 8, minQuantity: 3 },
            { id: 13, name: 'Alicate Desencapador de Fios', local: 'Gaveta 10', category: 'Elétrica', quantity: 5, minQuantity: 2 },
            { id: 14, name: 'Chave de Fenda (Kit 6 peças)', local: 'Gaveta 11', category: 'Elétrica', quantity: 6, minQuantity: 2 },
            { id: 15, name: 'Chave Phillips (Kit 6 peças)', local: 'Gaveta 11', category: 'Elétrica', quantity: 6, minQuantity: 2 },
            { id: 16, name: 'Chave de Teste (Detector de Tensão)', local: 'Gaveta 12', category: 'Elétrica', quantity: 4, minQuantity: 2 },
            { id: 17, name: 'Multímetro Digital', local: 'Gaveta 12', category: 'Elétrica', quantity: 3, minQuantity: 1 },
            { id: 18, name: 'Fita Isolante (rolo)', local: 'Gaveta 12', category: 'Elétrica', quantity: 20, minQuantity: 8 },
            
            // 🔨 FERRAMENTAS
            { id: 19, name: 'Martelo', local: 'Prateleira B1', category: 'Ferramentas', quantity: 8, minQuantity: 3 },
            { id: 20, name: 'Trena 5m', local: 'Gaveta 13', category: 'Ferramentas', quantity: 10, minQuantity: 4 },
            { id: 21, name: 'Trena 10m', local: 'Gaveta 13', category: 'Ferramentas', quantity: 5, minQuantity: 2 },
            { id: 22, name: 'Chave Inglesa 8"', local: 'Gaveta 14', category: 'Ferramentas', quantity: 4, minQuantity: 2 },
            { id: 23, name: 'Chave Inglesa 12"', local: 'Gaveta 14', category: 'Ferramentas', quantity: 3, minQuantity: 1 },
            { id: 24, name: 'Furadeira/Parafusadeira', local: 'Armário C1', category: 'Ferramentas', quantity: 4, minQuantity: 2 },
            { id: 25, name: 'Furadeira de Impacto', local: 'Armário C1', category: 'Ferramentas', quantity: 3, minQuantity: 1 },
            { id: 26, name: 'Estilete', local: 'Gaveta 15', category: 'Ferramentas', quantity: 12, minQuantity: 4 },
            { id: 27, name: 'Nível de Bolha 60cm', local: 'Prateleira B2', category: 'Ferramentas', quantity: 5, minQuantity: 2 },
            { id: 28, name: 'Jogo de Chaves Allen (métrico)', local: 'Gaveta 15', category: 'Ferramentas', quantity: 4, minQuantity: 2 },
            { id: 29, name: 'Jogo de Chaves Allen (polegada)', local: 'Gaveta 15', category: 'Ferramentas', quantity: 3, minQuantity: 1 },
            { id: 30, name: 'Lanterna', local: 'Prateleira B3', category: 'Ferramentas', quantity: 6, minQuantity: 2 },
            { id: 31, name: 'Lanterna de Cabeça', local: 'Prateleira B3', category: 'Ferramentas', quantity: 4, minQuantity: 2 },
            
            // 🪖 EPI
            { id: 32, name: 'Luva de Raspa (par)', local: 'Armário D1', category: 'EPI', quantity: 12, minQuantity: 5 },
            { id: 33, name: 'Óculos de Proteção', local: 'Armário D1', category: 'EPI', quantity: 15, minQuantity: 6 },
            { id: 34, name: 'Protetor Auricular', local: 'Armário D1', category: 'EPI', quantity: 8, minQuantity: 3 },
            { id: 35, name: 'Capacete de Segurança', local: 'Armário D1', category: 'EPI', quantity: 10, minQuantity: 4 },
            
            // 💧 HIDRÁULICA
            { id: 36, name: 'Tubo PVC 25mm (barra 6m)', local: 'Cantinho Tubos', category: 'Hidráulica', quantity: 10, minQuantity: 4 },
            { id: 37, name: 'Joelho 90° 25mm', local: 'Caixa 5', category: 'Hidráulica', quantity: 30, minQuantity: 10 },
            { id: 38, name: 'Fita Veda-rosca', local: 'Gaveta 16', category: 'Hidráulica', quantity: 15, minQuantity: 5 },
            { id: 39, name: 'Cola para PVC', local: 'Gaveta 16', category: 'Hidráulica', quantity: 8, minQuantity: 3 },
            
            // 📋 GERAL (itens diversos)
            { id: 40, name: 'Cadeado Médio', local: 'Gaveta 17', category: 'Geral', quantity: 8, minQuantity: 3 },
            { id: 41, name: 'Cadeado Grande', local: 'Gaveta 17', category: 'Geral', quantity: 5, minQuantity: 2 },
            { id: 42, name: 'Corda Nylon 10mm (rolo)', local: 'Prateleira E1', category: 'Geral', quantity: 4, minQuantity: 2 },
            { id: 43, name: 'Abraçadeira Nylon (pacote)', local: 'Gaveta 18', category: 'Geral', quantity: 6, minQuantity: 2 },
            { id: 44, name: 'Lona Plástica 4x5m', local: 'Prateleira E2', category: 'Geral', quantity: 3, minQuantity: 1 },
            { id: 45, name: 'Fita Crepe (rolo)', local: 'Gaveta 18', category: 'Geral', quantity: 12, minQuantity: 4 }
        ];
        
        let movements = JSON.parse(localStorage.getItem('movements')) || [];
        let loans = JSON.parse(localStorage.getItem('loans')) || [];
        let currentUser = null;
        let currentCategory = 'todos';

        // Login fixo
        function login() {
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            
            if (username === 'admin' && password === 'hwtmanutençao') {
                currentUser = { name: 'admin' };
                document.getElementById('loginScreen').style.display = 'none';
                document.getElementById('appScreen').style.display = 'block';
                document.getElementById('profileName').textContent = 'admin';
                updateDashboard();
                loadProducts();
                loadCategoryFilter();
                loadProductSelect();
                loadLoanProductSelect();
            } else {
                alert('Usuário ou senha inválidos!');
            }
        }

        function logout() {
            currentUser = null;
            document.getElementById('loginScreen').style.display = 'block';
            document.getElementById('appScreen').style.display = 'none';
        }

        function updateDashboard() {
            document.getElementById('totalProducts').textContent = products.length;
            
            const totalStock = products.reduce((sum, p) => sum + p.quantity, 0);
            document.getElementById('totalStock').textContent = totalStock;
            
            // Alertas de estoque baixo
            const lowStock = products.filter(p => p.quantity <= p.minQuantity);
            const lowStockList = document.getElementById('lowStockList');
            
            if (lowStock.length > 0) {
                lowStockList.innerHTML = lowStock.map(p => `
                    <div class="alert-item">
                        <strong>${p.name}</strong> - ${p.quantity} / ${p.minQuantity}
                        <br><small>📍 ${p.local}</small>
                    </div>
                `).join('');
            } else {
                lowStockList.innerHTML = '<p>✅ Todos os itens com estoque adequado</p>';
            }
            
            // Alertas de empréstimos
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
                        <div><strong>${l.productName}</strong></div>
                        <div>📍 ${l.productLocal}</div>
                        <div>Quantidade: ${l.quantity}</div>
                        <button class="return-btn" onclick="openReturnModal(${l.id})">↩️ Devolver</button>
                    </div>
                `).join('');
            } else {
                loanAlert.style.display = 'none';
            }
            
            const today = new Date().toISOString().split('T')[0];
            const todayMovements = movements.filter(m => m.date === today);
            
            document.getElementById('todayEntries').textContent = todayMovements
                .filter(m => m.type === 'entry').reduce((sum, m) => sum + m.quantity, 0);
            
            document.getElementById('todayExits').textContent = todayMovements
                .filter(m => m.type === 'exit').reduce((sum, m) => sum + m.quantity, 0);
                
            document.getElementById('todayLoans').textContent = loans.filter(l => l.date === today && !l.returned).length;
        }

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
                                     p.local.toLowerCase().includes(searchTerm);
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
                            <button class="edit-btn" onclick="editProduct(${p.id})">Editar</button>
                            <button class="loan-btn" onclick="openLoanModal(${p.id})">Emprestar</button>
                            <button class="delete-btn" onclick="deleteProduct(${p.id})">Excluir</button>
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
                minQuantity: parseInt(document.getElementById('productMinQuantity').value) || 0
            };
            
            if (!productData.name || !productData.local || !productData.category) {
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
            loadCategoryFilter();
            loadProductSelect();
            loadLoanProductSelect();
        }

        function deleteProduct(id) {
            if (confirm('Tem certeza que deseja excluir este item?')) {
                products = products.filter(p => p.id !== id);
                localStorage.setItem('products', JSON.stringify(products));
                loadProducts();
                updateDashboard();
                loadCategoryFilter();
            }
        }

        function openEntryModal() {
            document.getElementById('movementModalTitle').textContent = 'Entrada';
            document.getElementById('movementType').value = 'entry';
            document.getElementById('movementQuantity').value = '';
            document.getElementById('movementDateField').value = new Date().toISOString().split('T')[0];
            document.getElementById('movementObservation').value = '';
            document.getElementById('movementModal').classList.add('active');
        }

        function openExitModal() {
            document.getElementById('movementModalTitle').textContent = 'Saída';
            document.getElementById('movementType').value = 'exit';
            document.getElementById('movementQuantity').value = '';
            document.getElementById('movementDateField').value = new Date().toISOString().split('T')[0];
            document.getElementById('movementObservation').value = '';
            document.getElementById('movementModal').classList.add('active');
        }

        function loadProductSelect() {
            const select = document.getElementById('movementProduct');
            select.innerHTML = '<option value="">Selecione um item *</option>' +
                products.map(p => `<option value="${p.id}">${p.name} (${p.quantity})</option>`).join('');
        }

        function saveMovement() {
            const productId = parseInt(document.getElementById('movementProduct').value);
            const quantity = parseInt(document.getElementById('movementQuantity').value);
            const date = document.getElementById('movementDateField').value;
            const type = document.getElementById('movementType').value;
            
            if (!productId || !quantity || !date) {
                alert('Preencha todos os campos!');
                return;
            }
            
            const product = products.find(p => p.id === productId);
            
            if (type === 'exit' && quantity > product.quantity) {
                alert('Quantidade insuficiente!');
                return;
            }
            
            if (type === 'entry') product.quantity += quantity;
            else product.quantity -= quantity;
            
            movements.push({
                id: Date.now(),
                productId,
                productName: product.name,
                quantity,
                date,
                type
            });
            
            localStorage.setItem('products', JSON.stringify(products));
            localStorage.setItem('movements', JSON.stringify(movements));
            
            closeModal('movementModal');
            loadProducts();
            updateDashboard();
            loadProductSelect();
            loadLoanProductSelect();
        }

        function loadLoanProductSelect() {
            const select = document.getElementById('loanProduct');
            const activeLoans = loans.filter(l => !l.returned);
            
            select.innerHTML = '<option value="">Selecione um item *</option>' +
                products.map(p => {
                    const loaned = activeLoans.filter(l => l.productId === p.id)
                        .reduce((sum, l) => sum + l.quantity, 0);
                    const available = p.quantity - loaned;
                    
                    return `<option value="${p.id}" ${available <= 0 ? 'disabled' : ''}>
                        ${p.name} (Disponível: ${available})
                    </option>`;
                }).join('');
        }

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

        function saveLoan() {
            const userName = document.getElementById('loanUserName').value;
            const productId = parseInt(document.getElementById('loanProduct').value);
            const quantity = parseInt(document.getElementById('loanQuantity').value);
            const date = document.getElementById('loanDate').value;
            const observation = document.getElementById('loanObservation').value;
            
            if (!userName || !productId || !quantity || !date) {
                alert('Preencha todos os campos!');
                return;
            }
            
            const product = products.find(p => p.id === productId);
            
            loans.push({
                id: Date.now(),
                userName,
                productId,
                productName: product.name,
                productLocal: product.local,
                quantity,
                date,
                observation,
                returned: false
            });
            
            movements.push({
                id: Date.now() + 1,
                productId,
                productName: product.name,
                quantity,
                date,
                type: 'loan',
                observation: `Emprestado para ${userName}`
            });
            
            localStorage.setItem('loans', JSON.stringify(loans));
            localStorage.setItem('movements', JSON.stringify(movements));
            
            closeModal('loanModal');
            loadProducts();
            updateDashboard();
            loadLoanProductSelect();
        }

        function openReturnModal(loanId) {
            const loan = loans.find(l => l.id === loanId);
            if (loan) {
                document.getElementById('returnInfo').innerHTML = `
                    <strong>Devolução:</strong><br>
                    👤 ${loan.userName}<br>
                    🔧 ${loan.productName}<br>
                    📦 Quantidade: ${loan.quantity}
                `;
                document.getElementById('returnDate').value = new Date().toISOString().split('T')[0];
                document.getElementById('returnLoanId').value = loanId;
                document.getElementById('returnModal').classList.add('active');
            }
        }

        function saveReturn() {
            const loanId = parseInt(document.getElementById('returnLoanId').value);
            const returnDate = document.getElementById('returnDate').value;
            
            const loanIndex = loans.findIndex(l => l.id === loanId);
            if (loanIndex === -1) return;
            
            loans[loanIndex].returned = true;
            
            movements.push({
                id: Date.now(),
                productId: loans[loanIndex].productId,
                productName: loans[loanIndex].productName,
                quantity: loans[loanIndex].quantity,
                date: returnDate,
                type: 'return',
                observation: `Devolvido por ${loans[loanIndex].userName}`
            });
            
            localStorage.setItem('loans', JSON.stringify(loans));
            localStorage.setItem('movements', JSON.stringify(movements));
            
            closeModal('returnModal');
            loadProducts();
            updateDashboard();
            loadLoanProductSelect();
        }

        function loadMovements() {
            const date = document.getElementById('movementDate').value;
            let filtered = movements;
            if (date) filtered = movements.filter(m => m.date === date);
            
            document.getElementById('movementsList').innerHTML = filtered.sort((a,b)=>b.id-a.id)
                .map(m => {
                    let icon = m.type === 'entry' ? '📥' : m.type === 'exit' ? '📤' : m.type === 'loan' ? '🔧' : '↩️';
                    let color = m.type === 'entry' ? '#27ae60' : m.type === 'exit' ? '#e74c3c' : '#17a2b8';
                    
                    return `
                        <div class="product-card">
                            <div style="display: flex; justify-content: space-between;">
                                <strong>${m.productName}</strong>
                                <span style="color: ${color}">${icon} ${m.type}</span>
                            </div>
                            <div>Quantidade: ${m.quantity}</div>
                            <small>${m.date}</small>
                            ${m.observation ? `<br><small>📝 ${m.observation}</small>` : ''}
                        </div>
                    `;
                }).join('') || '<p style="text-align: center;">📭 Nenhuma movimentação</p>';
        }

        function filterMovements() {
            loadMovements();
        }

        function changeScreen(screen) {
            document.querySelectorAll('.menu-item').forEach(item => item.classList.remove('active'));
            event.target.closest('.menu-item').classList.add('active');
            
            document.getElementById('dashboardScreen').style.display = 'none';
            document.getElementById('productsScreen').style.display = 'none';
            document.getElementById('movementsScreen').style.display = 'none';
            document.getElementById('profileScreen').style.display = 'none';
            
            document.getElementById(screen + 'Screen').style.display = 'block';
            
            const titles = {
                'dashboard': 'Dashboard',
                'products': 'Itens do Estoque',
                'movements': 'Movimentações',
                'profile': 'Perfil'
            };
            document.getElementById('screenTitle').textContent = titles[screen];
            
            if (screen === 'movements') {
                loadMovements();
                document.getElementById('movementDate').value = '';
            }
        }

        function closeModal(modalId) {
            document.getElementById(modalId).classList.remove('active');
        }

        window.onclick = function(event) {
            if (event.target.classList.contains('modal')) {
                event.target.classList.remove('active');
            }
        }
    </script>
</body>
</html>
