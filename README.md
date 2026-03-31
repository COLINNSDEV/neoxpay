🚀 NeoxPay - Gateway & Telegram Automation Hub
🌐 Módulo 1: Painel Web (Dashboard & Management)
[x] Interface de Criação de Grupos (Foto, nome, token, descrição)

[x] Sistema Multimoedas (Pricing dinâmico BRL, USD, EUR)

[x] Validação de Conexão (Verificação via código de 14 dígitos)

[x] Criação de Produtos Avulsos (Ebooks/Packs/Conteúdos Exclusivos)

[x] Configuração de Remarketing Dinâmico (Interface Liquid Glass iOS para criar ofertas por plano, tempo de disparo e público-alvo)

[x] Puxada Automática de Dados (O sistema lê os planos e conteúdos já criados no bot e gera os cards de oferta automaticamente)

[x] Cadastro de Contas Bancárias (Gerenciamento de Chaves PIX)

[x] Painel Administrativo "Visão de Deus" (Lucro líquido, volume total e controle de taxas)

[x] Central de Atendimento Pró (Aprovação manual de saques, busca por TX ID e Reenvio de acesso)

[x] Sistema de Afiliados (Rastreamento de cadastros via link ?ref=)

[x] Login Universal Inteligente (Redirecionamento automático Admin/Suporte/Cliente)

[x] Gestão de Equipe (Demitir atendentes e configurar permissões de acesso)

🤖 Módulo 2: O Robô do Telegram
[x] Comando /start Dinâmico (Lê painel e chama pelo nome)

[x] Botões Inline de Conversão (BRL, USD, EUR)

[x] Áudios Humanizados (Envio de voz automático na recepção e na entrega)

[x] Funil Multi-idioma (Perguntar idioma ao usuário e trocar textos/áudios dinamicamente)

[x] Mídia Específica por País (Fotos e vídeos diferentes para gringos e brasileiros)

💳 Módulo 3: Gateway de Pagamento
[x] Integração Checkout Stripe (Sessões seguras USD/EUR)

[x] Sistema PIX Real (Integração PodPay com código Copia e Cola)

[x] Blindagem de Webhook (Verificação criptográfica de assinatura para evitar fakes)

[x] Simulador de Vendas (Ferramenta interna para testar o dashboard com notificações PWA nativas)

🛡️ Módulo 4: Segurança Industrial e AppSec (O "Cofre")
[x] Isolamento de Chaves (.env) (Senhas e APIs escondidas do código-fonte)

[x] Criptografia Fail-Safe (Fernet) (Tokens do Telegram criptografados no banco)

[x] Prevenção de Saque Duplo (Travamento de banco with_for_update contra requisições simultâneas)

[x] Bloqueio IDOR Absoluto (Trava de segurança para impedir que usuários editem dados de outros)

[x] Rate Limit Inteligente (ProxyFix) (Bloqueio de IP por tentativas de login lendo IP real via Cloudflare)

[x] Upload de Arquivo "Magic Bytes" (Verificação do DNA do arquivo + renomeação por UUID)

[x] Sistema de Banimento "Insta-Kill" (Derruba a sessão ativa instantaneamente se o usuário for banido)

[x] Proteção Anti-XSS (Bleach) (Sanitização cirúrgica de inputs mantendo formatação do Telegram)

[x] Defesa Anti-CSRF Estrita (Validação rigorosa de Origin e Referer via Middleware)

[x] Cabeçalhos de Segurança (CSP) (Bloqueio de Clickjacking e SameSite=Strict)

🚧 O QUE FALTA (Os Próximos Passos)
🚪 Pós-Venda e Retenção (O Motor de Faturamento)
[ ] Controle de Recorrência (Script para expulsar automaticamente o usuário do Telegram após o vencimento do plano)

[ ] Motor de Disparo de Remarketing (Script de background para processar os tempos de disparo configurados e enviar as cópias/mídias via bot)

[ ] Checkout Abandonado Avançado (Identificar quem iniciou o fluxo no Telegram mas não gerou o pagamento para recuperação ativa)

🏗️ Infraestrutura e Escala (Para 10.000+ clientes)
[ ] Modularização (Blueprints) (Dividir o app.py em rotas separadas: auth, finance, bot, admin)

[ ] Migração PostgreSQL (Mudar o SQLite local para um banco de dados em nuvem de alta performance)

[ ] Processamento Assíncrono (Celery + Redis) (Garantir que envios em massa não travem o servidor principal)

🔒 Reforço de Segurança (Hardening)
[ ] Login Captcha (Proteção contra ataques de força bruta automatizados no login)

[ ] Criptografia de HTML (Ofuscação do código fonte no cliente para dificultar a cópia do design/lógica do front)

[ ] 2FA (Autenticação em Duas Etapas) (Token via Telegram ou E-mail para saques e login admin)
