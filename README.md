# orcamento-marcenaria2
= PRÉ - ORÇAMENTO MARCENARIA =
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Orçamento Marcenaria WhatsApp</title>
    <!-- Carregando Tailwind CSS para Estilização Responsiva e Moderna -->
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f7f3e8; /* Fundo Creme Suave */
        }
        .wood-card {
            background-color: #ffffff;
            border: 2px solid #a0522d; /* Detalhe em Marrom/Sienna */
            box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1);
        }
        .btn-primary {
            background-color: #d2b48c; /* Tan/Cor de Madeira Clara */
            transition: all 0.2s;
        }
        .btn-primary:hover {
            background-color: #a0522d; /* Sienna/Cor de Madeira Escura */
            color: #ffffff;
        }
        .btn-whatsapp {
            background-color: #25d366; /* Verde WhatsApp */
            transition: all 0.2s;
        }
        .btn-whatsapp:hover {
            background-color: #128c7e;
        }
        .btn-remover {
            background-color: #ef4444; /* Vermelho */
            color: white;
            border-radius: 9999px;
            width: 1.5rem;
            height: 1.5rem;
            font-weight: bold;
            font-size: 0.875rem;
            line-height: 1.5rem; /* Centraliza o 'X' */
            text-align: center;
            transition: background-color 0.2s;
        }
        .btn-remover:hover {
            background-color: #b91c1c;
        }
        .input-style {
            border: 1px solid #ccc;
            padding: 0.75rem;
            border-radius: 0.5rem;
            width: 100%;
            transition: border-color 0.2s;
        }
        .input-style:focus {
            border-color: #a0522d;
            outline: none;
        }
        /* Classe para borda verde de sucesso na validação */
        .border-success {
            border-color: #22c55e; /* Verde */
        }
    </style>
</head>
<body class="min-h-screen flex items-center justify-center p-4">

    <!-- Card Principal e Layout Responsivo -->
    <div class="w-full max-w-lg mx-auto wood-card rounded-xl p-6 md:p-8">

        <!-- TÍTULO ALTERADO -->
        <h1 class="text-3xl font-bold text-center text-gray-800 mb-2">
            Pré-Orçamento de Marcenaria
        </h1>
        <p class="text-center text-sm text-gray-600 mb-4">
            Adicione os serviços desejados para montar a proposta.
        </p>

        <!-- Banner de Promoção e Eventos (Mantido) -->
        <div class="mb-8 p-6 bg-[#a0522d] text-white wood-card rounded-xl border-none shadow-xl transform transition duration-300 hover:scale-[1.01]">
            <h2 class="text-2xl font-bold text-center mb-1">
                ✨ PROMOÇÃO IMPERDÍVEL! ✨
            </h2>
            <p class="text-center text-sm font-semibold mb-3">
                Substituição de Portas: *5% de Desconto* no total para 3+ unidades!
            </p>
            <div class="border-t border-t-white/30 pt-3 text-center">
                <p class="text-xs italic">
                    Agende sua visita técnica GRATUITA hoje e ganhe um brinde exclusivo!
                </p>
                <span class="text-xs font-bold block mt-1">
                    Próximo Evento: Workshop "DIY Portas" em 15/Dez. Reserve sua vaga!
                </span>
            </div>
        </div>
        <!-- FIM: Banner de Promoção e Eventos -->

        <!-- NOVO: PASSO 1 - Endereço como Pré-Requisito -->
        <div id="endereco-container" class="space-y-2 mb-6">
            <label for="endereco" class="block text-lg font-semibold text-gray-700">
                1. Endereço da Visita
            </label>
            <input type="text" id="endereco" class="input-style text-base" placeholder="Digite o endereço completo da visita...">
            <p id="endereco-msg" class="text-sm text-gray-500">
                Preencha o endereço para liberar o orçamento.
            </p>
        </div>
        
        <!-- NOVO: PASSO 2 - Corpo do Orçamento (Inicia Oculto) -->
        <div id="orcamento-body" class="hidden">

            <!-- Formulário de Adicionar Itens -->
            <div id="item-form" class="space-y-4 pt-6 border-t border-gray-200">
                <label class="block text-lg font-semibold text-gray-700">
                    2. Adicione os Serviços
                </label>
                <div>
                    <label for="servico-item" class="block text-sm font-medium text-gray-700 mb-1">Selecione o Serviço:</label>
                    <select id="servico-item" class="input-style bg-white">
                        <!-- Opções serão preenchidas via JS -->
                    </select>
                </div>
                <div class="flex items-center space-x-4">
                    <div class="flex-1">
                        <label for="quantidade-item" class="block text-sm font-medium text-gray-700 mb-1">Quantidade:</label>
                        <input type="number" id="quantidade-item" min="1" value="1" class="input-style">
                    </div>
                    <button id="btn-add-item" class="btn-primary mt-6 px-6 py-3 rounded-xl font-semibold text-gray-900 shadow-md hover:shadow-xl">
                        Adicionar
                    </button>
                </div>
            </div>
            <!-- FIM: Formulário de Adicionar Itens -->

            <!-- Lista de Itens Adicionados e Total -->
            <div id="itens-container" class="mt-8 pt-6 border-t border-gray-200">
                <h2 class="text-xl font-bold text-gray-800 mb-4">Itens do Orçamento</h2>
                <div id="lista-itens" class="space-y-2 mb-4">
                    <!-- Itens adicionados via JS aparecerão aqui -->
                    <p id="lista-vazia-msg" class="text-gray-500 text-sm">Nenhum item adicionado ainda.</p>
                </div>
                <div id="total-display" class="text-right text-2xl font-bold text-gray-800 p-4 bg-gray-100 rounded-lg">
                    Total: R$ 0,00
                </div>
            </div>
            <!-- FIM: Lista de Itens Adicionados e Total -->

            <!-- Área de Finalização (WhatsApp) -->
            <div id="finalizar-area" class="mt-6 space-y-4">
                <label class="block text-lg font-semibold text-gray-700">
                    3. Finalizar
                </label>
            
                <p id="whatsapp-error" class="text-red-600 text-sm text-center hidden"></p>

                <button id="btn-whatsapp" class="btn-whatsapp w-full py-3 rounded-xl text-lg font-semibold text-white flex items-center justify-center space-x-2 shadow-lg">
                    <!-- Ícone de WhatsApp -->
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" viewBox="0 0 24 24" fill="currentColor">
                        <path d="M12 2C6.477 2 2 6.477 2 12c0 1.932.54 3.74 1.48 5.308l-1.01 3.904 4.02-1.054A9.97 9.97 0 0012 22c5.523 0 10-4.477 10-10S17.523 2 12 2zM17.5 15.6c-.22-.11-.7-.35-.8-.4c-.1-.05-.18-.08-.25.08-.07.16-.27.4-.33.48-.07.08-.13.08-.25.03-.6-.23-1.85-.7-2.78-1.72-.75-.85-1.25-1.87-1.4-2.12-.15-.24 0-.37.11-.48.1-.11.25-.26.33-.39.08-.13.11-.22.07-.3s-.25-.6-.35-.85c-.11-.24-.22-.2-.3-.2-.07-.07-.15-.12-.23-.12-.07 0-.17.03-.25.12-.08.08-.3.3-.3.73 0 .43.31.84.35.9.04.06.6.93.7 1.13.1.2.16.2.3.2.14 0 .93-.34 1.12-.41.19-.07.38-.13.43-.2.05-.07.16-.18.25-.28.09-.1.17-.2.25-.13.07.06.47.78.6 1.05.13.26.08.48.02.58-.06.1-.2.24-.4.36z"/>
                    </svg>
                    <span>Enviar Pré-Orçamento via WhatsApp</span>
                </button>
                <p class="text-xs text-center text-gray-500 mt-2">
                    Você será redirecionado para o WhatsApp com a mensagem pré-preenchida.
                </p>
            </div>
            <!-- FIM: Área de Finalização -->
        
        </div>
        <!-- FIM: Corpo do Orçamento -->


    </div>

    <script>
        // Variáveis globais para configuração do Firebase (não usadas para esta lógica)
        const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';
        const firebaseConfig = typeof __firebase_config !== 'undefined' ? JSON.parse(__firebase_config) : {};
        const initialAuthToken = typeof __initial_auth_token !== 'undefined' ? __initial_auth_token : '';
        
        // --- Lógica de Orçamento Itemizado ---

        // 1. DADOS: Baseado na imagem fornecida
        const servicosDisponiveis = [
            { id: 'p_s_pf', desc: 'Paraná - Substituição (Porta e Forra)', valor: 180.00 },
            { id: 'p_s_p', desc: 'Paraná - Substituição (Porta)', valor: 150.00 },
            { id: 'm_s_pf', desc: 'Madeira Maciça - Substituição (Porta e Forra)', valor: 200.00 },
            { id: 'm_s_p', desc: 'Madeira Maciça - Substituição (Porta)', valor: 180.00 },
            { id: 'pr_i_pf', desc: 'Portas Prontas - Instalação (Porta e Forra)', valor: 200.00 },
            { id: 'pr_i_p', desc: 'Portas Prontas - Instalação (Porta)', valor: 180.00 },
            { id: 'mp_i_pfp', desc: 'Portas Maciça Pivotantes - Instalação (Porta e Forra Padrão)', valor: 250.00 },
            { id: 'mp_i_pffp', desc: 'Portas Maciça Pivotantes - Instalação (Porta e Forra Fora de Padrão)', valor: 'COMBINAR' },
            { id: 'fc_s_fd', desc: 'Fechaduras Convencional - Substituição (Fechadura e Dobradiças)', valor: 150.00 },
            { id: 'fe_i_ua', desc: 'Fechaduras Eletrônicas - Instalação (Usinagem e Adaptação)', valor: 180.00 },
            { id: 'c_i_t', desc: 'Carpintaria - Instalação (Telhado)', valor: 'COMBINAR' },
            { id: 'c_i_c', desc: 'Carpintaria - Instalação (Caramanchão)', valor: 'COMBINAR' },
            { id: 'c_i_l', desc: 'Carpintaria - Instalação (Lambri)', valor: 'COMBINAR' },
            { id: 'c_i_d', desc: 'Carpintaria - Instalação (Deck)', valor: 'COMBINAR' }
        ];

        // 2. ESTADO: Lista de itens que o usuário adicionou
        let itensOrcamento = [];

        // 3. ELEMENTOS DO DOM
        const elements = {
            // NOVO: Itens de Endereço
            endereco: document.getElementById('endereco'),
            enderecoMsg: document.getElementById('endereco-msg'),
            orcamentoBody: document.getElementById('orcamento-body'),
            
            // Itens do Formulário
            servicoItem: document.getElementById('servico-item'),
            quantidadeItem: document.getElementById('quantidade-item'),
            btnAddItem: document.getElementById('btn-add-item'),
            
            // Itens da Lista e Total
            listaItens: document.getElementById('lista-itens'),
            listaVaziaMsg: document.getElementById('lista-vazia-msg'),
            totalDisplay: document.getElementById('total-display'),
            
            // Itens de Finalização
            btnWhatsapp: document.getElementById('btn-whatsapp'),
            whatsappError: document.getElementById('whatsapp-error'),
        };

        // 4. FUNÇÕES
        
        /**
         * Formata um número para o padrão monetário BRL.
         */
        function formatarMoeda(valor) {
            return valor.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' });
        }

        /**
         * Popula o dropdown <select> com os serviços disponíveis.
         */
        function popularDropdown() {
            elements.servicoItem.innerHTML = ''; // Limpa opções antigas
            servicosDisponiveis.forEach(servico => {
                const option = document.createElement('option');
                option.value = servico.id;
                
                let precoTexto = '';
                if (typeof servico.valor === 'number') {
                    precoTexto = `(${formatarMoeda(servico.valor)})`;
                } else {
                    precoTexto = `(À Combinar)`;
                }
                
                option.textContent = `${servico.desc} ${precoTexto}`;
                elements.servicoItem.appendChild(option);
            });
        }

        /**
         * Renderiza a lista de itens do orçamento e atualiza o total.
         */
        function renderizarLista() {
            elements.listaItens.innerHTML = ''; // Limpa a lista
            let total = 0;
            let temItensACombinar = false;

            if (itensOrcamento.length === 0) {
                elements.listaItens.appendChild(elements.listaVaziaMsg);
                elements.listaVaziaMsg.style.display = 'block';
            } else {
                elements.listaVaziaMsg.style.display = 'none';
                
                itensOrcamento.forEach((item, index) => {
                    const itemDiv = document.createElement('div');
                    itemDiv.className = 'flex items-center justify-between p-3 bg-gray-50 rounded-lg border';
                    
                    let subtotalTexto = '';
                    if (typeof item.servico.valor === 'number') {
                        const subtotal = item.quantidade * item.servico.valor;
                        total += subtotal;
                        subtotalTexto = `<span class="font-semibold">${formatarMoeda(subtotal)}</span>`;
                    } else {
                        subtotalTexto = `<span class="font-semibold text-blue-600">À Combinar</span>`;
                        temItensACombinar = true;
                    }

                    itemDiv.innerHTML = `
                        <div class="flex-1 mr-2">
                            <span class="font-medium text-gray-800">${item.quantidade}x</span>
                            <span class="text-gray-700 text-sm">${item.servico.desc}</span>
                        </div>
                        ${subtotalTexto}
                        <button class="btn-remover ml-3" data-index="${index}" title="Remover item">&times;</button>
                    `;
                    elements.listaItens.appendChild(itemDiv);
                });
            }

            // Atualiza o display do total
            let totalTexto = formatarMoeda(total);
            if (temItensACombinar) {
                totalTexto += " + Itens à Combinar";
            }
            elements.totalDisplay.textContent = `Total: ${totalTexto}`;
        }

        /**
         * Adiciona o item selecionado à lista de orçamento.
         */
        function adicionarItem() {
            const servicoId = elements.servicoItem.value;
            const quantidade = parseInt(elements.quantidadeItem.value, 10);

            if (isNaN(quantidade) || quantidade < 1) {
                // Substituindo alert por uma mensagem de erro no console ou UI
                console.warn('Quantidade inválida.');
                elements.quantidadeItem.focus();
                return;
            }

            const servicoSelecionado = servicosDisponiveis.find(s => s.id === servicoId);

            if (servicoSelecionado) {
                itensOrcamento.push({
                    servico: servicoSelecionado,
                    quantidade: quantidade
                });
                renderizarLista();
                elements.quantidadeItem.value = 1; // Reseta a quantidade
            }
        }

        /**
         * Remove um item da lista baseado no seu índice.
         */
        function removerItem(index) {
            itensOrcamento.splice(index, 1);
            renderizarLista();
        }

        /**
         * NOVO: Verifica o preenchimento do endereço e exibe/oculta o corpo do orçamento.
         */
        function verificarEndereco() {
            // Usando 5 caracteres como validação mínima para um endereço
            const enderecoValido = elements.endereco.value.trim().length >= 5; 
            
            if (enderecoValido) {
                elements.orcamentoBody.classList.remove('hidden');
                elements.enderecoMsg.textContent = 'Endereço preenchido. Pode prosseguir!';
                elements.enderecoMsg.className = 'text-sm text-green-600 font-medium';
                elements.endereco.classList.add('border-success'); // Adiciona borda verde
            } else {
                elements.orcamentoBody.classList.add('hidden');
                elements.enderecoMsg.textContent = 'Preencha o endereço para liberar o orçamento.';
                elements.enderecoMsg.className = 'text-sm text-gray-500';
                elements.endereco.classList.remove('border-success'); // Remove borda verde
            }
        }

        /**
         * Constrói e abre o link do WhatsApp com o orçamento preenchido.
         */
        function enviarWhatsApp() {
            const endereco = elements.endereco.value.trim();
            elements.whatsappError.classList.add('hidden');

            // Validação de itens (validação de endereço é tratada pela visibilidade do botão)
            if (itensOrcamento.length === 0) {
                elements.whatsappError.textContent = 'Adicione pelo menos um item ao orçamento.';
                elements.whatsappError.classList.remove('hidden');
                return;
            }

            // Construir a mensagem
            const dataAtual = new Date().toLocaleDateString('pt-BR');
            let total = 0;
            let temItensACombinar = false;

            let itensTexto = itensOrcamento.map(item => {
                let subtotalTexto = '';
                if (typeof item.servico.valor === 'number') {
                    const subtotal = item.quantidade * item.servico.valor;
                    total += subtotal;
                    subtotalTexto = `Subtotal: ${formatarMoeda(subtotal)}`;
                } else {
                    subtotalTexto = `Subtotal: À Combinar`;
                    temItensACombinar = true;
                }
                return `- ${item.quantidade}x ${item.servico.desc}\n  (${subtotalTexto})`;
            }).join('\n');

            let totalTexto = formatarMoeda(total);
            if (temItensACombinar) {
                totalTexto += " + Itens à Combinar";
            }

            // Texto "Pré-Orçamento" incluído no template
            const orcamentoFinalText = `
*PROPOSTA DE PRÉ-ORÇAMENTO DE MARÇENARIA*
Data: ${dataAtual}
Endereço para Visita: ${endereco}
----------------------------------------
*Itens Solicitados:*
${itensTexto}
----------------------------------------
*VALOR TOTAL ESTIMADO:*
${totalTexto}
----------------------------------------
*Nota:* Este é um pré-orçamento preliminar. O valor final pode variar após a medição e avaliação técnica no local.
Por favor, confirme se gostaria de agendar uma visita técnica.
            `.trim();

            
            // Substitua 'SEUNUMERO' pelo número de telefone da sua empresa (incluindo código do país, ex: 5521999998888)
            const whatsappNumber = "5585986611840"; // INSIRA SEU NÚMERO AQUI (Código País + DDD + Número)
            const encodedText = encodeURIComponent(orcamentoFinalText);
            
            // Abre a URL do WhatsApp Web/App
            const whatsappUrl = `https://wa.me/${whatsappNumber}?text=${encodedText}`;
            window.open(whatsappUrl, '_blank');
        }

        // 5. EVENT LISTENERS

        // Popula o dropdown quando a página carregar
        document.addEventListener('DOMContentLoaded', () => {
            popularDropdown();
            renderizarLista(); // Para exibir a mensagem "Nenhum item"
            verificarEndereco(); // Verifica o endereço no carregamento (caso o usuário atualize a pág)
        });
        
        // NOVO: Listener para verificar o endereço em tempo real
        elements.endereco.addEventListener('input', verificarEndereco);

        // Adicionar item
        elements.btnAddItem.addEventListener('click', adicionarItem);

        // Enviar WhatsApp
        elements.btnWhatsapp.addEventListener('click', enviarWhatsApp);

        // Remover item (usando delegação de eventos)
        elements.listaItens.addEventListener('click', (e) => {
            const removeButton = e.target.closest('.btn-remover');
            if (removeButton) {
                const index = parseInt(removeButton.dataset.index, 10);
                removerItem(index);
            }
        });

    </script>
</body>
</html>
