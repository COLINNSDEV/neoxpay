## 📜 Registro de Atualizações (Changelog)

### 📅 [17/04/2026] - Refatoração Enterprise, Hardening & Escalabilidade
Nesta data, a base de código passou por uma auditoria crítica de segurança e arquitetura. O sistema evoluiu de uma base funcional para uma infraestrutura de alta disponibilidade (*Production-Ready*), mitigando vetores críticos da OWASP e eliminando gargalos de banco de dados.

**🔐 Segurança Extrema (AppSec)**
* **Anti-LFI (Local File Inclusion):** Blindagem Crítica na rota de envio de mídias do Telegram (`safe_media_sender`) com fronteiras estritas (`os.path.commonpath`), erradicando vetores de *Path Traversal* (Tentativas de ler `/etc/passwd` ou `.env`).
* **Prevenção de Account Takeover (ATO):** Implementação de trava rigorosa de segurança (mínimo de 8 caracteres) nas rotas de registro.
* **Mitigação de Timing Attacks:** Injeção de *Dummy Hashes* (Scrypt) nas rotas de login para cegar ferramentas automatizadas que tentam enumerar e-mails válidos através de análise de latência.
* **Blindagem de Storage (AWS S3):** Proteção contra *Stored XSS / HTML Smuggling* forçando a diretiva `Content-Disposition: attachment` nas *Pre-signed URLs*, obrigando o download seguro de arquivos mascarados.
* **Filtro L7 Anti-DoS:** Migração da validação de *Blacklist* de IPs do PostgreSQL para Cache em Memória (RAM L1 com TTL), blindando o *Connection Pool* do banco contra ataques volumétricos.

**⚡ Performance e Otimização de Banco de Dados**
* **Fim dos Table Locks (O(N) ➡️ O(log N)):** Arquitetura do CRON de expulsões reconstruída. Adição da coluna indexada `expires_at` e adoção do padrão *Fetch-Process-Update*, zerando os bloqueios de tabelas do PostgreSQL durante chamadas lentas à API do Telegram.
* **Prevenção de Over-fetching (Economia de RAM):** Otimização profunda de *Eager Loading* (`joinedload`) nos webhooks do bot. Queries pesadas agora são acionadas exclusivamente em interações de menu (ignorando mensagens de chat de texto puro).
* **Otimização Criptográfica:** Refatoração do motor `Fernet` para o padrão *Singleton*, eliminando o desperdício de CPU gerado pela recriação em loop de instâncias de criptografia, incluindo suporte a *Key Rotation* via `MultiFernet`.

**🧱 Arquitetura Limpa e Padrões SOLID**
* **Padrão Factory (Princípio OCP):** Desacoplamento de Gateways de Pagamento com a criação da `PaymentProviderFactory`. O orquestrador do Telegram tornou-se 100% agnóstico a regras específicas de processamento de moedas (BRL/USD/EUR).
* **Erradicação de Fat Controllers:** Lógicas pesadas de agrupamento e Queries N+1 extraídas dos Controladores HTTP para o `AdminService`.
* **Fim dos Imports Circulares:** Substituição de dependências acopladas por injeção direta *Out-of-Band* no barramento de mensageria (`celery_app.send_task`).
* **Thread-Safety (Concorrência Segura):** Implementação de `threading.local()` nas sessões HTTP das adquirentes, prevenindo corrupção de sockets TLS/SSL cruzados (`Connection reset by peer`) no Gunicorn.
* **Estabilidade de Sessões de Admin:** Fixação do paradigma *Fail-Fast* para a variável `FLASK_SECRET_KEY`, evitando logoffs em massa (invalidação de *cookies*) durante reinicializações da infraestrutura.

**⚖️ Compliance (LGPD & GDPR)**
* **Data Minimization:** Refatoração nos Webhooks da Stripe e SharkHub. Os *logs* em nuvem agora filtram e registram estritamente metadados de correlação sistêmica, destruindo PIIs sensíveis (CPFs, Nomes e E-mails) em memória antes da gravação em disco.
