# Numerologia e Luz

Site institucional de numerologia pitagórica, bilíngue (Português 🇧🇷 / Espanhol 🇦🇷).
Oferece um **cálculo gratuito** (Número de Destino, Número de Expressão e Lições Kármicas)
como porta de entrada, e três **cartas numerológicas pagas** solicitadas via WhatsApp.

---

## ⚠️ Antes de publicar — 2 ajustes obrigatórios

Abra o `index.html` e procure por:

1. **Número de WhatsApp** — no topo do `<script>`:
   ```js
   const WHATSAPP = "5500000000000"; // ← TROCAR pelo número real
   ```
   Formato: código do país + DDD + número, **só dígitos**.
   Ex.: Brasil (91) 99999-9999 → `5591999999999` · Argentina 11 5555-5555 → `5491155555555`

2. **Preço da Carta Essencial em espanhol** — no dicionário `es`, dentro de `prices`:
   ```js
   prices:{essencial:"Consultar", ...}  // ← definir o valor em AR$
   ```

---

## Stack

- **HTML + CSS + JavaScript puro**, tudo em **um único arquivo** (`index.html`).
- **Sem build, sem dependências, sem backend.** A calculadora roda 100% no navegador.
- Fontes via Google Fonts (Cormorant Garamond + Karla).

## Rodar localmente

É só abrir o `index.html` no navegador. Ou, para servir num endereço local:

```bash
python3 -m http.server 8080
# abre http://localhost:8080
```

## Deploy (Cloudflare Pages)

1. Suba este repositório no GitHub.
2. No Cloudflare → **Pages** → **Connect to Git** → selecione o repositório.
3. Build settings: **deixe tudo em branco** (não há build).
   - Framework preset: `None`
   - Build command: *(vazio)*
   - Output directory: `/`
4. Salve. A cada `push`, o Cloudflare publica automaticamente.
5. **Custom domain** → aponte `numerologiaeluz.com.br` (ou `.com`) para o projeto.

## Estrutura

```
numerologia-e-luz/
├── index.html     ← o site inteiro (marcação + estilo + lógica)
├── README.md
└── CLAUDE.md      ← regras do projeto para sessões de IA
```

## Conteúdo numerológico

Método **pitagórico**. As interpretações do Karma Destino (Missão, Dons, Desafios,
Lição Kármica) foram fornecidas pela numeróloga e **não devem ser alteradas** sem
a aprovação dela. Detalhes do método em `CLAUDE.md`.
