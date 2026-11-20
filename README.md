# Grão Nobre Roastery & Bistrô — `grao-nobre-roastery`

[![Enterprise CI, Firebase TLS, OWASP & LGPD](https://img.shields.io/badge/Testes_Automatizados-20%2F20_Passing-10B981?style=for-the-badge&logo=githubactions&logoColor=white)](https://github.com/nonscs813-a11y/grao-nobre-roastery)
[![Firebase TLS 1.3](https://img.shields.io/badge/Firebase_Firestore-TLS_1.3_%26_Circuit_Breaker-FFCA28?style=for-the-badge&logo=firebase&logoColor=black)](https://github.com/nonscs813-a11y/grao-nobre-roastery)
[![OWASP Top 10](https://img.shields.io/badge/Segurança-OWASP_Top_10_%26_CSP-0EA5E9?style=for-the-badge)](https://github.com/nonscs813-a11y/grao-nobre-roastery)
[![LGPD Privacy-by-Design](https://img.shields.io/badge/Privacidade-LGPD_Art._6_7_18-8B5CF6?style=for-the-badge)](https://github.com/nonscs813-a11y/grao-nobre-roastery)

> **Sistema Web Empresarial 10/10** para **Cafés Especiais & Reserva de Mesas** — Desenvolvido com **1 arquivo HTML (`index.html`) + 1 arquivo CSS (`styles.css`) + 1 arquivo JavaScript (`app.js`) + Transporte Seguro Firebase Cloud Firestore v1 (`reservas_cafeteria`)**, blindagem **OWASP Top 10**, conformidade **LGPD (Privacy-by-Design)** e **20 testes automatizados (`node --test`)**.

🌐 **Aplicação Ao Vivo (Produção):** [**`https://nonscs813-a11y.github.io/grao-nobre-roastery/`**](https://nonscs813-a11y.github.io/grao-nobre-roastery/)

---

## 🔥 Arquitetura de Conexão Segura Firebase Cloud (Zero-Trust & TLS 1.3)

1. **Validação Anti-SSRF e Enforcement TLS 1.3 (`validateFirebaseEndpoint`):** Bloqueia conexões `http://`, credenciais embutidas em URL e qualquer domínio fora da whitelist oficial do Google Cloud (`firestore.googleapis.com`, `firebaseio.com`, `identitytoolkit.googleapis.com`).
2. **Protocolo Oficial Google Cloud Firestore v1 (`toFirestoreDocument` / `fromFirestoreDocument`):** Serialização tipada (`fields.stringValue`, `booleanValue`, `timestampValue`) com verificação automática de assinatura criptográfica FNV-1a 64-bit na leitura e na escrita.
3. **Injeção Segura de Tokens (`buildSecureHeaders`) & Zero Credenciais Expostas:** Suporte nativo a `Authorization: Bearer <idToken>` e `X-Firebase-AppCheck`, auditado pelo scanner automatizado de segredos (*Secret Leak Scanner* — Teste #10).
4. **Circuit Breaker (`CloudCircuitBreaker`) + `AbortController` Timeout (4.5s):** Protege a aplicação contra lentidão de rede, transicionando automaticamente entre `CLOSED`, `OPEN` e `HALF_OPEN` com persistência local assinada criptograficamente.

---

## 🧪 Suíte de 20 Testes Automatizados (`tests/enterprise.test.js`)

```bash
npm test
# ou diretamente:
node --test tests/enterprise.test.js
```

Todos os **20 testes automatizados** (XSS, Vetores de Injeção, NoSQLi/Prototype Pollution, RateLimiter, Hash FNV-1a, Validação Firebase TLS 1.3 & Anti-SSRF, Serialização Firestore v1 Wire Format, CloudCircuitBreaker, Headers Auth/AppCheck, Secret Leak Scanner, Mascaramento de PII LGPD, Consentimento Obrigatório LGPD, Limites de Schema, Injeção em Formulário, Motor Financeiro em Centavos, Roundtrip Monetário, Persistência CRUD Firebase, Direito ao Esquecimento LGPD, Auditoria HTML/CSP/WCAG e Auditoria Firestore Rules/HSTS) passam com **100% de aprovação**.

---

## 📋 Catálogo Operacional Configurado

| ID | Serviço / Solução | Categoria | Duração / Ref | Valor |
| :-: | :--- | :---: | :---: | :---: |
| `s1` | **Brunch Grão Nobre para 2 Pessoas (Croissant, Ovos Benedict, Frutas & 2 Filtrados)** | `Brunch` | `Serve 2` | **R$ 138,00** |
| `s2` | **Voo de Degustação de Cafés Especiais (3 Métodos: V60, Aeropress & Prensa)** | `Cafés SCA` | `Experiência` | **R$ 54,00** |
| `s3` | **Tostex Rústico de Sourdough com Queijo Brie, Presunto Parma & Mel** | `Salgados` | `Individual` | **R$ 46,00** |
| `s4` | **Cheesecake Basco Queimado com Calda Quente de Frutas Vermelhas** | `Confeitaria` | `Fatia Generosa` | **R$ 34,00** |
| `s5` | **Pacote Grão em Casa — Microlote Geisha 89 Pontos (250g em Grãos ou Moído)** | `Empório` | `Torra Fresca` | **R$ 68,00** |
| `s6` | **Workshop Barista por 1 Dia (Extração de Espresso & Latte Art)** | `Cursos` | `3 Horas` | **R$ 280,00** |

---

**Arquitetura e Engenharia Web Sênior por [Julio Cesar (`@nonscs813-a11y`)](https://github.com/nonscs813-a11y)**
