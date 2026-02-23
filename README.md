<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
    <title>Controle de Estoque</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }

        /* Container principal */
        .container {
            width: 100%;
            max-width: 400px;
            margin: 0 auto;
        }

        /* Cards */
        .card {
            background: white;
            border-radius: 20px;
            padding: 30px 25px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            margin-bottom: 20px;
        }

        /* Tela de Login */
        .login-header {
            text-align: center;
            margin-bottom: 30px;
        }

        .login-header h1 {
            color: #333;
            font-size: 28px;
            font-weight: 600;
            margin-bottom: 10px;
        }

        .login-header p {
            color: #666;
            font-size: 14px;
        }

        .login-buttons {
            display: flex;
            gap: 10px;
            margin-bottom: 25px;
        }

        .btn-outline {
            flex: 1;
            padding: 12px;
            border: 2px solid #667eea;
            background: transparent;
            color: #667eea;
            border-radius: 10px;
            font-weight: 600;
            font-size: 16px;
            cursor: pointer;
            transition: all 0.3s;
        }

        .btn-outline:hover {
            background: #667eea;
            color: white;
        }

        .btn-primary {
            flex: 1;
            padding: 12px;
            border: none;
            background: #667eea;
            color: white;
            border-radius: 10px;
            font-weight: 600;
            font-size: 16px;
            cursor: pointer;
            transition: all 0.3s;
        }

        .btn-primary:hover {
            background: #5a67d8;
        }

        .input-group {
            margin-bottom: 20px;
        }

        .input-group label {
            display: block;
            color: #333;
            font-weight: 600;
            font-size: 14px;
            margin-bottom: 5px;
        }

        .input-group input {
            width: 100%;
            padding: 15px;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            font-size: 16px;
            transition: border-color 0.3s;
        }

        .input-group input:focus {
            outline: none;
            border-color: #667eea;
        }

        .login-footer {
            text-align: center;
            margin-top: 20px;
            color: #999;
            font-size: 13px;
        }

        /* Tela Principal */
        .app-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .app-header h1 {
            color: white;
            font-size: 24px;
            font-weight: 600;
        }

        .user-menu {
            background: rgba(255,255,255,0.2);
            padding: 8px 15px;
            border-radius: 20px;
            color: white;
            font-weight: 500;
            cursor: pointer;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 10px;
            margin-bottom: 20px;
        }

        .stat-card {
            background: white;
            padding: 15px 10px;
            border-radius: 15px;
            text-align: center;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        .stat-card .number {
            font-size: 24px;
            font-weight: 700;
            color: #667eea;
            margin-bottom: 5px;
        }

        .stat-card .label {
            font-size: 12px;
            color: #666;
        }

        .stat-card .sub-label {
            font-size: 10px;
            color: #999;
            margin-top: 3px;
        }

        .section-title {
            color: white;
            font-size: 18px;
            font-weight: 600;
            margin-bottom: 15px;
        }

        .empty-state {
            background: white;
            border-radius: 15px;
            padding: 30px 20px;
            text-align: center;
            color: #666;
            margin-bottom: 20px;
        }

        .empty-state p {
            margin-top: 10px;
            font-size: 14px;
        }

        .empty-icon {
            font-size: 40px;
            margin-bottom: 10px;
            opacity: 0.5;
        }

        .movements-list {
            background: white;
            border-radius: 15px;
            overflow: hidden;
        }

        .movement-item {
            padding: 15px;
            border-bottom: 1px solid #f0f0f0;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .movement-item:last-child {
            border-bottom: none;
        }

        .movement-info {
            flex: 1;
        }

        .movement-title {
            font-weight: 600;
            color: #333;
            margin-bottom: 3px;
        }

        .movement-date {
            font-size: 12px;
            color: #999;
        }

        .movement-value {
            font-weight: 600;
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 14px;
        }

        .value-positive {
            background: #e6f7e6;
            color: #27ae60;
        }

        .value-negative {
            background: #fee7e7;
            color: #e74c3c;
        }

        /* Menu Inferior */
        .bottom-menu {
            display: flex;
            background: white;
            border-radius: 20px;
            padding: 10px;
            margin-top: 20px;
        }

        .menu-item {
            flex: 1;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 8px;
            border: none;
            background: transparent;
            color: #999;
            font-size: 12px;
            cursor: pointer;
            border-radius: 12px;
            transition: all 0.3s;
        }

        .menu-item.active {
            background: #667eea;
            color: white;
        }

        .menu-item span {
            font-size: 20px;
            margin-bottom: 4px;
        }

        /* Produtos */
        .products-header {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
        }

        .search-box {
            flex: 1;
            padding: 12px;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            font-size: 16px;
            background: white;
        }

        .add-btn {
            width: 50px;
            height: 50px;
            border: none;
            background: #27ae60;
            color: white;
            border-radius: 10px;
            font-size: 24px;
            cursor: pointer;
        }

        .category-filter {
            display: flex;
            gap: 8px;
            margin-bottom: 20px;
            overflow-x: auto;
            padding: 5px 0;
        }

        .category-filter button {
            padding: 8px 15px;
            border: none;
            border-radius: 20px;
            background: white;
            color: #333;
            font-weight: 500;
            font-size: 13px;
            cursor: pointer;
            white-space: nowrap;
        }

        .category-filter button.active {
            background: #667eea;
            color: white;
        }

        .product-card {
            background: white;
            border-radius: 15px;
            padding: 15px;
            margin-bottom: 10px;
            border-left: 4px solid #667eea;
        }

        .product-card.low-stock {
            border-left-color: #e74c3c;
        }

        .product-card.on-loan {
            border-left-color: #17a2b8;
            background: #f0f9ff;
        }

        .product-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 8px;
        }

        .product-name {
            font-size: 16px;
            font-weight: 600;
            color: #333;
        }

        .product-category {
            background: #f0f0f0;
            padding: 3px 10px;
            border-radius: 15px;
            font-size: 11px;
            color: #666;
        }

        .product-local {
            color: #666;
            font-size: 13px;
            margin-bottom: 10px;
        }

        .product-details {
            display: flex;
            gap: 15px;
            margin: 10px 0;
        }

        .product-detail {
            flex: 1;
            text-align: center;
        }

        .product-detail label {
            font-size: 11px;
            color: #999;
            display: block;
        }

        .product-detail span {
            font-size: 16px;
            font-weight: 600;
            color: #333;
        }

        .product-actions {
            display: flex;
            gap: 8px;
            margin-top: 10px;
        }

        .product-actions button {
            flex: 1;
            padding: 8px;
            border: none;
            border-radius: 8px;
            font-weight: 500;
            font-size: 13px;
            cursor: pointer;
        }

        .edit-btn {
            background: #3498db;
            color: white;
        }

        .loan-btn {
            background: #17a2b8;
            color: white;
        }

        .delete-btn {
            background: #e74c3c;
            color: white;
        }

        .loan-badge {
            display: inline-block;
            background: #17a2b8;
            color: white;
            padding: 3px 10px;
            border-radius: 15px;
            font-size: 11px;
            margin-bottom: 8px;
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
            padding: 20px;
        }

        .modal.active {
            display: flex;
        }

        .modal-content {
            background: white;
            border-radius: 20px;
            padding: 25px;
            max-width: 400px;
            width: 100%;
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
            color: #333;
            font-size: 20px;
        }

        .close-btn {
            background: none;
            border: none;
            font-size: 24px;
            cursor: pointer;
            color: #999;
        }

        .modal-form {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .modal-form input,
        .modal-form select,
        .modal-form textarea {
            padding: 12px;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            font-size: 16px;
        }

        .submit-btn {
            background: #27ae60;
            color: white;
            border: none;
            padding: 15px;
            border-radius: 10px;
            font-weight: 600;
            font-size: 16px;
            cursor: pointer;
            margin-top: 10px;
        }

        .return-btn {
            background: #28a745;
            color: white;
            border: none;
            padding: 10px;
            border-radius: 8px;
            font-weight: 600;
            width: 100%;
            margin-top: 10px;
            cursor: pointer;
        }

        .hidden {
            display: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Tela de Login -->
        <div id="loginScreen" class="card">
            <div class="login-header">
                <h1>Controle de Estoque</h1>
                <p>Sistema simples e eficiente para gerenciar seu estoque</p>
            </div>

            <div class="login-buttons">
                <button class="btn-primary">Entrar</button>
                <button class="btn-outline">Cadastrar</button>
            </div>

            <div class="input-group">
                <label>Usuário</label>
                <input type="text" id="username" placeholder="Digite seu usuário" value="Pablo Murilo">
            </div>

            <div class="input-group">
                <label>Senha</label>
                <input type="password" id="password" placeholder="Digite sua senha" value="123456">
            </div>

            <button class="btn-primary" onclick="login()">Entrar</button>

            <div class="login-footer">
                Sistema para até 4 usuários
            </div>
        </div>

        <!-- Tela Principal -->
        <div id="appScreen" class="hidden">
            <!-- Cabeçalho -->
            <div class="app-header">
                <h1># Painel</h1>
                <div class="user-menu" onclick="logout()">👤 Sair</div>
            </div>

            <!-- Visão geral -->
            <p style="color: white; margin-bottom: 15px; opacity: 0.9;">
                Visão geral do seu estoque em tempo real
            </p>

            <!-- Stats -->
            <div class="stats-grid">
                <div class="stat-card">
                    <div class="number" id="totalProducts">0</div>
                    <div class="label">Total de Produtos</div>
                    <div class="sub-label">produtos cadastrados</div>
                </div>
                <div class="stat-card">
                    <div class="number" id="lowStockCount">0</div>
                    <div class="label">Estoque baixo</div>
                    <div class="sub-label">produtos com estoque baixo</div>
                </div>
                <div class="stat-card">
                    <div class="number" id="todayMovements">0</div>
                    <div class="label">Movimentações Hoje</div>
                    <div class="sub-label">movimentações hoje</div>
                </div>
            </div>

            <!-- Seção Estoque Baixo -->
            <div class="section-title">📦 Estoque baixo</div>
            <div id="lowStockSection" class="empty-state">
                <div class="empty-icon">✅</div>
                <p>Nenhum produto com estoque baixo!</p>
            </div>

            <!-- Seção Emprestados -->
            <div class="section-title">🔧 Emprestados</div>
            <div id="loanSection" class="empty-state">
                <div class="empty-icon">📭</div>
                <p>Nenhum produto emprestado no momento.</p>
            </div>

            <!-- Seção Movimentações Recentes -->
            <div class="section-title">📋 Movimentações Recentes</div>
            <div id="movementsSection" class="empty-state">
                <div class="empty-icon">📊</div>
                <p>Nenhuma transferência registrada ainda.</p>
            </div>

            <!-- Menu Inferior -->
            <div class="bottom-menu">
                <button class="menu-item active" onclick="showScreen('dashboard')">
                    <span>🏠</span>
                    Início
                </button>
                <button class="menu-item" onclick="showScreen('products')">
                    <span>📦</span>
                    Itens
                </button>
                <button class="menu-item" onclick="showScreen('loans')">
                    <span>🔧</span>
                    Empréstimos
                </button>
            </div>
        </div>

        <!-- Tela de Produtos (inicialmente oculta) -->
        <div id="productsScreen" class="hidden" style="margin-top: 20px;">
            <div class="app-header">
                <h1>📦 Itens</h1>
                <div class="user-menu" onclick="showScreen('dashboard')">← Voltar</div>
            </div>

            <div class="products-header">
                <input type="text" class="search-box" id="searchProduct" placeholder="Buscar item..." onkeyup="filterProducts()">
                <button class="add-btn" onclick="openProductModal()">+</button>
            </div>

            <div class="category-filter" id="categoryFilter"></div>

            <div id="productsList"></div>
        </div>

        <!-- Tela de Empréstimos (inicialmente oculta) -->
        <div id="loansScreen" class="hidden" style="margin-top: 20px;">
            <div class="app-header">
                <h1>🔧 Empréstimos</h1>
                <div class="user-menu" onclick="showScreen('dashboard')">← Voltar</div>
            </div>

            <button class="btn-primary" onclick="openLoanModal()" style="margin-bottom: 20px; width: 100%;">
                + Novo Empréstimo
            </button>

            <div id="activeLoansList"></div>
        </div>

        <!-- Modal de Produto -->
        <div id="productModal" class="modal">
            <div class="modal-content">
                <div class="modal-header">
                    <h2 id="modalTitle">Novo Produto</h2>
                    <button class="close-btn" onclick="closeModal('productModal')">&times;</button>
                </div>
                <div class="modal-form">
                    <input type="text" id="productName" placeholder="Nome do produto">
                    <input type="text" id="productLocal" placeholder="Local">
                    <select id="productCategory">
                        <option value="">Categoria</option>
                        <option value="Jardim">Jardim</option>
                        <option value="Elétrica">Elétrica</option>
                        <option value="Ferramentas">Ferramentas</option>
                        <option value="EPI">EPI</option>
                        <option value="Hidráulica">Hidráulica</option>
                        <option value="Geral">Geral</option>
                    </select>
                    <input type="number" id="productQuantity" placeholder="Quantidade">
                    <input type="number" id="productMinQuantity" placeholder="Quantidade mínima">
                    <input type="hidden" id="editingProductId">
                    <button class="submit-btn" onclick="saveProduct()">Salvar</button>
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
                    <input type="text" id="loanUserName" placeholder="Nome de quem pegou">
                    <select id="loanProduct"></select>
                    <input type="number" id="loanQuantity" placeholder="Quantidade" value="1">
                    <input type="date" id="loanDate">
                    <textarea id="loanObservation" placeholder="Observação"></textarea>
                    <button class="submit-btn" onclick="saveLoan()">Registrar</button>
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
                    <div style="background: #f8f9fa; padding: 15px; border-radius: 8px; margin-bottom: 15px;" id="returnInfo"></div>
                    <input type="date" id="returnDate">
                    <textarea id="returnObservation" placeholder="Observação"></textarea>
                    <input type="hidden" id="returnLoanId">
                    <button class="submit-btn" onclick="saveReturn()">Confirmar</button>
                </div>
            </div>
        </div>
    </div>

    <script>
        // DADOS INICIAIS
        let products = JSON.parse(localStorage.getItem('products')) || [
            { id: 1, name: 'Tesoura de Poda', local: 'Prateleira A1', category: 'Jardim', quantity: 8, minQuantity: 3 },
            { id: 2, name: 'Alicate Universal', local: 'Gaveta 10', category: 'Elétrica', quantity: 5, minQuantity: 2 },
            { id: 3, name: 'Martelo', local: 'Prateleira B1', category: 'Ferramentas', quantity: 10, minQuantity: 4 },
            { id: 4, name: 'Luva de Raspa', local: 'Armário D1', category: 'EPI', quantity: 12, minQuantity: 5 },
            { id: 5, name: 'Fita Veda-rosca', local: 'Gaveta 16', category: 'Hidráulica', quantity: 15, minQuantity: 5 },
            { id: 6, name: 'Cadeado', local: 'Gaveta 17', category: 'Geral', quantity: 8, minQuantity: 3 }
        ];
        
        let loans = JSON.parse(localStorage.getItem('loans')) || [];
        let movements = JSON.parse(localStorage.getItem('movements')) || [];
        let currentUser = null;
        let currentCategory = 'todos';

        // LOGIN
        function login() {
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            
            if (username && password) {
                currentUser = { name: username };
                document.getElementById('loginScreen').style.display = 'none';
                document.getElementById('appScreen').classList.remove('hidden');
                updateDashboard();
                loadProducts();
                loadCategoryFilter();
                loadLoanProductSelect();
                loadActiveLoans();
            } else {
                alert('Preencha usuário e senha!');
            }
        }

        function logout() {
            currentUser = null;
            document.getElementById('loginScreen').style.display = 'block';
            document.getElementById('appScreen').classList.add('hidden');
            document.getElementById('productsScreen').classList.add('hidden');
            document.getElementById('loansScreen').classList.add('hidden');
        }

        // NAVEGAÇÃO
        function showScreen(screen) {
            document.getElementById('appScreen').classList.add('hidden');
            document.getElementById('productsScreen').classList.add('hidden');
            document.getElementById('loansScreen').classList.add('hidden');
            
            if (screen === 'dashboard') {
                document.getElementById('appScreen').classList.remove('hidden');
                updateDashboard();
                loadActiveLoans();
            } else if (screen === 'products') {
                document.getElementById('productsScreen').classList.remove('hidden');
                loadProducts();
                loadCategoryFilter();
            } else if (screen === 'loans') {
                document.getElementById('loansScreen').classList.remove('hidden');
                loadActiveLoans();
            }
        }

        // DASHBOARD
        function updateDashboard() {
            document.getElementById('totalProducts').textContent = products.length;
            
            const lowStock = products.filter(p => p.quantity <= p.minQuantity);
            document.getElementById('lowStockCount').textContent = lowStock.length;
            
            const today = new Date().toISOString().split('T')[0];
            const todayMovements = movements.filter(m => m.date === today);
            document.getElementById('todayMovements').textContent = todayMovements.length;
            
            // Estoque baixo
            const lowStockSection = document.getElementById('lowStockSection');
            if (lowStock.length > 0) {
                lowStockSection.innerHTML = lowStock.map(p => `
                    <div style="background: white; padding: 10px; margin-bottom: 5px; border-radius: 8px; border-left: 4px solid #e74c3c;">
                        <strong>${p.name}</strong> - ${p.quantity} / ${p.minQuantity}
                        <br><small>📍 ${p.local}</small>
                    </div>
                `).join('');
            } else {
                lowStockSection.innerHTML = `
                    <div class="empty-icon">✅</div>
                    <p>Nenhum produto com estoque baixo!</p>
                `;
            }
            
            // Movimentações recentes
            const movementsSection = document.getElementById('movementsSection');
            if (movements.length > 0) {
                const recent = movements.sort((a,b)=>b.id-a.id).slice(0,5);
                movementsSection.innerHTML = recent.map(m => `
                    <div style="background: white; padding: 10px; margin-bottom: 5px; border-radius: 8px;">
                        <div style="display: flex; justify-content: space-between;">
                            <strong>${m.productName}</strong>
                            <span style="color: ${m.type === 'entry' ? '#27ae60' : '#e74c3c'}">
                                ${m.type === 'entry' ? '+'+m.quantity : '-'+m.quantity}
                            </span>
                        </div>
                        <small>${m.date}</small>
                    </div>
                `).join('');
            } else {
                movementsSection.innerHTML = `
                    <div class="empty-icon">📊</div>
                    <p>Nenhuma transferência registrada ainda.</p>
                `;
            }
        }

        // PRODUTOS
        function loadCategoryFilter() {
            const cats = ['todos', ...new Set(products.map(p => p.category))];
            const filterDiv = document.getElementById('categoryFilter');
            
            filterDiv.innerHTML = cats.map(cat => 
                `<button class="${cat === 'todos' ? 'active' : ''}" onclick="filterByCategory('${cat}')">
                    ${cat === 'todos' ? 'Todos' : cat}
                </button>`
            ).join('');
        }

        function filterByCategory(cat) {
            currentCategory = cat;
            document.querySelectorAll('#categoryFilter button').forEach(btn => {
                btn.classList.remove('active');
                if (btn.textContent === (cat === 'todos' ? 'Todos' : cat)) {
                    btn.classList.add('active');
                }
            });
            filterProducts();
        }

        function filterProducts() {
            const search = document.getElementById('searchProduct').value.toLowerCase();
            const filtered = products.filter(p => 
                (currentCategory === 'todos' || p.category === currentCategory) &&
                (p.name.toLowerCase().includes(search) || p.local.toLowerCase().includes(search))
            );
            displayProducts(filtered);
        }

        function displayProducts(list) {
            const activeLoans = loans.filter(l => !l.returned);
            
            document.getElementById('productsList').innerHTML = list.map(p => {
                const loaned = activeLoans.filter(l => l.productId === p.id).reduce((s, l) => s + l.quantity, 0);
                const available = p.quantity - loaned;
                
                return `
                    <div class="product-card ${p.quantity <= p.minQuantity ? 'low-stock' : ''} ${loaned > 0 ? 'on-loan' : ''}">
                        <div class="product-header">
                            <span class="product-name">${p.name}</span>
                            <span class="product-category">${p.category}</span>
                        </div>
                        <div class="product-local">📍 ${p.local}</div>
                        ${loaned > 0 ? `<div class="loan-badge">🔧 ${loaned} emprestado(s)</div>` : ''}
                        <div class="product-details">
                            <div class="product-detail">
                                <label>Disponível</label>
                                <span style="color: ${available <= p.minQuantity ? '#e74c3c' : '#27ae60'}">${available}</span>
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
            }).join('') || '<p style="text-align: center;">🔍 Nenhum item encontrado</p>';
        }

        function loadProducts() {
            filterProducts();
        }

        function openProductModal() {
            document.getElementById('modalTitle').textContent = 'Novo Produto';
            document.getElementById('productName').value = '';
            document.getElementById('productLocal').value = '';
            document.getElementById('productCategory').value = '';
            document.getElementById('productQuantity').value = '';
            document.getElementById('productMinQuantity').value = '';
            document.getElementById('editingProductId').value = '';
            document.getElementById('productModal').classList.add('active');
        }

        function editProduct(id) {
            const p = products.find(p => p.id === id);
            if (p) {
                document.getElementById('modalTitle').textContent = 'Editar Produto';
                document.getElementById('productName').value = p.name;
                document.getElementById('productLocal').value = p.local;
                document.getElementById('productCategory').value = p.category;
                document.getElementById('productQuantity').value = p.quantity;
                document.getElementById('productMinQuantity').value = p.minQuantity;
                document.getElementById('editingProductId').value = id;
                document.getElementById('productModal').classList.add('active');
            }
        }

        function saveProduct() {
            const id = document.getElementById('editingProductId').value;
            const product = {
                name: document.getElementById('productName').value,
                local: document.getElementById('productLocal').value,
                category: document.getElementById('productCategory').value,
                quantity: parseInt(document.getElementById('productQuantity').value) || 0,
                minQuantity: parseInt(document.getElementById('productMinQuantity').value) || 0
            };
            
            if (!product.name || !product.local || !product.category) {
                alert('Preencha todos os campos!');
                return;
            }
            
            if (id) {
                const index = products.findIndex(p => p.id == id);
                products[index] = { ...products[index], ...product };
            } else {
                product.id = Date.now();
                products.push(product);
            }
            
            localStorage.setItem('products', JSON.stringify(products));
            closeModal('productModal');
            loadProducts();
            updateDashboard();
            loadCategoryFilter();
            loadLoanProductSelect();
        }

        function deleteProduct(id) {
            if (confirm('Excluir este item?')) {
                products = products.filter(p => p.id !== id);
                localStorage.setItem('products', JSON.stringify(products));
                loadProducts();
                updateDashboard();
                loadCategoryFilter();
            }
        }

        // EMPRÉSTIMOS
        function loadLoanProductSelect() {
            const select = document.getElementById('loanProduct');
            const activeLoans = loans.filter(l => !l.returned);
            
            select.innerHTML = '<option value="">Selecione um item</option>' +
                products.map(p => {
                    const loaned = activeLoans.filter(l => l.productId === p.id).reduce((s, l) => s + l.quantity, 0);
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
            if (productId) document.getElementById('loanProduct').value = productId;
            document.getElementById('loanModal').classList.add('active');
        }

        function saveLoan() {
            const user = document.getElementById('loanUserName').value;
            const pid = parseInt(document.getElementById('loanProduct').value);
            const qty = parseInt(document.getElementById('loanQuantity').value);
            const date = document.getElementById('loanDate').value;
            
            if (!user || !pid || !qty || !date) {
                alert('Preencha todos os campos!');
                return;
            }
            
            const product = products.find(p => p.id === pid);
            
            loans.push({
                id: Date.now(),
                userName: user,
                productId: pid,
                productName: product.name,
                productLocal: product.local,
                quantity: qty,
                date,
                returned: false
            });
            
            movements.push({
                id: Date.now() + 1,
                productId: pid,
                productName: product.name,
                quantity: qty,
                date,
                type: 'loan'
            });
            
            localStorage.setItem('loans', JSON.stringify(loans));
            localStorage.setItem('movements', JSON.stringify(movements));
            
            closeModal('loanModal');
            updateDashboard();
            loadProducts();
            loadLoanProductSelect();
            loadActiveLoans();
        }

        function loadActiveLoans() {
            const active = loans.filter(l => !l.returned);
            const list = document.getElementById('activeLoansList');
            const loanSection = document.getElementById('loanSection');
            
            if (active.length > 0) {
                if (list) {
                    list.innerHTML = active.map(l => `
                        <div style="background: white; border-radius: 15px; padding: 15px; margin-bottom: 10px; border-left: 4px solid #17a2b8;">
                            <div style="display: flex; justify-content: space-between;">
                                <strong>👤 ${l.userName}</strong>
                                <small>${l.date}</small>
                            </div>
                            <div style="margin: 8px 0;"><strong>${l.productName}</strong></div>
                            <div>📍 ${l.productLocal}</div>
                            <div>Quantidade: ${l.quantity}</div>
                            <button class="return-btn" onclick="openReturnModal(${l.id})">↩️ Devolver</button>
                        </div>
                    `).join('');
                }
                
                if (loanSection) {
                    loanSection.innerHTML = active.map(l => `
                        <div style="background: white; padding: 10px; margin-bottom: 5px; border-radius: 8px; border-left: 4px solid #17a2b8;">
                            <strong>${l.productName}</strong> - ${l.userName}
                            <br><small>📦 ${l.quantity} unid. - ${l.date}</small>
                        </div>
                    `).join('');
                }
            } else {
                if (list) list.innerHTML = '<p style="text-align: center;">Nenhum empréstimo ativo</p>';
                if (loanSection) {
                    loanSection.innerHTML = `
                        <div class="empty-icon">📭</div>
                        <p>Nenhum produto emprestado no momento.</p>
                    `;
                }
            }
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
            
            const index = loans.findIndex(l => l.id === loanId);
            if (index === -1) return;
            
            loans[index].returned = true;
            
            movements.push({
                id: Date.now(),
                productId: loans[index].productId,
                productName: loans[index].productName,
                quantity: loans[index].quantity,
                date: returnDate,
                type: 'return'
            });
            
            localStorage.setItem('loans', JSON.stringify(loans));
            localStorage.setItem('movements', JSON.stringify(movements));
            
            closeModal('returnModal');
            updateDashboard();
            loadProducts();
            loadLoanProductSelect();
            loadActiveLoans();
        }

        function closeModal(id) {
            document.getElementById(id).classList.remove('active');
        }
    </script>
</body>
</html>
