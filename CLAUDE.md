# CLAUDE.md — Regras do Projeto "Numerologia e Luz"

Este arquivo orienta qualquer sessão de IA (Claude Code) que trabalhe neste repositório.
Leia antes de editar qualquer coisa.

---

## 1. O que é este projeto

Site de **uma página**, **estático** e **bilíngue (PT-BR / ES-AR)**, para uma numeróloga.
Tudo vive em `index.html`: marcação, CSS e JavaScript no mesmo arquivo.
O público é Brasil e Argentina, então **todo texto existe em dois idiomas**.

A dona do conteúdo é a numeróloga (cliente). O desenvolvedor é o Rodolfo.

---

## 2. Regras INVIOLÁVEIS (não fazer sem discutir antes)

- ❌ **Não adicionar framework, build, bundler ou backend.** O site é estático de
  propósito (deploy simples e custo zero na Cloudflare Pages). Nada de React, Next,
  Vite, npm, Node, etc.
- ❌ **Não quebrar o arquivo único.** Manter HTML + CSS + JS dentro de `index.html`,
  a menos que o Rodolfo peça explicitamente para separar.
- ❌ **Não alterar a LÓGICA de cálculo numerológico** (ver seção 3). O método foi
  validado com a numeróloga. Mudar a matemática quebra a confiança no produto.
- ❌ **Não alterar os TEXTOS das interpretações** do Karma Destino (Missão, Dons,
  Desafios, Lição Kármica, Palavra-chave). São conteúdo oficial da numeróloga.
- ❌ **Não commitar o número de WhatsApp de teste** (`5500000000000`) como se fosse
  real, nem inventar um número.

---

## 3. Cálculo numerológico — método pitagórico (NÃO MEXER)

Confirmado com a numeróloga. Qualquer mudança aqui precisa de aprovação dela.

**Tabela pitagórica (letra → número):**
```
1: A J S   2: B K T   3: C L U   4: D M V
5: E N W   6: F O X   7: G P Y   8: H Q Z   9: I R
```

**Número de Destino (Karma Destino):** soma TODOS os dígitos da data de nascimento
de uma vez e reduz a um dígito — **exceto 11 e 22, que são números mestres e NÃO
são reduzidos**. (O 33 **não** é tratado como mestre.)
Ex.: 15/05/1985 → 1+5+0+5+1+9+8+5 = 34 → 3+4 = **7**.

**Número de Expressão:** soma o valor pitagórico de todas as letras do nome completo,
mesma regra de redução (preserva 11 e 22).

**Lições Kármicas:** os números de 1 a 9 que **não aparecem** em nenhuma letra do nome.

**Acentos:** removidos antes do cálculo. `á→a`, `ç→c`, `ñ→n`, etc. (função `normalize`).
Isso é essencial para nomes em português e espanhol — não remover esse tratamento.

---

## 4. Bilíngue — regra de ouro

Todo texto visível vem do objeto `I18N`, com chaves `pt` e `es`.
**Ao adicionar ou mudar qualquer texto, atualize SEMPRE os dois idiomas.**
Nunca deixe uma chave só em um idioma. O espanhol é argentino (voseo: "calculá",
"vos", "tu mapa") — manter esse registro.

Estruturas de conteúdo no `<script>`:
- `I18N` → todos os textos da interface
- `DEST` → interpretações ricas do Número de Destino (por idioma)
- `EXPR` → linha de interpretação do Número de Expressão (por idioma)

---

## 5. Identidade visual (preservar)

- Paleta: marfim `#FBF6EE`, roxo profundo `#3A2A5D`, dourado `#B6893A`, lavanda.
- Fontes: **Cormorant Garamond** (títulos) + **Karla** (texto).
- Estética: minimalista com toque espiritual (olho/triângulo, lua, estrela, traços finos).
- Mobile-first. Manter acessível (foco visível, `aria-live` no resultado, contraste).

Não trocar a paleta nem as fontes sem pedido explícito.

---

## 6. Configuração

No topo do `<script>`:
```js
const WHATSAPP = "5500000000000"; // número real entra aqui (só dígitos, com país)
```
Todos os botões de WhatsApp e o resultado da calculadora usam essa constante.

---

## 7. Deploy

- Hospedagem: **Cloudflare Pages** (plano grátis), deploy automático a cada push.
- Sem etapa de build. Output: raiz do repositório.
- Domínio custom apontado no painel do Cloudflare Pages.
- O Rodolfo controla os pushes. Sessões de IA trabalham em branch separado e
  **não fazem merge/PR para a branch principal sem revisão dele**.
