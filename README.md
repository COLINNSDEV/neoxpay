# 🚀 Roadmap NeoxPay Gateway

### 🌐 Módulo 1: Painel Web (Dashboard)
- [x] Interface de Criação de Grupos (Foto, nome, token, descrição)
- [x] Sistema Multimoedas (Pricing dinâmico BRL, USD, EUR)
- [x] Validação de Conexão (Verificação de Admin via código de 6 dígitos)
- [x] Gerenciador do Bot (Alteração da mensagem de boas-vindas em tempo real)
- [x] Criação de Produtos Avulsos (Ebooks/Packs)
- [x] Dashboard Financeiro (Interface de relatórios de saldo e vendas)
- [x] Sistema de Autenticação Real (Login seguro com banco de dados e hash de senhas)
- [x] Cadastro de Contas Bancárias (Gerenciamento de Chaves PIX no perfil)
- [x] Sistema de Saque Integrado (Comunicação direta com a API de cashout)

### 🤖 Módulo 2: O Robô do Telegram
- [x] Arquitetura Anti-Fantasmas (Prevenção de sequestro de cliques)
- [x] Comando `/start` Dinâmico (Lê painel e chama pelo nome)
- [x] Botões Inline de Conversão (Gera BRL, USD, EUR lendo do banco)
- [x] Leitura de Cliques Liberada (API do Telegram desbloqueada para callbacks)
- [x] Áudios Humanizados (Envio de voz antes da mensagem de texto na entrega)

### 💳 Módulo 3: Gateway de Pagamento
- [x] Integração Checkout Stripe (Geração de sessão USD/EUR)
- [x] Redirecionamento Pós-Compra (Tela de sucesso e registro de venda)
- [x] Sistema PIX Real (Integração com PodPay para código Copia e Cola autêntico)
- [x] Webhook de Confirmação (Sistema "Tanque de Guerra" à prova de falhas com banco de dados)

### 🚪 Módulo 4: Pós-Venda e Entrega
- [x] Geração do Link de Convite VIP (Uso único e entrega automática via Telegram)
- [ ] Controle de Recorrência (Expulsão automática do grupo após X dias)
- [ ] Recuperação de Vendas/Remarketing (Aviso após 15 min sem pagamento)

### 🛡️ Módulo 5: Segurança e Infraestrutura
- [x] Versionamento Seguro (Código-fonte protegido e backupeado no GitHub Privado)
- [x] Escudo de Banco de Dados (.gitignore bloqueando vazamento de dados de clientes)
- [ ] Isolamento de Chaves API (Criação de arquivo .env para ocultar senhas)
