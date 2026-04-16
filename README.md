🏗️ Stack Tecnológica (Infraestrutura Escalonável)
Backend: Python 3.11, Flask (Arquitetura modularizada com Blueprints).

Banco de Dados: PostgreSQL (Projetado para alta performance, concorrência e transações seguras via Locks).

Mensageria & Filas: Celery + Redis (Processamento assíncrono de webhooks, integrações bancárias e motor de remarketing em background).

Frontend: HTML5, CSS3, Vanilla JS (Design Liquid Glass iOS, 100% responsivo e suporte a PWA com Service Workers).

Gateways de Pagamento: Shark Banking (PIX Nativo, Webhooks HMAC e Saques BRL via API) & Stripe (Checkout global seguro para cartões USD/EUR/GBP).

Storage: AWS S3 (Armazenamento em nuvem via Pre-signed URLs Diretas, aliviando o I/O do servidor).

🌐 Módulo 1: Painel Web (Dashboard & Management)
Interface Liquid Glass iOS: UI premium com abas dinâmicas, glassmorphism real e animações fluidas baseadas no ecossistema Apple.

Criação de Bots com Validação Real-time: Limite de 18 bots por conta com verificação imediata de Token via API oficial do Telegram (get_me()).

Sistema Multimoedas: Pricing dinâmico com conversão simultânea e independente para BRL, USD e EUR na ponta do usuário.

Criação de Produtos Avulsos: Venda de E-books, planilhas ou links externos através de botões de redirecionamento nativos no Telegram.

Remarketing Dinâmico: Motor assíncrono de recuperação de vendas programável por plano, tempo de disparo e segmentação de público (Ativos, Inativos e Abandonos).

Puxada Automática de Dados: O sistema lê os planos e conteúdos cadastrados no banco e gera os cards de oferta automaticamente na interface.

Notificações Push (PWA): Integração via Service Worker e VAPID para avisos nativos e vibrações no celular (Notificação de PIX gerado e Venda Aprovada).

Painel Administrativo "Visão de Deus": Gestão centralizada de lucro líquido, volume total processado, auditoria de Logs de Sistema e controle de IP Banidos.

Central de Atendimento Pró: Ferramenta de inspeção de contas (Score de Risco), aprovação manual de saques integrados à CIP, suspensão de lojas e validação de KYC (Documentos).

Gestão de Equipe: Criação de sub-contas para atendentes com permissões granulares e histórico de logs imutáveis.

🤖 Módulo 2: O Robô do Telegram (Experiência do Cliente)
Comando /start Dinâmico: O bot lê as configurações do banco em tempo real e inicia o atendimento personalizado chamando o cliente pelo nome extraído do payload.

Funil Multi-idioma Automático: Sistema inteligente que pergunta o idioma (PT, EN, ES) via Inline Keyboards e adapta textos, moedas e botões dinamicamente.

Entrega Inteligente de Acessos: Algoritmo que detecta o tipo de produto: entrega links externos protegidos ou gera convites do Telegram de uso único para Grupos/Canais VIP.

Áudios Humanizados: Envio de mensagens de voz nativas (.ogg via send_voice) nos momentos de recepção, conversão e remarketing para aumentar a autoridade e conversão.

Mídia Específica por País: Suporte para imagens e vídeos locais alocados em CDN dependendo do idioma escolhido pelo cliente no funil.

💳 Módulo 3: Gateway de Pagamento & Checkout
Integração Checkout Stripe: Sessões de pagamento seguras via API SDK da Stripe e otimizadas para tráfego internacional.

Sistema PIX Oficial (Shark Banking): Geração nativa e instantânea de código "Copia e Cola" e QR Code dinâmico renderizado dentro do chat.

Motor de Saques via API: Liquidação de saldo direta do painel integrando a chave de saque externa da Shark Banking, acoplada a taxas de antecipação calculadas na ponta.

Blindagem de Webhook: Arquitetura orientada a eventos. O endpoint responde imediatamente "200 OK" para o banco emissor e delega o processamento da liberação de acesso e validação criptográfica (HMAC) para o Celery em background, eliminando falhas por timeouts.

🛡️ Módulo 4: Segurança Industrial e AppSec (O "Cofre")
Isolamento de Chaves (.env): Camada de proteção com variáveis de ambiente injetadas no deploy, mantendo tokens fora do controle de versão.

Criptografia Fail-Safe (Fernet): Tokens de bots e dados bancários sensíveis (PII) dos lojistas armazenados com criptografia simétrica forte de ponta a ponta (Data at Rest).

Prevenção de Saque Duplo (ACID): Travamento em nível de banco de dados (with_for_update()) no processamento do Ledger Financeiro para impedir race conditions em tentativas de saques/transações simultâneas.

Bloqueio IDOR Absoluto: Validação rigorosa em todos os controllers das rotas (middlewares de ownership) garantindo que usuários manipulem estritamente as entidades do próprio user_id.

Rate Limit Inteligente: Proteção via Redis contra ataques de força bruta (Brute Force) e limitação volumétrica em endpoints públicos e webhooks.

Upload Seguro "Magic Bytes": Verificação do DNA binário do payload via python-magic, impedindo bypass de extensão e upload de shells maliciosas no AWS S3.

Proteção Anti-XSS Extrema (Nh3): Sanitização cirúrgica de inputs de texto utilizando a biblioteca Ammonia (núcleo em Rust), blindando contra vetores XSS avançados.

🚧 Roadmap & Próximos Passos
🚪 Pós-Venda e Retenção
[ ] Controle de Recorrência Inteligente (Otimização Celery): Refatoração do script de varredura no Celery Beat (substituindo Table Scans por Queries otimizadas em tempo) para identificar assinaturas e expulsar automaticamente usuários inativos.

[ ] Checkout Abandonado Avançado: Identificação de usuários que abriram o checkout externo (Stripe) mas não concluíram, acionando sequências de recuperação agressiva.

🔒 Reforço de Segurança (Hardening)
[ ] Refatoração do Filtro L7 (IP Banning): Migração das checagens do DB no middleware global HTTP para caching em memória (Redis), mitigando vetores DoS de camada de aplicação.

[ ] Ledger Compliance Universal: Garantir que todas as rotas financeiras sem exceção operem via FinancialEngine, preservando a trilha imutável.

[ ] Login Captcha Invisível: Implementação de Cloudflare Turnstile nas rotas de autenticação.

[ ] Autenticação em Duas Etapas (2FA): Confirmação OTP (E-mail/App) exigida para saques de alto valor e elevação de privilégios de acesso administrativo.
