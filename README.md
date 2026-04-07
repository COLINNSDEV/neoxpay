
Seu projeto evoluiu absurdamente desde a primeira versão. Nós saímos de um script simples com SQLite para uma arquitetura escalável em nuvem, com banco de dados robusto (PostgreSQL), filas de processamento assíncrono (Celery + Redis), integração com a Shark Banking e uma interface PWA padrão Apple.

Aqui está o seu README.md completamente atualizado, refletindo o verdadeiro poder do sistema que construímos até agora. É só copiar e colar no seu GitHub:

🚀 NeoxPay - Gateway & Telegram Automation Hub
A NeoxPay é uma infraestrutura de pagamentos e automação de vendas focada no ecossistema do Telegram. Desenvolvida para lojistas e infoprodutores que desejam escalar operações globais, a plataforma une a gestão de checkouts multimoeda (BRL, USD, EUR) com a entrega automatizada de acessos a grupos VIP e conteúdos exclusivos, tudo através de uma interface PWA ultrarrápida estilo Liquid Glass iOS.

🏗️ Stack Tecnológica (Infraestrutura Escalonável)
Backend: Python 3.11, Flask (Modularizado com Blueprints)

Banco de Dados: PostgreSQL (Alta performance e concorrência)

Mensageria & Filas: Celery + Redis (Processamento assíncrono de webhooks e remarketing)

Frontend: HTML5, CSS3, Vanilla JS (Design Liquid Glass, responsivo e PWA)

Gateways: Shark Banking (PIX e Saques BRL) & Stripe (Cartões USD/EUR)

Storage: AWS S3 (Armazenamento em nuvem para mídias e áudios)

🌐 Módulo 1: Painel Web (Dashboard & Management)
[x] Interface Liquid Glass iOS: UI premium com abas dinâmicas, glassmorphism e animações fluidas.

[x] Criação de Bots com Validação Real-time: Limite de 18 bots por conta com verificação imediata do Token na API do Telegram (via get_me()).

[x] Sistema Multimoedas: Pricing dinâmico com conversão simultânea para BRL, USD e EUR.

[x] Criação de Produtos Avulsos: Venda de E-books, planilhas ou links externos via botões no Telegram.

[x] Remarketing Dinâmico: Motor de recuperação de vendas programável por plano, tempo de disparo e público-alvo (Ativos, Inativos, Abandonos).

[x] Puxada Automática de Dados: O sistema lê os planos e conteúdos do bot e gera os cards de oferta automaticamente.

[x] Notificações Push (PWA): Integração via Service Worker e VAPID para avisos nativos no celular (PIX gerado, Venda Aprovada).

[x] Painel Administrativo "Visão de Deus": Gestão de lucro líquido, volume total e controle de taxas da plataforma.

[x] Central de Atendimento Pró: Busca por TX ID, aprovação manual de saques, suspensão de lojas e reenvio de acessos.

[x] Gestão de Equipe: Criação de sub-contas (Atendentes) com permissões granulares e exclusão.

🤖 Módulo 2: O Robô do Telegram
[x] Comando /start Dinâmico: O bot lê as configurações do painel em tempo real e chama o cliente pelo nome.

[x] Funil Multi-idioma Automático: Pergunta o idioma (PT, EN, ES) e altera textos, moedas e botões dinamicamente.

[x] Entrega Inteligente de Acessos: Se o painel contiver um link externo (Ex: Google Drive, Instagram), o bot entrega um botão de redirecionamento. Caso contrário, gera um convite de uso único para o Grupo VIP.

[x] Áudios Humanizados: Envio de mensagens de voz nativas (.ogg) na recepção, conversão e remarketing.

[x] Mídia Específica por País: Suporte para imagens e vídeos diferentes dependendo do idioma escolhido pelo cliente.

💳 Módulo 3: Gateway de Pagamento
[x] Integração Checkout Stripe: Sessões seguras para tráfego internacional (USD/EUR).

[x] Sistema PIX Oficial (Shark Banking): Geração nativa de código Copia e Cola e QR Code.

[x] Motor de Saques via API: Liquidação de saldo direto do painel (com aprovação de administradores) integrando a chave de saque externo da Shark.

[x] Blindagem de Webhook: Threads Nativas do Python para dar resposta imediata de "200 OK" à Stripe/SharkBanking e enviar o processamento de entrega para background sem travar a API.

⚙️ Módulo 4: Arquitetura e Escala (Performance)
[x] Modularização (Blueprints): Código reestruturado separando rotas públicas, painel, admin, background tasks e banco de dados.

[x] Processamento Assíncrono (Celery + Redis): Motor pesado rodando em background para disparar centenas de mensagens de remarketing sem derrubar o servidor Flask.

[x] Migração para PostgreSQL: Saída do SQLite para suporte a milhares de requisições simultâneas em produção.

🛡️ Módulo 5: Segurança Industrial e AppSec (O "Cofre")
[x] Isolamento de Chaves (.env): Senhas, APIs da Shark/Stripe e chaves VAPID ocultas do código-fonte.

[x] Criptografia Fail-Safe (Fernet): Tokens de bots dos lojistas armazenados com criptografia de ponta a ponta no banco.

[x] Prevenção de Saque Duplo: Travamento de banco with_for_update() para impedir "race conditions" em saques simultâneos.

[x] Bloqueio IDOR Absoluto: Validação rigorosa garantindo que lojistas só acessem ou deletem dados (Bots, Campanhas, Saques) vinculados ao seu próprio user_id.

[x] Rate Limit Inteligente: Bloqueio contra ataques de força bruta no login e em endpoints públicos.

[x] Upload Seguro "Magic Bytes": O sistema ignora a extensão do arquivo e lê o DNA binário, impedindo upload de scripts maliciosos disfarçados de imagem no AWS S3.

[x] Proteção Anti-XSS (Bleach): Sanitização cirúrgica de inputs de texto (mensagens do bot), permitindo apenas tags HTML seguras aceitas pelo Telegram.

🚧 O QUE FALTA (Roadmap & Próximos Passos)
🚪 Pós-Venda e Retenção
[ ] Controle de Recorrência Inteligente: Script de varredura (Celery Beat) para identificar assinaturas vencidas e expulsar automaticamente o usuário do grupo no Telegram via API.

[ ] Checkout Abandonado Avançado: Identificar usuários que clicaram no botão de pagamento dentro da Stripe/Shark mas fecharam a aba, acionando um script de recuperação agressiva no Telegram.

🔒 Reforço de Segurança (Hardening Front-end)
[ ] Login Captcha Invisível: Implementação de Cloudflare Turnstile ou reCAPTCHA v3 na rota de login e registro.

[ ] Autenticação em Duas Etapas (2FA): Confirmação via código no E-mail para permitir saques altos e acesso ao painel de Administrador.

[ ] Criptografia de Front-end: Ofuscação pesada do HTML/JS para dificultar engenharia reversa do design exclusivo Liquid Glass.
