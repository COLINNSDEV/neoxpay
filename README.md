

## 🏗️ Stack Tecnológica (Infraestrutura Escalonável)

* **Backend:** Python 3.11, Flask (Arquitetura modularizada com Blueprints).
* **Banco de Dados:** PostgreSQL (Projetado para alta performance e concorrência).
* **Mensageria & Filas:** Celery + Redis (Processamento assíncrono de webhooks, entregas e motor de remarketing).
* **Frontend:** HTML5, CSS3, Vanilla JS (Design **Liquid Glass iOS**, 100% responsivo e suporte a PWA).
* **Gateways de Pagamento:** **Shark Banking** (PIX Nativo e Saques BRL via API) & **Stripe** (Checkout global para cartões USD/EUR/GBP).
* **Storage:** AWS S3 (Armazenamento em nuvem de alta disponibilidade para mídias e áudios).

---

## 🌐 Módulo 1: Painel Web (Dashboard & Management)

* **Interface Liquid Glass iOS:** UI premium com abas dinâmicas, glassmorphism real e animações fluidas baseadas no ecossistema Apple.
* **Criação de Bots com Validação Real-time:** Limite de 18 bots por conta com verificação imediata de Token via API oficial do Telegram (`get_me()`).
* **Sistema Multimoedas:** Pricing dinâmico com conversão simultânea e independente para BRL, USD e EUR.
* **Criação de Produtos Avulsos:** Venda de E-books, planilhas ou links externos através de botões de redirecionamento no Telegram.
* **Remarketing Dinâmico:** Motor de recuperação de vendas programável por plano, tempo de disparo e segmentação de público (Ativos, Inativos e Abandonos).
* **Puxada Automática de Dados:** O sistema lê os planos e conteúdos cadastrados no banco e gera os cards de oferta automaticamente na interface.
* **Notificações Push (PWA):** Integração via Service Worker e VAPID para avisos nativos no celular (Notificação de PIX gerado e Venda Aprovada).
* **Painel Administrativo "Visão de Deus":** Gestão centralizada de lucro líquido, volume total processado e controle de taxas da plataforma.
* **Central de Atendimento Pró:** Ferramenta de busca por TX ID (Transaction ID), aprovação manual de saques, suspensão de lojas e reenvio de acessos.
* **Gestão de Equipe:** Criação de sub-contas para atendentes com permissões granulares e controle de exclusão.

---

## 🤖 Módulo 2: O Robô do Telegram (Experiência do Cliente)

* **Comando /start Dinâmico:** O bot lê as configurações do painel em tempo real e inicia o atendimento personalizado chamando o cliente pelo nome.
* **Funil Multi-idioma Automático:** Sistema inteligente que pergunta o idioma (PT, EN, ES) e adapta textos, moedas e botões dinamicamente.
* **Entrega Inteligente de Acessos:** Algoritmo que detecta o tipo de produto: entrega links externos protegidos ou gera convites de uso único para Grupos/Canais VIP.
* **Áudios Humanizados:** Envio de mensagens de voz nativas (.ogg) nos momentos de recepção, conversão e remarketing para aumentar a autoridade.
* **Mídia Específica por País:** Suporte para imagens e vídeos diferentes dependendo do idioma escolhido pelo cliente no funil.

---

## 💳 Módulo 3: Gateway de Pagamento & Checkout

* **Integração Checkout Stripe:** Sessões de pagamento seguras e otimizadas para tráfego internacional e cartões de crédito.
* **Sistema PIX Oficial (Shark Banking):** Geração nativa e instantânea de código "Copia e Cola" e QR Code dinâmico.
* **Motor de Saques via API:** Liquidação de saldo direta do painel (após aprovação administrativa) integrando a chave de saque externa da Shark Banking.
* **Blindagem de Webhook:** Arquitetura orientada a eventos (Celery) para dar resposta imediata de "200 OK" aos gateways e processar a entrega em background, eliminando timeouts.

---

## 🛡️ Módulo 4: Segurança Industrial e AppSec (O "Cofre")

* **Isolamento de Chaves (.env):** Camada de proteção para credenciais de API, senhas de banco e chaves criptográficas fora do código-fonte.
* **Criptografia Fail-Safe (Fernet):** Tokens de bots e dados sensíveis dos lojistas armazenados com criptografia simétrica de ponta a ponta.
* **Prevenção de Saque Duplo:** Travamento de banco via `with_for_update()` para impedir "race conditions" em tentativas de saques simultâneos.
* **Bloqueio IDOR Absoluto:** Validação rigorosa em todas as rotas garantindo que usuários acessem apenas dados vinculados ao seu próprio `user_id`.
* **Rate Limit Inteligente:** Proteção contra ataques de força bruta (Brute Force) no login e em endpoints públicos de pagamento.
* **Upload Seguro "Magic Bytes":** Verificação do DNA binário do arquivo, impedindo o upload de scripts maliciosos disfarçados de imagem no AWS S3.
* **Proteção Anti-XSS (Bleach):** Sanitização cirúrgica de inputs de texto, permitindo apenas as tags HTML seguras aceitas pelo Telegram.

---

## 🚧 Roadmap & Próximos Passos

### 🚪 Pós-Venda e Retenção
- [ ] **Controle de Recorrência Inteligente:** Script de varredura (Celery Beat) para identificar assinaturas vencidas e expulsar automaticamente o usuário via API.
- [ ] **Checkout Abandonado Avançado:** Identificação de usuários que abriram o checkout externo mas não concluíram, acionando recuperação agressiva.

### 🔒 Reforço de Segurança (Hardening)
- [ ] **Login Captcha Invisível:** Implementação de Cloudflare Turnstile ou reCAPTCHA v3 nas rotas de autenticação.
- [ ] **Autenticação em Duas Etapas (2FA):** Confirmação via código para saques de alto valor e acesso administrativo.
- [ ] **Ofuscação de Front-end:** Proteção extra do código JS para dificultar engenharia reversa do design exclusivo.

---

> **Desenvolvido para máxima performance e conversão.** NeoxPay V2 — Redefinindo o padrão de vendas no Telegram.
