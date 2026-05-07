<div align="center">

# 🎯 Acessibilidade & SEO

### Trabalho prático — Estrutura semântica, acessibilidade WCAG 2.1 AA e SEO técnico

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![WCAG 2.1 AA](https://img.shields.io/badge/WCAG-2.1%20AA-2d5a4a?style=flat-square)
![SEO](https://img.shields.io/badge/SEO-Schema.org-c44d29?style=flat-square)

</div>

---

## 📋 Sobre o projeto

Este repositório contém **dois exercícios práticos** de transformação de páginas web reais — pegando sites com problemas de semântica, acessibilidade e SEO — e reescrevendo-os com:

- ✅ Estrutura semântica HTML5 correta
- ✅ Acessibilidade WCAG 2.1 AA completa
- ✅ SEO técnico (meta tags, Schema.org, hierarquia de headings)
- ✅ Widget de acessibilidade flutuante (alto contraste, fonte ajustável, leitor de tela e mais)

---

## 📁 Estrutura

```
.
├── README.md                       ← Este arquivo  
└── arngren-premium.html           ← Refatoração do site Arngren 
```

---

# Acesse:
https://projeto-melhora-acessibilidade-dev-we.netlify.app/


```

## ✅ Missões cumpridas

Cada arquivo implementa as missões da atividade prática:

| # | Missão | Pontos | Status |
|---|--------|:---:|:---:|
| 1 | **Estrutura Base** — `<header>`, `<main>`, `<footer>` | 2 | ✅ |
| 2 | **Semântica** — substituir `<div>` por tags semânticas | 2 | ✅ |
| 3 | **Acessibilidade** — `alt` em imagens e `<label>` em forms | 2 | ✅ |
| 4 | **SEO** — hierarquia correta de títulos H1→H2→H3 | 1 | ✅ |
| 5 | **Debug** — corrigir erros de semântica e a11y | 3 | ✅ |
| ⭐ | **Missão Secreta** — skip link + `aria-live` | +1 | ✅ |
| **Total** | | **11/10** | 🏆 |

---

## 🛒 Página — Arngren

**Arquivo:** `arngren-premium.html`
**Inspiração:** [arngren.net](https://arngren.net) (e-commerce conhecido pelo design caótico)

### Conceito visual

Reimaginação completa em estética **Editorial Magazine** — fugindo do padrão "AI luxury" (dark + dourado + Cormorant Garamond) que está em todo lugar.

| Elemento | Escolha |
|----------|---------|
| **Paleta** | Creme aquecido (`#f4ede0`) + tinta (`#1a140e`) + terracota (`#c44d29`) |
| **Display** | [Fraunces](https://fonts.google.com/specimen/Fraunces) com `WONK` + `SOFT` variation axes |
| **Body** | [Inter Tight](https://fonts.google.com/specimen/Inter+Tight) |
| **Mono** | [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) para metadados |
| **Layout** | Grid assimétrico estilo revista impressa |
| **Textura** | SVG fractal noise sutil simulando papel |

### Estrutura de seções

```
Ticker (avisos rolando)
└── Header (logo + nav + ações)
    └── Hero editorial (tipografia gigantesca)
        └── Produto destaque com tabela de specs
            └── Strip de categorias numeradas
                └── Catálogo (grid 3 colunas com bordas pretas)
                    └── Sobre (split: texto + números grandes)
                        └── Notas técnicas (blog magazine-style)
                            └── Newsletter
                                └── Footer (5 colunas)
```

---

## ♿ Widget de Acessibilidade

Botão flutuante (FAB) no canto inferior direito que segue o scroll. Inspirado em [VLibras](https://www.gov.br/governodigital/pt-br/vlibras), [UserWay](https://userway.org/) e ferramentas similares de acessibilidade institucional.

### Funcionalidades

#### 📏 Tamanho de fonte
- **A−** Menor (14px)
- **A** Padrão (16px)
- **A+** Maior (18px → 20px → 22px progressivo)

#### 👁️ Visualização
- **Alto contraste** — preto puro + branco + amarelo para máxima legibilidade
- **Inverter cores** — `filter: invert(1) hue-rotate(180deg)`
- **Escala de cinza** — para sensibilidade visual
- **Sublinhar links** — todos os links ganham `text-decoration: underline`

#### 📖 Leitura
- **Espaçamento ampliado** — `letter-spacing` e `line-height` aumentados
- **Modo dislexia** — fonte Verdana + spacing amigável
- **Cursor grande** — cursor SVG amarelo de 44px
- **Pausar animações** — desativa todas as animações e transições

#### 🔊 Leitor de Tela
Usa a [Web Speech API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Speech_API):

```javascript
const utter = new SpeechSynthesisUtterance(texto);
utter.lang = 'pt-BR';
window.speechSynthesis.speak(utter);
```

Quando ativado, qualquer clique em texto da página é lido em voz alta em **português brasileiro**.

#### ↻ Restaurar Padrões
Reseta tudo de uma vez e limpa o `localStorage`.

### Persistência

Todas as preferências são salvas em `localStorage`:

```javascript
function salvar(chave, valor) {
  localStorage.setItem(`a11y_${chave}`, JSON.stringify(valor));
}
```

Quando o usuário volta, suas escolhas continuam ativas.

### Atalhos de teclado

| Atalho | Ação |
|--------|------|
| `Alt + A` | Abrir/fechar painel |
| `Esc` | Fechar painel |
| `Tab` | Navegar entre opções |

---

## 🎯 Acessibilidade — Detalhamento WCAG 2.1 AA

### Perceivable (Perceptível)

- **1.1.1 Conteúdo não-textual** — Todas as imagens têm `alt` descritivo. Ilustrações SVG usam `role="img"` + `aria-label`.
- **1.3.1 Informações e relações** — Estrutura semântica completa: `<header>`, `<main>`, `<footer>`, `<nav>`, `<aside>`, `<article>`, `<section>`, `<time>`, `<figure>`.
- **1.4.3 Contraste** — Combinações de cor verificadas (≥ 4.5:1 para texto normal, ≥ 3:1 para texto grande).

### Operable (Operável)

- **2.1.1 Acessível por teclado** — Todos os elementos interativos focáveis via Tab. Submenus com gerenciamento de foco e tecla `Esc` para fechar.
- **2.4.1 Pular blocos** — Skip link `<a href="#conteudo" class="skip-link">` que aparece ao receber foco.
- **2.4.7 Foco visível** — `:focus-visible` com outline customizado (terracota/dourado, offset).
- **2.5.5 Tamanho de área de toque** — Todos os botões ≥ 44×44 CSS pixels.

### Understandable (Compreensível)

- **3.1.1 Idioma da página** — `<html lang="pt-BR">`.
- **3.3.1 Identificação de erros** — Forms com mensagens via `aria-describedby`.
- **3.3.2 Rótulos ou instruções** — Todos os inputs têm `<label>` associado (visível ou via `sr-only`).

### Robust (Robusto)

- **4.1.2 Nome, função, valor** — Botões-ícone com `aria-label`. Submenus com `aria-expanded` + `aria-haspopup`. Modais com `role="dialog"` + `aria-modal`.
- **4.1.3 Mensagens de status** — `<div role="status" aria-live="polite">` para anúncios dinâmicos (busca, newsletter, mudanças no widget de a11y).

---

## 🔍 SEO — Detalhamento

### Meta tags básicas

```html
<title>Arngren — Drones, Bicicletas Elétricas e RC desde 1983</title>
<meta name="description" content="Loja especializada em drones, bicicletas elétricas..." />
<meta name="robots" content="index, follow, max-image-preview:large" />
<link rel="canonical" href="..." />
```

### Open Graph + Twitter Cards

```html
<meta property="og:type" content="website" />
<meta property="og:title" content="..." />
<meta property="og:description" content="..." />
<meta property="og:locale" content="pt_BR" />
<meta name="twitter:card" content="summary_large_image" />
```

### Schema.org (JSON-LD)

| Tipo | Onde | Função |
|------|------|--------|
| `WebSite` + `SearchAction` | Tecnoblog | Habilita sitelinks searchbox no Google |
| `Organization` | Ambos | Knowledge graph da marca |
| `Store` | Arngren | Marca como e-commerce no rich results |
| `ItemList` + `Product` | Arngren | Lista de produtos indexável |
| `BreadcrumbList` | Ambos | Breadcrumbs no SERP |

### Hierarquia semântica para SEO

Cada página tem **um único H1** descrevendo o conteúdo principal, seguido por H2 (seções) e H3 (artigos/produtos):

```html
<h1>Catálogo de vôo, roda e transmissão</h1>
  <h2>No estoque esta semana</h2>
    <h3>DJI Mini 5 Pro</h3>
    <h3>Stark Eco 2</h3>
  <h2>Loja antiga, cabeça nova</h2>
  <h2>Notas técnicas</h2>
    <h3>Mavic 4 Pro depois de 30 dias</h3>
```

---

## 🎨 Tecnologias e princípios

### HTML
- HTML5 semântico
- Atributos ARIA quando necessário
- Estrutura sem `<div>`-itis

### CSS
- CSS Custom Properties (variáveis) para temas
- Grid + Flexbox para layout
- `clamp()` para tipografia responsiva
- `prefers-reduced-motion` respeitado em todas as animações
- Mobile-first com media queries em breakpoints relevantes

### JavaScript
- Vanilla JS, sem dependências
- Event delegation para performance
- Web Speech API para leitor de tela
- localStorage para persistência

### Princípios de design
- **Tecnoblog:** dark mode informativo (gradientes únicos por notícia, sem dependência de imagens externas)
- **Arngren:** estética editorial print magazine (fugindo do "AI luxury template")

---

## 📐 Decisões de design — Arngren


|---|---|
| Dark + gold | Creme + tinta + terracota |
| "Atelier", "boutique", "premium" | "Loja antiga, cabeça nova" |
| Numerais romanos (— I., II., III.) | "§ 01 — Catálogo" (estilo paragrafo legal) |
| Stats genéricos (42+, 38 países, 4.9/5) | Stats concretos (3 cidades, 5min de resposta) |
| Hero com gradient mesh | Tipografia gigantesca em fundo creme |
| Cards arredondados com gradient | Grid editorial com bordas pretas finas |
| "Tecnologia como *arte*" | "Catálogo de *vôo, roda* e transmissão" |
| Cormorant Garamond | **Fraunces** com `WONK` + `SOFT` axes |
| Em-dashes everywhere | Estrela `★` como indicador |

---
## 🧪 Como testar

### Acessibilidade

1. **Skip link:** Pressione `Tab` ao carregar a página — o link "Pular para o conteúdo principal" aparece no canto superior esquerdo.
2. **Navegação por teclado:** Navegue toda a página usando apenas `Tab` / `Shift+Tab` / `Enter` / `Esc`.
3. **Widget a11y (Arngren):** Clique no botão dourado/preto no canto inferior direito ou pressione `Alt+A`.
4. **Leitor de tela:** Ative no widget e clique em qualquer texto para ouvi-lo.
5. **Validação automática:** Use [Lighthouse](https://developers.google.com/web/tools/lighthouse) ou [WAVE](https://wave.webaim.org/) para auditoria automática.

### SEO

1. **View source:** Veja meta tags, Schema.org no `<head>`.
2. **Hierarquia:** Use a extensão [HeadingsMap](https://chromewebstore.google.com/detail/headingsmap/flbjommegcjonpdmenkdiocclhjacmbi) para visualizar a árvore de headings.
3. **Schema validation:** Cole o JSON-LD em [Schema Markup Validator](https://validator.schema.org/).

---

## 📝 Licença

Projeto educacional. Os logos e nomes "Tecnoblog" e "Arngren" pertencem a seus respectivos donos — usados aqui apenas como referência para o exercício de refatoração.

---

## 👤 Autor

**Jhonathan Magalhães da Cruz**
**Fellipe De Castro**
— Trabalho desenvolvido para disciplina de desenvolvimento web

---

<div align="center">

**Feito com ♿ e foco em acessibilidade.**

</div>
