# CSS

## 🧱 O que é CSS

CSS (Cascading Style Sheets ou Folhas de Estilo em Cascata) é uma linguagem de estilo usada para descrever a apresentação HTML ou XML.
Ela controle como os elementos são exibidos e estruturados a fim de assegurar uma aparência visual atraente e consistente.
História e Evolução:

- CSS1 (1996): Primeira versão, focada em formatação básica de texto e cores.
- CSS2 (1998): Adicionou recursos como posicionamento absoluto e suporte a media types.
- CSS3: Dividida em módulos independentes (como animações, grids e flexbox), permitindo evolução contínua e incremental

## 📐 Sintaxe Básica do CSS

Uma regra do CSS é composta por um seletor e um bloco de declarações.
Cada declaração inclui uma propriedade e um valor, os quais são separados por um valor e terminados com ponto e vírgula

```css
selector{
    propriedade: valor;
}
```

Seletores são usados para direcionar elementos específicos no HTML. Eles podem ser:

- Seletores de elemento: ```p { }``` (seleciona todos os parágrafos).
- Seletores de classe: ```.classe { }``` (seleciona elementos com a classe especificada).
- Seletores de ID: ```#id { }``` (seleciona um elemento com o ID especificado).
- Seletores de atributo: ```[type="text"] { }``` (seleciona elementos com atributos específicos).
- Pseudo-classes: ```a:hover { }``` (seleciona elementos em estados específicos)

Além disso, o CSS usa o conceito de Box Model, no qual cada elemento é tratado como uma caixa composta por:

- **Conteúdo**: Área onde o texto e imagens são exibidos.
- **Padding**: Espaço entre o conteúdo e a borda.
- **Border**: Linha que envolve o padding e o conteúdo.
- **Margin**: Espaço externo que separa o elemento de outros elementos

Exemplo:

```css
div {
    width:300px;
    padding: 20px;
    border: 5px solid #000;
    margin: 10px;
}
```

## Seletores e Especicidade do CSS

Dentro do CSS, os Seletores são padrões que nos permitem selecionar e estilizar elementos HTML específicos em uma página Web. Eles são o mecanismo fundamental que vincula a estrutura HTML à apresentação visual.

**Função Principal** -> Direcionar estilos para elementos específicos sem alterar a estrutura HTML subjacente.


| Tipo             | Exemplo            | Seleciona                                           |
| ---------------- | ------------------ | --------------------------------------------------- |
| Universal        | *                  | Todos os elementos                                  |
| Por tipo         | p                  | Todas as tags `<p>`                                 |
| Classe           | .destaque          | Elementos com class="destaque"                      |
| ID               | #menu              | Elemento com id="menu"                              |
| Atributo         | input[type="text"] | Inputs do tipo texto                                |
| Descendente      | div p              | Todos os `<p>` dentro de `<div>`                    |
| Filho direto     | div > p            | `<p>` que são filhos diretos de `<div>`             |
| Adjacente        | h1 + p             | O `<p>` imediatamente após um `<h1>`                |
| Irmão geral      | h1 ~ p             | Todos os `<p>` que são irmãos posteriores de `<h1>` |
| Pseudo-classes   | a:hover            | Links ao passar o mouse                             |
| Pseudo-elementos | p::first-line      | Primeira linha de um `<p>`                          |

Exemplo:

```css
/* Seletor de elemento/tag */
p {
  color: blue;
}

/* Seletor de classe */
.destaque {
  background-color: yellow;
}

/* Seletor de ID */
#header {
  padding: 20px;
}

/* Seletor universal */
* {
  box-sizing: border-box;
}

/* Elementos com atributo específico */
[disabled] {
  opacity: 0.5;
}

/* Atributo com valor exato */
[type="text"] {
  border: 1px solid #ccc;
}

/* Atributo que contém valor */
[class*="btn"] {
  cursor: pointer;
}

/* Atributo que começa com valor */
[href^="https"] {
  color: green;
}

/* Atributo que termina com valor */
[src$=".jpg"] {
  border: 2px solid #ddd;
}

/* Descendente (espaço) */
div p {
  line-height: 1.6;
}

/* Filho direto (>) */
ul > li {
  list-style-type: square;
}

/* Irmão adjacente (+) */
h2 + p {
  margin-top: 0;
}

/* Irmão geral (~) */
h2 ~ p {
  color: #666;
}
```

## ⚖️ Especificidade: A Hierarquia do CSS

Além disso, existem casos aonde dois ou mais seletores aplicam estilos ao mesmo elemento, logo, o navegador precisa decidir qual regra vence.
Tal decisão é norteada pela Especificidade

Em suma, a **especificidade** determina qual regr CSS será aplicada quando múltiplas regras conflitantes se aplicam ao mesmo elemento.
Assim, A **especificidade** é calculada como uma "pontuação", seguindo esta lógica:

- Inline styles (atributo style="" no HTML) → têm a maior prioridade (1000 pontos)
- IDs → cada um vale 100 pontos
- Classes, atributos e pseudo-classes → cada um vale 10 pontos
- Elementos e pseudo-elementos → cada um vale 1 ponto
- Universal () → 0 pontos
- !important → sobrepõe qualquer especificidade (mas deve ser usado com MUITA cautela)

Exemplos:

```css
<p id="texto" class="destaque">Olá, mundo!</p>
```

---

```css
p { color: blue; }         /* especificidade: 1 */
.destaque { color: green; } /* especificidade: 10 */
#texto { color: red; }      /* especificidade: 100 */
```

O texto ficará **vermelho**, pois o seletor **#texto tem maior especificidade**

Ademais, dentro do CSS, quando dois seletores possuem a mesma especificidade, 
o navegador passa a aplicar a regra que aparece dentro do bloco de código

Por Exemplo...

```css
p { color: blue; }
p { color: orange; }
```

Aqui o Texto será **Laranja**

## Variáveis CSS

Variáveis CSS, ou Custom Properties, permitem armazenar valores reutilizáveis em folhas de estilo, facilitando a manutenção e atualização de propriedades como cores, 
tamanhos ou espaçamentos. 

Introduzidas no CSS Custom Properties Module Level 1, 

Diferente de variáveis em preprocessadores como Sass, as variáveis CSS são dinâmicas, podem ser manipuladas 
via **JavaScript** e respeitam a cascata e herança do CSS.

O MDN destaca que variáveis CSS são especialmente úteis para temas (ex.: modo claro/escuro), design systems e responsividade. 
O W3C enfatiza que são propriedades CSS comuns, sujeitas a herança e especificidade.

Sintaxe Básica

```css
/* Definir variável */
:root {
  --nome-da-variavel: valor;
}

/* Usar variável */
.elemento {
  propriedade: var(--nome-da-variavel, valor-fallback);
}
```

Valores Possíveis:

- Nome: Deve começar com ``-- (ex.: --cor-primaria)``. Sensível a maiúsculas/minúsculas; não pode ser none ou palavras reservadas.
- Valor: Qualquer valor CSS válido ```(ex.: #ff0000, 16px, 1.5rem, linear-gradient(red, blue))```. Pode incluir outras variáveis.
- Escopo: Definidas em ```:root (global)``` ou seletores específicos (local). Herdam pela cascata.
- Fallback: Em ```var(--nome, fallback)```, o **fallback é usado se a variável não existe ou é inválida**.
- Globais: ```initial```, ```inherit```, ```unset```, ```revert```, ```revert-layer``` podem ser usados, mas raramente em variáveis.

## Unidade de Medida CSS 

As Unidades de Medida no CSS definem tamanhos para propriedades como width, height, font-size, margin, padding, border-radius, etc.

Elas permitem que elementos se adaptem a diferentes dispositivos, resoluções e preferências do usuário.

O CSS suporta dezenas de unidades, divididas em absolutas (fixas) e relativas (dependentes de contexto)

**OBSERVAÇÃO**

```bash
Unidades são obrigatórias para valores numéricos (exceto 0, que pode ser 0 sem unidade). Valores negativos são permitidos em algumas propriedades 
(ex: margin: -10px; para sobreposições)
```

Unidades são categorizadas pelo seu comportamento. Assim, cabe ao Dev escolher com base no contexto: fixo para impressos, relativo para responsividade.

### 📏 **Unidades Absolutas (Fixas, Independentes de Contexto)**  

Essas são constantes, baseadas em medidas físicas. Ideais para cenários controlados, como PDFs ou designs impressos, mas ruins para telas variáveis.

- px (pixels) → Unidade base do CSS. 1px = 1/96 de polegada (aprox. 0.26mm). É "absoluto" em telas, mas escalável com zoom do navegador.
- Ex: font-size: 16px; .
- pt (points) → De tipografia. 1pt = 1/72in ≈ 0.35mm; 1pc = 12pt. Comum em documentos.
- cm (centímetros) → Medidas reais. 1in = 2.54cm = 96px. Úteis para @media print.
- Ex: width: 21cm; para A4 em impressão.

### 📏 *Unidades Relativas (Dependentes de Contexto)** 

Essas se adaptam ao pai, viewport ou fonte base, promovendo designs fluidos.

- em → Relativo ao font-size do elemento pai. 1em = font-size do pai.

```bash
Ex: Se pai tem font-size: 16px;, padding: 1em; = 16pxVantagem: Composto – se ancestral mudar, propaga.Armadilha: "Efeito cascata" pode causar tamanhos imprevisíveis em aninhamentos profundos.
```

- rem (root em) → Relativo ao font-size do :root (geralmente html, padrão 16px). Ignora herança local. Ex: font-size: 1.5rem; = 24px se root for 16px.Melhor prática: Defina - - html **{ font-size: 62.5%; }** -> para rem fácil (1rem = 10px).Ideal para acessibilidade –> usuários podem ajustar a fonte base.
- % (percentual) → Relativo ao pai. Para width, é % da largura do pai; para font-size, % do pai. Ex: width: 50%; = metade do container.
    * Armadilha: .Em posições absolutas, % pode referenciar viewport.

### 📏 **Unidade de Viewport (Relativa à Tela)** 

Perfeitas para responsividade full-screen.

- vw, vh → 1vw = 1% da largura da viewport; 1vh = 1% da altura.
- Ex: height: 100vh; para full-height.
- Armadilha: Em mobiles, vh inclui barras de navegador – pode causar overflow.
- vmin, vmax → 1vmin = 1% do menor lado (width ou height); vmax do maior. Útil para quadrados responsivos: width: 50vmin;height: 50vmin; 

Além disso, o CSS dispõe de uma função qie executa cálculos ao especificar valores de propriedades, que no caso é o calc() .

```bash
A função calc() recebe uma única expressão como parâmetro, e o resultado da expressão é usado como valor para uma propriedade CSS. Nesta expressão, o operando pode ser combinado usando os operadores aritméticos
```

Exemplos

```css
calc(100% - 80px)

calc(100px * sin(pi / 2))

calc(var(--hue) + 180)

lch(from aquamarine l c calc(h + 180))
```

--- 

## ⚙ Propriedades CSS

Uma propriedade CSS trata-se de um atributo de estilos que iremos aplicar em elemento que, anteriormente, foi demarcado via HTML.

### 🖌 Propriedade Color

A propriedade ***color*** define a cor do conteúdo de algum elemento, além de determinar o valor de ***currentColor*** usado em outras propriedades - bordas, sombras e afins.

O CSS aceita uma variedade de notações dos quais destacam-se…

- Named Colors
    * Exemplos: red, blue, transparent , receccapurple
    * São 140 nomes definidos pela especificação CSS

- Hexadecial

    * Notação mais usada e clássica
    * Representa valores em base 16 para vermelho, verde e Azul
    * Com Alpha → Os últimos dois dígitos indicam transparência (AA)

- RGB E RGBA
    * Definem valores de vermelho, verde e azul de 0 a 255
    * rgba()  adiciona canal ** alfa** (opacidade).

- HSL e HSLA

    * HSL = Hue (matiz, 0–360°), Saturation (%), Lightness (%)
    * Fácil para gerar variações de tom/clareza
    * hsla() inclui transparência

Exemplos:

```css
p { 
	color: #1a73e8; 
}

h1 { 
	color: rgb(26 115 232); 
}

small { 
	color: hsl(210 90% 57% / 0.9); 
}

.box { 
	color: #0f0a; /* #RGBA shorthand, alpha incluso */ 
}
```

---

### 🖼 Propriedade Background

A propriedade background controla tudo que pinta atrás do conteúdo do elemento, isto é, trata-se do versionamento de estilos que compõem 
o interior de um elemento, como cor, imagens, repetição, posionamento, tamanho, origem, área de pintada e afins.

A forma abreviada { backgound } junta várias propriedades em uma linha; quando usada, componentes não especificados voltam aos seus valores padrão.

### ***Subpropriedades de Background…***

- background-color → cor da camada mais inferior (aceita todo tipo de notação <color>).

- background-image → um ou mais images (URLs, gradientes, image-set(), element(), image() e paint worklets). Camadas separadas por vírgula; a primeira declarada fica no topo.

- background-position → posição (palavras-chave, percentuais, valores em px, calc() etc.).

- background-size → auto, cover, contain ou valores <width> <height>. Quando usado no shorthand com background-position, vem depois de uma barra /. (ex.: background: url(...) center / cover no-repeat;)

- background-repeat → repeat, no-repeat, space, round, e variantes repeat-x/repeat-y.

- background-attachment → scroll, fixed, local (controla se a imagem fica fixa no viewport, no bloco, ou “grudada” ao conteúdo rolável). Use com cuidado no mobile           (comportamentos e limitações).

- background-origin → define a caixa usada para posicionamento: border-box | padding-box | content-box

- background-clip → define até onde a pintura se estende (border / padding / content). Tem também o valor text (usado para efeitos como texto com gradiente), que historicamente tem diferenças de suporte entre engines e às vezes exige prefixo -webkit-. (veja compatibilidade antes de usar em produção)

### **Outros conceitos...**

- Múltiplas camadas & ordem de empilhamento

- A propriedade background-image aceita mútiplas imagens separadas por vírgula.

- Ordem Importante: a primeira imagem é desenhada no topo e a última é a camada de fundo acima do background-color. Isso permite composições complexas (padrões, texturas, gradientes de overlay)

- background-position / background-size — a tecla / no shorthand

- Quando é preciso definir background-position e background-size simultâneamente, usa-se a notação abreviada, a sintaxe é: position / sizeEx: background: url(...) center / cover no-repeat;

- Isso evita ambiguidade na interpretação dos valores

- background-attachment — comportamento de rolagem

### ***Valores*** 

- scroll (padrão): a imagem está posicionada relativamente ao seu elemento e se comporta normalmente ao rolar a página.

- fixed: a imagem é fixada ao viewport; útil para efeitos parallax simples, mas com limitações (em dispositivos móveis pode não se comportar como esperado e pode afetar background-size).

    * ***Procure usar fixed com cuidado em layouts responsivos***

- local: o background “rola” junto com o conteúdo do elemento (útil quando o elemento tem overflow interno)

- linear-gradient

---

## 🎲 Propriedade Border 

Bordas não afetam o flow do layout por padrão (exceto em tabelas com border-collapse), mas adicionam ao box model 
(content + padding + border + marginA propriedade border define as bordas de um elemento HTML, controlando largura, estilo e cor).

```bash
Ela é aplicada a elementos de bloco ou inline-block (como div, p, img, button), criando separação visual, foco em interações (ex: hover) 
e estruturas como cards ou tabelas.
```

### ***Sintaxe Básica***

```css
selector {
    /* Modelo sintático shorthand */
    border: largura estilo cor; /* Ex: border: 1px solid black; */
}
```

```html
<!-- Exemplo Simples -->
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <style>
    .box {
      border: 2px dashed red; /* Largura 2px, estilo dashed, cor vermelha */
      width: 200px;
      height: 100px;
      padding: 10px;
    }
  </style>
</head>
<body>
  <div class="box">Caixa com borda!</div>
</body>
</html>
```

---

### **Valor inicial e padrão**

-Inicial: border: medium none currentColor; (sem borda visível).

-Não é herdada por padrão, mas pode ser forçada com inherit.

-Aplicável a todos os elementos exceto tabelas internas (use border-collapse para tabelas).

-Box model impacto: Bordas adicionam ao tamanho total – use box-sizing: border-box; para incluir borda/padding no width/height calculado.

---

### ***Sintaxe Detalhada: Shortand e Propriedades Inviduais***

A propriedade border pode ser decomposto para controle fino por lado ```(top, right, bottom, left)``` ou aspecto.

- Shorthand completo: border: width style color; (ordem fixa; omita partes para defaults).

- Propriedades individuais:

    * border-width: Define espessura. Valores: thin (1px), medium (3px), thick (5px), ou numéricos (ex: 2px, 0.5em). Pode ser por lado: border-top-width, etc.

    * border-style: Estilo visual. Valores: none (default), hidden, dotted, dashed, solid, double, groove, ridge, inset, outset. Dica: hidden é como none, mas afeta colisões em tabelas.

    * border-color: Cor da borda. Suporta todos formatos de cor (hex, rgb, hsl, transparent). Default: currentColor (herda da cor do texto).
    Ex: border-color: rgba(0, 0, 0, 0.5); para semi-transparente.

---

### **Por Lado**

- Shorthands: border-top: 1px solid blue;, border-right, etc.

- Ordem em shorthand múltiplo: border-width: 1px 2px 3px 4px; (top, right, bottom, left – sentido horário).

- Exemplo avançado:

```css
.fancy-box {
	/* Top e bottom 5px, sides 0 */
  border-width: 5px 0 5px 0;
  
  /* Top/bottom solid, left/right dashed (repetição implícita) */ 
  border-style: solid dashed;
  
  /* Cada lado uma cor */ 
  border-color: red green blue yellow; 
}
```

```bash
Resetando: border: none; ou border: 0;. Útil para remover bordas padrão em inputs/buttons.
```

---

### **Valores Avançados e Propriedades Relacionada**

- border-radius: Arredonda cantos. Valores: numéricos (ex: 10px), % (relativo ao tamanho), ou por canto: border-top-left-radius, etc.

    * Shorthand: border-radius: 10px 20px 30px 40px; (top-left, top-right, bottom-right, bottom-left).
    * Elliptical: border-radius: 50px / 25px; (horizontal/vertical).
    * Dica expert: Para círculos: border-radius: 50%; em elementos quadrados.

- border-image: Usa imagens para bordas customizadas.

    * Sintaxe: border-image: source slice width outset repeat;
    * Ex: border-image: url('border.png') 30 round; (imagem sliceada em 30px, repetição round).
    * Vantagem: Para patterns como gradients ou SVGs. Armadilha: Complexo para responsividade – teste em diferentes tamanhos.

- border-collapse: Para tabelas. Valores: collapse (mescla bordas adjacentes), separate (default, espaçadas).

    * Relacionado: border-spacing controla gaps em separate.

- border-block/inline (Logical Properties): Para writing modes (ex: vertical text).border-block-start` = top em horizontal, start em vertical. 

    * Útil para internacionalização.
    * Compatibilidade: Bordas básicas em todos browsers; border-image e logical props em modernos
    * Fallbacks: Use feature queries @supports (border-image: url()) { ... }.

### **Comportamentos**

- Cascata: Segue regras CSS – seletores específicos vencem. !important para overrides, mas evite para manutenção.
- Herança: Não herdada, mas filhos podem herdar estilos se aplicados ao pai. Ex: Bordas em listas aninhadas.

- Interações:
    * Com overflow: Bordas clipam conteúdo se overflow: hidden;.
    * Com position: Bordas absolutas podem sobrepor.
    * Em flex/grid: Bordas afetam alignment – use box-sizing para consistência.
    * Armadilha comum: Bordas duplicadas em tabelas – use border-collapse: collapse;.

---

## 📖 Propriedada Margin

A propriedade ```margin``` define o espaçamento externo ao redor de um elemento, separando-o de vizinhos.

Ela faz parte do box model CSS (content + padding + border + margin), onde margins não adicionam cor ou estilo – são transparentes 
e não afetam o tamanho interno do elemento.

Margins influenciam o flow do documento, especialmente em blocos verticais, e são vitais para grids, flexbox e posicionamentos.

### Sintaxe Básica e Exemplo Simples

```css
selector {
  margin: valor; /* Aplica igual a todos os lados */
  
  /* Propriedade em Modelo Shorthand */
  margin: <valo_top> <valor_right> <valor_bottom> <valor_left>
}
```

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <style>
    .box {
      margin: 20px; /* 20px em todos os lados */
      width: 200px;
      height: 100px;
      background: lightblue;
    }
  </style>
</head>
<body>
  <div class="box">Caixa com margem!</div>
  <div class="box">Outra caixa – observe o espaçamento.</div>
</body>
</html>
```

### ***Valor Inicial e Padrão***

- Inicial: margin: 0; (sem espaçamento).
- Não é herdada por padrão, mas pode ser forçada com inherit.
- Aplicável a todos os elementos exceto alguns internos de tabelas (ex: td herda de table).
- Impacto no box model: Com box-sizing: content-box; (default), margins são externas; com border-box;, não afetam cálculos de width/height, mas ainda espaçam elementos

### ***Sintaxe Detalhada → Shorthand e Valores***

- Shorthand:
    * 1 valor: Aplica a todos (ex: margin: 10px;).
    * 2 valores: Vertical (top/bottom) e horizontal (left/right) (ex: margin: 10px 20px;).
    * 3 valores: Top, horizontal (left/right), bottom (ex: margin: 10px 20px 30px;).
    * 4 valores: Top, right, bottom, left (sentido horário) (ex: margin: 10px 20px 30px 40px;).

- Propriedades individuais: margin-top, margin-right, etc., para controle fino.
- Exemplo: ```margin-left: 50px;``` para indentação.

### ***Valores Suportados***

- **Numéricos**: Positivos (espaçamento externo), negativos (sobreposição/pulling) – ex: margin-top: -10px; para overlap.
- **Unidades**: Qualquer (px, em, rem, %, vw, etc.). Relativas para responsividade (ex: margin: 5%;).
- **auto**: Centraliza horizontalmente em blocos (ex: margin: 0 auto; para div centrada). Não funciona verticalmente sem height definido.
- **initial, inherit, unset**: Para reset ou herança.
- **Armadilha**: % é relativo ao width do pai (mesmo para margins verticais), levando a layouts imprevisíveis em containers fluidos.

```bash
Cálculos: Use calc() para dinâmicos: margin: calc(10% - 20px);. 
Integre com variáveis: :root { --margin-base: 1rem; } | margin: var(--margin-base);
```


### Comportamentos Avançados - Colapso de Margins

- Quando colapsa:

    * Entre blocos adjacentes (ex: dois seguidos – margin-bottom do primeiro e top do segundo viram max dos dois).
    * Pai e filho: Se pai sem border/padding e filho com margin-top/bottom, propaga para fora (colapso through).
    * Elementos vazios: Margins de blocos vazios colapsam.

- Evitando colapso:

    * Adicione border/padding ao pai (mesmo border: 1px solid transparent;).
    * Use overflow: hidden; ou display: flow-root; (moderno para BFC – Block Formatting Context).
    * Flex/grid containers não colapsam margins de filhos.

- Exemplo de colapso:

```css
.parent {
  margin-top: 20px; /* Não colapsa com filho */
}
.child {
  margin-top: 30px; /* Colapsa through, resultando em 30px total */
}
```

- **Solução**

```css
.parent{
    overflow: hidden;
}
```

### **Além disso, a propriedade Margin dispõe dos seguintes comportamentos**

- Cascata: Segue specificity – seletores mais específicos vencem. Use !important raramente.
- Herança: Não herdada, mas afeta filhos indiretamente via flow.

- Interações:
    * **Com flexbox**: Margins afetam alignment (ex: margin: auto; centraliza itens).
    * **Com grid**: Margins em itens não afetam gaps (use gap em vez de margins para espaçamentos internos).
    * **Posicionamento**: Em position: absolute;, margins relativos ao container posicionado.
    * **Floats**: Margins não colapsam com floats – use clearfix.
    * **Armadilha Comum**: Colapso causando "espaços fantasmas" – debugue com DevTools (Computed tab mostra valores colapsados

--- 

## 📚 Propriedade Padding

A propriedade **padding** define o espaçamento interno entre o conteúdo de um elemento e sua borda, adicionando "respiro" ao conteúdo sem afetar o exterior.

Diferente de **margin** (espaçamento externo), **padding** é interno e herda a cor de fundo do elemento (background-color se aplica ao padding).

Faz parte do box model (content + padding + border + margin), influenciando tamanhos calculados e interações como toques em mobiles.


### **Sintaxe Básica da Propriedade**

```css
selector {
  padding: valor; /* Aplica igual a todos os lados */
  
  /* Propriedade em Modelo Shorthand */
  padding: <valo_top> <valor_right> <valor_bottom> <valor_left>
}
```

### **Exemplo Simples**

```css
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <style>
    .box {
      padding: 20px; /* 20px interno em todos os lados */
      width: 200px; /* Conteúdo + padding + border = tamanho total */
      background: lightblue;
      border: 1px solid black;
    }
  </style>
</head>
<body>
  <div class="box">Conteúdo com padding!</div>
</body>
</html>
```

--- 

## Propriedades Width e Height

As propriedades `width` e `height` definem as **dimensões de um elemento** dentro do CSS Box Model.

Elas controlam o tamanho da **área de conteúdo (content box)**, mas o tamanho total renderizado pode incluir `padding` e `border`, dependendo do valor da propriedade `box-sizing`.

Essas propriedades são fundamentais para:

- 📦 Estruturação de layouts (cards, containers, grids)
- 🖼️ Dimensionamento de imagens
- 📜 Controle de scroll
- 🖱️ Interações visuais (hover, animações)
- 📱 Responsividade

---

### 🧱 Relação com o Box Model

O tamanho final de um elemento pode incluir:

```bash
content + padding + border + margin
```

Por padrão (`box-sizing: content-box`), `width` e `height` afetam apenas o **content**.

Com `box-sizing: border-box`, o valor definido passa a incluir:

### ✅ Boa prática moderna

  ```css
  box-sizing: border-box;
  ```
### 📌 Comportamento por Tipo de Display

- Elementos block

  * width → eixo horizontal
  * height → eixo vertical
  * width: auto ocupa 100% do container pai

- Elementos inline

  * Ignoram width e height
  * Para permitir dimensões

- Elementos inline-block

  * Permitem definir largura e altura
  * Mantêm comportamento inline no fluxo

## 🧾 Sintaxe Básica

```css
selector {
  width: valor;
  height: valor;
}
```

## Exemplo Prático

```css
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <style>
    .box {
      width: 200px; /* Largura do content box */
      height: 100px; /* Altura do content box */
      background: lightblue;
      border: 1px solid black;
      padding: 10px; /* Soma ao total se content-box */
    }
  </style>
</head>
<body>
  <div class="box">Caixa dimensionada!</div>
</body>
</html>
```

### ⚙️ Valor Inicial e Comportamento Padrão

| Propriedade | Valor Inicial | Observação               |
| ----------- | ------------- | ------------------------ |
| `width`     | `auto`        | Calculado pelo navegador |
| `height`    | `auto`        | Baseado no conteúdo      |

***🔎 Observações***

- Não são propriedades herdadas.
- Influenciam filhos indiretamente via fluxo do documento.
- auto depende do contexto do elemento


### 📐 Tipos de Valores

- 1. Automático

```css
width: auto;
height: auto;
```

Em blocos, ```width: auto``` normalmente **ocupa 100%** do container pai 

- 2. Valores Absolutos e Relativos

  * Unidades Fixas
    - px
    - cm
    - mm
    - in
    - pt
  
  * Valores Relativos
    - ``%`` -> Relativo ao Pai
    - ``vw`` -> Viewport Width
    - ``vh`` -> Viewport Height
    - ``em / rem`` -> Relativo à fonte
  
    ```css
    width: 50%;
    height: 100vh;
    ```

- 3. Keywords Modernas

```css
width: fit-content;
width: min-content;
width: max-content;
```
| Valor         | Comportamento               |
| ------------- | --------------------------- |
| `fit-content` | Ajusta ao mínimo necessário |
| `min-content` | Menor largura possível      |
| `max-content` | Maior largura sem quebra    |


### Propriedades Relativas

- ``min-width / max-width``
- ``min-height / max-height``

Definem os limites para evitar o **Overflow**.
**São essenciais para Layouts Responsivos!!!**

```css
width: 50%;
max-width: 500px;
```

- ``aspect-ratio``

Garante a proporção automática:

```css
aspect-ratio: 16 / 9;
```

No caso de apenas ``width`` estiver definida, o navegador calcula ``height``.
Ideal para:

- Vídeos
- Cards
- Imagens
- Containers Proporcionais

- ``calc()``

Permite cálculos dinâmicos: 

```css
width: calc(100% - 40px);
```

- ``Variáveis CSS``

```css
:root {
  --width-base: 300px;
}

.box {
  width: var(--width-base);
}
```

- ``clamp() - Responsividade Moderna``

Permite cálculos dinâmicos: 

```css
width: clamp(200px, 50vw, 800px);
```

Sua estrutura segue o seguinte padrão

```scsss
clamp(valor-mínimo, valor-preferido, valor-máximo)
```

### 🧠 Sizing Intrínseco vs Extrínseco

- **Intrínseco**

Baseado no conteúdo:

```css
width: auto;
```

- **Extrínseco**

Baseado no ambiente externo:

```css
width: 100vw;
```

### 📦 Comportamentos em Diferentes Contextos

- Blocos 
  
  * ``width: auto`` **-->** 100% do Container
  * ``height: auto`` **-->** Altura do Container

- Flex 
  
  * ``width: auto`` **-->** Respeita ``flex-grow`` e ``flex-shrink``
  * Pode ser influenciada por ``flex-basis``

- Grid

  * Dimensões podem ser controladas por ``grid-template-columns`` e ``grid-template-rows``

### ⚠️ Armadilhas Comuns

- ``height: 100%`` sem pai definido

  * Se o pai de height não estiver adequadamente definida, pode não funcionar como o esperado
  * **Solução**
    ```css
    html, body {
      height: 100%;
    }
    ```

- Overflow

  * Se o conteúdo exceder as dimensões:
    - ``overflow: scroll;``
    - ``overflow: hidden;``
    - ``overflow: auto;``

- Aspect-ratio em containers flexíveis

  * Pode gerar conflitos de cálculo.
  * Use ``min-width`` e ``max-width`` para controle.

- Viewport Units

  * Alguns navegadores tratam zoom de forma diferente com ``vw`` e ``vh``.
  * Sempre teste em múltiplos dispositivos.

### 🔁 Interações com Outras Propriedades

- ``margin`` e ``padding`` influenciam espaço total.
- ``position: absolute`` usa como referência o ancestor posicionado.
- ``float`` altera fluxo.
- **Especificidade** e **cascata** determinam sobrescritas.
- Evite ``!important`` sempre que possível.

### 📚 Resumo Técnico

| Propriedade    | Função             | Observação                      |
| -------------- | ------------------ | ------------------------------- |
| `width`        | Define largura     | Padrão: auto                    |
| `height`       | Define altura      | Padrão: auto                    |
| `min-width`    | Largura mínima     | Evita colapso                   |
| `max-width`    | Largura máxima     | Essencial para responsividade   |
| `aspect-ratio` | Mantém proporção   | Automatiza cálculo              |
| `clamp()`      | Range responsivo   | Substitui media queries simples |
| `calc()`       | Cálculos dinâmicos | Combina unidades                |

---

## 📐 Propriedade Position

A propriedade `position` define como um elemento é posicionado no
layout, influenciando o **flow natural** do documento.

Ela determina se o elemento:

-   Segue o fluxo normal (`static`)
-   É deslocado relativo a si mesmo (`relative`)
-   É removido do fluxo (`absolute` / `fixed`)
-   "Cola" em determinados thresholds (`sticky`)

Pode ser combinada com **offsets** (`top`, `right`, `bottom`, `left`) e
`z-index` para controle tridimensional (empilhamento).

------------------------------------------------------------------------

## 🧾 Sintaxe Básica

``` css
selector {
  position: valor;
  top: valor;
  left: valor;
  z-index: numero;
}
```

------------------------------------------------------------------------

## 💻 Exemplo Prático

``` html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <style>
    .container {
      position: relative;
      height: 200px;
      background: lightgray;
    }

    .box {
      position: absolute;
      top: 20px;
      left: 20px;
      width: 100px;
      height: 50px;
      background: lightblue;
    }
  </style>
</head>
<body>
  <div class="container">
    Container
    <div class="box">Box absoluta!</div>
  </div>
</body>
</html>
```

------------------------------------------------------------------------

## ⚙️ Valor Inicial

-   Valor padrão: `static`
-   Não é herdada
-   Aplicável a todos os elementos
-   Em elementos inline pode alterar comportamento visual

------------------------------------------------------------------------

# 📌 Valores da Propriedade

## 🔹 `static`

-   Valor padrão
-   Segue o fluxo normal
-   Ignora offsets

------------------------------------------------------------------------

## 🔹 `relative`

-   Mantém espaço no fluxo
-   Permite deslocamento visual com offsets

``` css
position: relative;
top: 10px;
```

------------------------------------------------------------------------

## 🔹 `absolute`

-   Remove do fluxo
-   Posicionado relativo ao **nearest positioned ancestor**
-   Se não houver, usa o viewport

``` css
position: absolute;
bottom: 0;
right: 0;
```

------------------------------------------------------------------------

## 🔹 `fixed`

-   Remove do fluxo
-   Relativo ao viewport
-   Não se move com scroll

Ideal para: - Headers fixos - Botões flutuantes

------------------------------------------------------------------------

## 🔹 `sticky`

-   Híbrido entre `relative` e `fixed`
-   Funciona com offsets
-   "Gruda" quando atinge determinado ponto

``` css
position: sticky;
top: 0;
```

Requer: - Offset definido - Container com altura suficiente

------------------------------------------------------------------------

# 📍 Offsets

  Propriedade   Função
  ------------- -----------------------
  `top`         Distância do topo
  `right`       Distância da direita
  `bottom`      Distância da base
  `left`        Distância da esquerda

-   Com `static`: ignorados
-   Com `relative`: deslocam da posição original
-   Com `absolute`, `fixed`, `sticky`: posicionam em relação ao
    containing block

Unidades aceitas: - `px` - `%` - `em` - `rem` - `vw` - `vh`

------------------------------------------------------------------------

# 🧱 Containing Block

É o elemento de referência para `absolute`, `fixed` e `sticky`.

Regra prática:

> Sempre defina `position: relative;` no elemento pai para controlar
> filhos `absolute`.

------------------------------------------------------------------------

# 🧊 Stacking Context e `z-index`

Controla a ordem de empilhamento.

``` css
z-index: 10;
```

-   `auto` → padrão
-   Valores positivos → frente
-   Valores negativos → atrás

Um novo stacking context é criado quando: - `position` diferente de
static + `z-index` - `opacity < 1` - `transform` - `filter` -
`will-change`

⚠️ `z-index` só funciona em elementos posicionados.

------------------------------------------------------------------------

# 🔬 Comportamentos Avançados

## 📌 Em Flex e Grid

Elementos posicionados saem do fluxo do layout flex/grid.

## 📌 Overflow

Se o container tiver `overflow: hidden;`, pode cortar elementos
posicionados.

## 📌 Scroll

-   `fixed` ignora scroll
-   `sticky` reage ao scroll

## 📌 Animações

``` css
transition: top 0.3s;
```

⚠️ Pode causar reflow.

------------------------------------------------------------------------

# ⚠️ Armadilhas Comuns

-   Elemento sumiu → Verifique o containing block.
-   `absolute` sem pai posicionado → Usa viewport.
-   Guerras de `z-index` → Use stacking contexts isolados.
-   `sticky` não funciona → Falta `top` ou container adequado.

------------------------------------------------------------------------

# 📚 Resumo Técnico
                                                                    
  Valor      Sai do Flow?   Referência        Uso comum
  ---------- -------------- ----------------- ----------------------
  static     Não            Flow normal       Reset
  relative   Não            Própria posição   Ajustes finos
  absolute   Sim            Pai posicionado   Layouts complexos
  fixed      Sim            Viewport          Elementos fixos
  sticky     Parcial        Container         Headers inteligentes

------------------------------------------------------------------------

# 🚀 Conclusão

A propriedade `position` é fundamental para controle estrutural e visual
no CSS.

Seu domínio permite:

-   Criar layouts complexos
-   Controlar empilhamento
-   Desenvolver componentes fixos e dinâmicos
-   Trabalhar com sobreposição de elementos

Compreender `containing block`, `stacking context` e offsets é essencial
para dominar posicionamento avançado.

------------------------------------------------------------------------

# 🎨 Propriedades `font` e `text` no CSS

As propriedades relacionadas a **fontes e texto** controlam como o
conteúdo textual é renderizado, organizado e apresentado na interface.

Elas são definidas principalmente pelos módulos:

-   CSS Fonts Module Level 4
-   CSS Text Module Level 3

Esses módulos ampliam os recursos tradicionais com suporte a: - Fontes
variáveis - Renderização otimizada - Ajustes tipográficos avançados -
Melhor controle de internacionalização

------------------------------------------------------------------------

# 🔤 Propriedades `font`

As propriedades de `font` definem **como a fonte é escolhida e
renderizada**, incluindo:

-   Família
-   Tamanho
-   Peso
-   Estilo
-   Variante
-   Stretch
-   Ajustes ópticos
-   Eixos personalizados (fontes variáveis)

------------------------------------------------------------------------

## 🧾 Shorthand `font`

``` css
p {
  font: italic small-caps bold 16px/1.5 "Arial", sans-serif;
}
```

### 📌 Regras importantes

A shorthand `font`:

-   Exige obrigatoriamente `font-size` e `font-family`
-   Pode incluir opcionalmente:
    -   `font-style`
    -   `font-variant`
    -   `font-weight`
    -   `font-stretch`
    -   `line-height` (separado por `/`)
-   Reseta propriedades não declaradas para seus valores iniciais

Também aceita valores de sistema:

``` css
font: menu;
font: caption;
```

------------------------------------------------------------------------

## 🔹 `font-family`

Define a pilha de fontes (font stack).

``` css
font-family: "Trebuchet MS", Verdana, sans-serif;
```

### 🎯 Boas práticas

-   Sempre incluir uma família genérica no final
-   Usar aspas em nomes com espaço
-   Priorizar fontes web-safe ou system-ui

### 📚 Famílias Genéricas

  Família      Uso
  ------------ -------------------------
  serif        Textos longos e formais
  sans-serif   Interfaces modernas
  monospace    Código
  cursive      Decorativo informal
  fantasy      Títulos chamativos
  system-ui    Fonte nativa do SO

------------------------------------------------------------------------

## 🔹 `font-size`

Define o tamanho da fonte.

``` css
font-size: 1.2rem;
```

### 📌 Unidades recomendadas

-   `rem` → mais acessível (baseado no root)
-   `em` → relativo ao elemento pai
-   `px` → fixo
-   `%` → relativo ao pai

Evite valores absolutos em layouts responsivos.

------------------------------------------------------------------------

## 🔹 `font-style`

``` css
font-style: italic;
font-style: oblique 14deg;
```

Valores: - normal - italic - oblique

Em fontes variáveis usa eixos como: - `ital` - `slnt`

------------------------------------------------------------------------

## 🔹 `font-weight`

``` css
font-weight: 400;
font-weight: bold;
```

Valores: - 100 a 900 - normal (400) - bold (700) - bolder / lighter

Fontes variáveis interpolam no eixo `'wght'`.

------------------------------------------------------------------------

## 🔹 `font-stretch`

Controla largura da fonte.

``` css
font-stretch: condensed;
font-stretch: 120%;
```

Relacionado ao eixo `'wdth'`.

------------------------------------------------------------------------

## 🔹 `font-variant`

Controla variações tipográficas.

``` css
font-variant: small-caps;
```

Expansões incluem:

-   `font-variant-caps`
-   `font-variant-numeric`
-   `font-variant-ligatures`

------------------------------------------------------------------------

## 🔹 `font-optical-sizing`

``` css
font-optical-sizing: auto;
```

Ativa ajuste automático baseado no eixo `'opsz'`.

------------------------------------------------------------------------

## 🔹 `font-variation-settings`

Controle de baixo nível para fontes variáveis.

``` css
font-variation-settings: "wght" 600;
```

------------------------------------------------------------------------

## ✍️ Propriedades `text`

Controlam o **layout, espaçamento e comportamento textual**.

O processamento textual ocorre em fases:

1.  Colapso de espaços
2.  Posicionamento e quebra

Considera idioma (`lang`) e regras Unicode.

------------------------------------------------------------------------

## 🔹 `text-align`

``` css
text-align: justify;
```

Valores: - start - end - left - right - center - justify

Relacionado:

``` css
text-justify: inter-word;
```

------------------------------------------------------------------------

## 🔹 `line-height`

``` css
line-height: 1.6;
```

Ideal para leitura: **1.5 -- 2**.

Evite usar valores em px fixos.

------------------------------------------------------------------------

## 🔹 `letter-spacing` e `word-spacing`

``` css
letter-spacing: 0.05em;
word-spacing: 0.2em;
```

Controlam espaçamento entre letras e palavras.

------------------------------------------------------------------------

## 🔹 `text-transform`

``` css
text-transform: uppercase;
```

Valores: - none - capitalize - uppercase - lowercase - full-width

Sensível ao idioma (ex: turco).

------------------------------------------------------------------------

## 🔹 `white-space`

``` css
white-space: pre-wrap;
```

Valores: - normal - nowrap - pre - pre-line - pre-wrap - break-spaces

------------------------------------------------------------------------

## 🔹 `word-break`

``` css
word-break: break-all;
```

Valores: - normal - break-all - keep-all

------------------------------------------------------------------------

## 🔹 `overflow-wrap`

``` css
overflow-wrap: break-word;
```

Evita overflow de palavras longas.

------------------------------------------------------------------------

## 🔹 `hyphens`

``` css
hyphens: auto;
```

Requer suporte linguístico.

------------------------------------------------------------------------

## 🔹 `text-indent`

``` css
text-indent: 2rem;
```

Indentação da primeira linha.

------------------------------------------------------------------------

## 🔹 `text-decoration`

``` css
text-decoration: underline;
```

Pode combinar com:

``` css
text-decoration: underline wavy red;
```

------------------------------------------------------------------------

## 🔹 `text-shadow`

``` css
text-shadow: 1px 1px 2px black;
```

Aceita múltiplas sombras separadas por vírgula.

------------------------------------------------------------------------

# 📊 Tabela Resumo

  Propriedade       Herda?   Aplicação Principal
  ----------------- -------- --------------------------
  font-family       Sim      Escolha da fonte
  font-size         Sim      Tamanho
  font-weight       Sim      Peso
  font-style        Sim      Estilo
  text-align        Sim      Alinhamento
  line-height       Sim      Espaçamento entre linhas
  letter-spacing    Sim      Espaço entre letras
  text-transform    Sim      Transformação
  text-decoration   Não      Decoração
  text-shadow       Sim      Sombra

------------------------------------------------------------------------

# 🚀 Conclusão

O domínio das propriedades `font` e `text` permite:

-   Melhorar legibilidade
-   Construir hierarquia visual
-   Criar sistemas tipográficos escaláveis
-   Trabalhar com fontes variáveis modernas
-   Desenvolver interfaces acessíveis e responsivas

Tipografia não é apenas estética --- é arquitetura visual da informação.

------------------------------------------------------------------------

# ⚙️ Propriedade `float`

A propriedade `float` desloca um elemento para a esquerda ou direita do
seu contêiner, permitindo que o conteúdo inline (como texto) flua ao seu
redor.

Historicamente utilizada para layouts em colunas, hoje é considerada
**legado para layout estrutural**, sendo substituída por **Flexbox e
Grid**. Contudo, ainda é extremamente relevante para:

-   Envolver imagens com texto
-   Componentes editoriais
-   Ajustes pontuais de fluxo

------------------------------------------------------------------------

## 🧾 Sintaxe

``` css
div {
  float: left;
}
```

------------------------------------------------------------------------

## 📌 Valores

-   `none` (padrão)
-   `left`
-   `right`
-   `inline-start`
-   `inline-end`
-   `inherit | initial | unset | revert | revert-layer`

------------------------------------------------------------------------

## 🔬 Comportamento no Fluxo

Quando um elemento recebe `float`:

1.  É removido do fluxo normal.
2.  É deslocado horizontalmente até encostar na borda do contêiner ou
    outro float.
3.  O conteúdo inline subsequente passa a contorná-lo.

------------------------------------------------------------------------

## ⚠️ Colapso do Contêiner

Elementos pais não expandem altura para conter floats.

### Solução moderna

``` css
.container {
  display: flow-root;
}
```

------------------------------------------------------------------------

# 🎮 Propriedade `opacity`

Controla a transparência de um elemento inteiro.

``` css
div {
  opacity: 0.6;
}
```

------------------------------------------------------------------------

## 📌 Valores

-   `0` → totalmente transparente
-   `1` → totalmente opaco
-   Intervalo permitido: `0` a `1`
-   Valores são clampados

------------------------------------------------------------------------

## 🔬 Comportamento Técnico

-   Multiplica o canal alpha de todos os pixels
-   Afeta filhos
-   Cria novo stacking context
-   Não altera layout

------------------------------------------------------------------------

# 🌑 Propriedade `text-shadow`

Adiciona sombra ao texto.

``` css
h1 {
  text-shadow: 2px 2px 4px black;
}
```

------------------------------------------------------------------------

## 📌 Sintaxe

    offset-x offset-y blur color

Exemplo múltiplo:

``` css
text-shadow: 
  1px 1px 2px black,
  0 0 10px blue;
```

------------------------------------------------------------------------

# 🌫️ Propriedade `box-shadow`

Adiciona sombra à caixa do elemento.

``` css
div {
  box-shadow: 0 4px 10px rgba(0,0,0,0.2);
}
```

------------------------------------------------------------------------

## 📌 Sintaxe

    offset-x offset-y blur spread color inset?

------------------------------------------------------------------------

# 📊 Resumo Comparativo

  Propriedade   Afeta Layout?   Herdada?   Cria Stacking Context?
  ------------- --------------- ---------- ------------------------
  float         Sim (fluxo)     Não        Parcial
  opacity       Não             Não        Sim (\<1)
  text-shadow   Não             Sim        Não
  box-shadow    Não             Não        Não

------------------------------------------------------------------------

# 🎯 Conclusão

Essas propriedades são fundamentais para fluxo, composição visual e
profundidade em interfaces modernas.

------------------------------------------------------------------------

# 🕹 Propriedades `text-shadow` e `box-shadow`

As propriedades `text-shadow` e `box-shadow`, introduzidas no **CSS3**,
permitem adicionar sombras a textos e caixas, criando profundidade
visual, hierarquia e melhor legibilidade --- tudo sem o uso de imagens.

Ambas são amplamente suportadas desde 2015 e fazem parte do processo de
composição gráfica do navegador (render tree + paint phase), não
afetando o layout (flow).

------------------------------------------------------------------------

# 🌑 `text-shadow`

Aplica sombras ao **texto e suas decorações** (como underline e
overline).

## 📌 Sintaxe Geral

``` css
text-shadow: offset-x offset-y blur-radius color;
```

### Exemplo simples

``` css
h1 {
  text-shadow: 2px 2px 4px rgba(0,0,0,0.4);
}
```

------------------------------------------------------------------------

## 📚 Valores Permitidos

-   `none` (valor inicial)
-   `<offset-x>` (obrigatório)
-   `<offset-y>` (obrigatório)
-   `<blur-radius>` (opcional, ≥ 0)
-   `<color>` (opcional, padrão: `currentColor`)
-   Valores globais: `inherit`, `initial`, `unset`, `revert`,
    `revert-layer`

### Múltiplas sombras

``` css
text-shadow:
  1px 1px 2px black,
  0 0 1em blue;
```

📌 **Ordem importa:** a primeira sombra é renderizada no topo.

------------------------------------------------------------------------

## 🔬 Comportamento Técnico

-   Herdada.
-   Animável como lista.
-   Aplicada front-to-back.
-   Não altera layout.
-   Não cria stacking context.
-   Blur usa aproximação Gaussiana (≈ blur / 2 como desvio padrão).

Sombras seguem transformações (`transform`), mas não fazem clipping ao
formato exato do glifo --- podendo "vazar" caso o texto tenha
transparência.

------------------------------------------------------------------------

## 🎯 Aplicações Práticas

-   Melhorar contraste em imagens
-   Criar efeito glow
-   Simular profundidade 3D leve
-   Criar contorno (stacking múltiplo)

Exemplo de contorno:

``` css
text-shadow:
  -1px -1px 0 black,
   1px -1px 0 black,
  -1px  1px 0 black,
   1px  1px 0 black;
```

------------------------------------------------------------------------

# 🌫️ `box-shadow`

Aplica sombra ao **box model do elemento**, respeitando `border-radius`.

## 📌 Sintaxe Geral

``` css
box-shadow: offset-x offset-y blur-radius spread-radius color inset;
```

### Exemplo básico

``` css
.card {
  box-shadow: 0 4px 12px rgba(0,0,0,0.15);
}
```

------------------------------------------------------------------------

## 📚 Valores Permitidos

-   `none` (inicial)
-   `<offset-x>` (obrigatório)
-   `<offset-y>` (obrigatório)
-   `<blur-radius>` (opcional)
-   `<spread-radius>` (opcional)
-   `<color>` (opcional)
-   `inset` (opcional)
-   Valores globais

------------------------------------------------------------------------

## 🔬 Comportamento Técnico

-   Não herdada.
-   Animável.
-   Não altera layout.
-   Não modifica box model.
-   Respeita `border-radius`.
-   Múltiplas sombras empilhadas (front-to-back).

### Spread Radius

-   Positivo → expande a sombra
-   Negativo → contrai
-   0 → tamanho original do box

------------------------------------------------------------------------

## 🧠 Diferença entre Externa e Inset

``` css
box-shadow: inset 0 2px 5px rgba(0,0,0,0.3);
```

-   Externa → segue `border-box`
-   Inset → aplicada dentro da `padding-box`

------------------------------------------------------------------------

## 🎨 Aplicações Modernas

-   Cards com elevação (Material Design)
-   Simular profundidade Z
-   Soft UI / Neumorphism
-   Foco acessível customizado
-   Destaque de elementos interativos

------------------------------------------------------------------------

# ⚙️ Performance e Renderização

Sombras são aplicadas na fase de pintura (paint).

⚠️ Valores altos de blur e múltiplas camadas podem impactar performance,
especialmente em animações.

### Boas práticas

-   Evitar blur excessivo (\>40px) em listas grandes
-   Preferir transições suaves
-   Usar GPU-friendly propriedades junto com `opacity` e `transform`

------------------------------------------------------------------------

# 🧩 Interações Importantes

  Propriedade   Afeta Layout?   Herdada?   Cria Stacking Context?
  ------------- --------------- ---------- ------------------------
  text-shadow   Não             Sim        Não
  box-shadow    Não             Não        Não

------------------------------------------------------------------------

# 🚀 Alternativas Modernas

## `filter: drop-shadow()`

``` css
filter: drop-shadow(0 4px 6px black);
```

-   Ideal para SVG
-   Baseada na forma real do conteúdo
-   Funciona melhor com transparência

## `backdrop-filter`

Para blur no fundo (efeito glassmorphism).

------------------------------------------------------------------------

# ⚠️ Problemas Comuns

### text-shadow

-   Vazamento em texto transparente
-   Perda de contraste (verificar WCAG)

### box-shadow

-   Não funciona em `border-collapse: collapse`
-   Spread negativo pode "cortar" visualmente
-   Performance em animações intensas

------------------------------------------------------------------------

# 🎯 Conclusão Técnica

`text-shadow` e `box-shadow` são fundamentais para:

-   Hierarquia visual
-   Profundidade sem imagens
-   Melhor contraste
-   Interfaces modernas

Compreender sua renderização, ordem de composição e impacto em
performance é essencial para criar interfaces escaláveis, acessíveis e
profissionais.

------------------------------------------------------------------------

# 🎭 Media Queries no CSS

Media Queries são regras condicionais do CSS que permitem aplicar
estilos com base em características do dispositivo ou do ambiente do
usuário, como:

-   Largura e altura do viewport
-   Orientação (portrait / landscape)
-   Resolução
-   Preferências do usuário (modo escuro, redução de movimento,
    contraste)
-   Tipo de mídia (screen, print, speech)

Elas fazem parte da especificação **Media Queries Level 5** e são
fundamentais para a construção de layouts responsivos e acessíveis.

------------------------------------------------------------------------

# 🧠 Conceito Fundamental

Media Queries funcionam como **"if statements" do CSS**.

O navegador:

1.  Avalia a condição.
2.  Se for verdadeira → aplica os estilos.
3.  Se for falsa → ignora o bloco.

Elas são reavaliadas dinamicamente em eventos como:

-   Resize da janela
-   Mudança de orientação
-   Alteração de preferências do sistema

------------------------------------------------------------------------

# 🧾 Sintaxe Geral

``` css
@media [not | only] <media-type> and (<media-feature>) {
  /* CSS condicional */
}
```

------------------------------------------------------------------------

# 📚 Componentes da Sintaxe

## 🔹 `not` / `only`

-   `not` → nega a condição.
-   `only` → previne que navegadores antigos interpretem incorretamente.

------------------------------------------------------------------------

## 🔹 `<media-type>`

-   `all` (padrão)
-   `screen`
-   `print`
-   `speech`

> A partir do Level 4, o foco principal passou a ser media features.

------------------------------------------------------------------------

## 🔹 `<media-feature>`

As mais utilizadas:

### 📐 Dimensão

-   `width`
-   `min-width`
-   `max-width`
-   `height`
-   `aspect-ratio`

### 📱 Orientação

``` css
@media (orientation: landscape)
```

### 🎨 Preferências do usuário

-   `prefers-color-scheme: dark | light`
-   `prefers-reduced-motion: reduce`
-   `prefers-contrast: more | less`

### 🖥 Resolução

-   `resolution: 2dppx`
-   `min-resolution: 300dpi`

------------------------------------------------------------------------

# 📊 Sintaxe Moderna (Level 4+)

Suporte a intervalos mais legíveis:

``` css
@media (768px <= width <= 1024px) {
}
```

Ou:

``` css
@media (width >= 768px) {
}
```

------------------------------------------------------------------------

# 🚀 Estratégia Recomendada: Mobile First

``` css
/* Estilo base (mobile) */

.container {
  padding: 1rem;
}

/* Tablet */
@media (min-width: 768px) {
  .container {
    padding: 2rem;
  }
}

/* Desktop */
@media (min-width: 1024px) {
  .container {
    padding: 3rem;
  }
}
```

📌 Comece pelo menor layout e expanda progressivamente.

------------------------------------------------------------------------

# ⚙️ Comportamento Técnico

-   Não herda (é uma at-rule).
-   Escopo interno segue cascade normal.
-   Pode ser usada em:
    -   Arquivos CSS
    -   `<style>`
    -   `<link media="...">`
-   Pode ser combinada com `@import`.

------------------------------------------------------------------------

# 🧩 Combinação de Condições

### AND

``` css
@media (min-width: 768px) and (orientation: landscape)
```

### OR

``` css
@media (max-width: 600px), (orientation: portrait)
```

------------------------------------------------------------------------

# 🎯 Media Queries e Acessibilidade

Sempre considere:

``` css
@media (prefers-reduced-motion: reduce) {
  * {
    animation: none !important;
    transition: none !important;
  }
}
```

``` css
@media (prefers-color-scheme: dark) {
  body {
    background: #111;
    color: #eee;
  }
}
```

Essas queries melhoram significativamente a experiência do usuário.

------------------------------------------------------------------------

# ⚡ Performance

-   Media queries são altamente otimizadas pelos navegadores.
-   Muitas queries complexas podem causar reflow durante resize.
-   Prefira breakpoints consistentes.
-   Use unidades relativas (`em`, `rem`) para escalabilidade.

------------------------------------------------------------------------

# ⚠️ Problemas Comuns

  -----------------------------------------------------------------------
  Problema                            Solução
  ----------------------------------- -----------------------------------
  Breakpoints inconsistentes          Use sistema de design com tokens

  Uso excessivo de px                 Prefira rem/em

  Ignorar preferências do usuário     Sempre inclua queries de
                                      acessibilidade

  CSS difícil de manter               Organize por mobile-first
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 🧪 Exemplo Prático -- Navbar Responsiva

## HTML

``` html
<nav class="navbar">
  <div class="logo">Meu Site</div>
  <ul class="menu">
    <li><a href="#">Home</a></li>
    <li><a href="#">Sobre</a></li>
    <li><a href="#">Contato</a></li>
  </ul>
</nav>
```

## CSS

``` css
/* Mobile First */

.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.menu {
  display: none;
  flex-direction: column;
}

/* Tablet */
@media (min-width: 768px) {
  .menu {
    display: flex;
    flex-direction: row;
  }
}

/* Desktop */
@media (min-width: 1024px) {
  .navbar {
    padding: 2rem;
  }
}
```

------------------------------------------------------------------------

# 🔮 Recursos Avançados (Level 5)

## Custom Media Queries

``` css
@custom-media --tablet (min-width: 768px);

@media (--tablet) {
}
```

## Nesting (experimental)

``` css
@media (min-width: 768px) {
  @media (orientation: landscape) {
  }
}
```

------------------------------------------------------------------------

# 🎯 Conclusão Técnica

Media Queries são a base do design responsivo moderno.

Elas permitem:

-   Adaptabilidade a múltiplos dispositivos
-   Acessibilidade baseada em preferências
-   Performance otimizada
-   Escalabilidade arquitetural

Dominar Media Queries significa compreender como o navegador interpreta
condições ambientais e aplica estilos de forma dinâmica e eficiente.

------------------------------------------------------------------------

# 🎞 `@keyframes` no CSS --- Guia Completo e Aprofundado

A regra **`@keyframes`** é uma *at-rule* do CSS que define os
quadros-chave de uma animação, permitindo criar sequências de estilos
que evoluem ao longo do tempo.

Ela faz parte do **CSS Animations Module Level 1** e é utilizada em
conjunto com as propriedades da família `animation`.

Diferente de `transition`, que trabalha entre **dois estados**,
`@keyframes` permite **múltiplos estados intermediários**, tornando
possível criar animações complexas como:

-   Rotações contínuas\
-   Pulsações\
-   Movimentos em trajetória\
-   Sequências de transformação\
-   Animações com múltiplos estágios

------------------------------------------------------------------------

# 🧠 Conceito Fundamental

`@keyframes` define **o que acontece** durante a animação.\
A propriedade `animation` define **como e quando acontece**.\
O navegador interpola automaticamente os valores entre os keyframes
definidos.

------------------------------------------------------------------------

# 📜 Sintaxe Básica

``` css
@keyframes nome-da-animacao {
  0%   { /* estado inicial */ }
  50%  { /* estado intermediário */ }
  100% { /* estado final */ }
}
```

Ou usando palavras-chave:

``` css
@keyframes fadeIn {
  from { opacity: 0; }
  to   { opacity: 1; }
}
```

------------------------------------------------------------------------

# 🧩 Componentes da Regra

## 🔹 Nome da Animação

-   Identificador único\
-   Sensível a maiúsculas/minúsculas\
-   Não pode ser `none`

``` css
@keyframes slideUp { ... }
```

------------------------------------------------------------------------

## 🔹 Seletores de Keyframe

Podem ser:

-   Percentuais (`0%` até `100%`)\
-   `from` (equivalente a `0%`)\
-   `to` (equivalente a `100%`)

É permitido:

``` css
0%, 100% { transform: translateY(0); }
```

------------------------------------------------------------------------

## 🔹 Propriedades Permitidas

Apenas **propriedades animáveis** funcionam dentro de keyframes:

✅ `opacity`\
✅ `transform`\
✅ `color`\
✅ `background-color`\
✅ `filter`\
❌ `display`\
❌ `float`\
❌ `position`

> `!important` é inválido dentro de `@keyframes`.

------------------------------------------------------------------------

# ⚙ Como a Animação é Aplicada

O `@keyframes` sozinho não executa nada.\
Ele precisa ser referenciado via `animation-name`.

``` css
.elemento {
  animation-name: fadeIn;
}
```

Ou usando shorthand:

``` css
.elemento {
  animation: fadeIn 1s ease-in-out;
}
```

------------------------------------------------------------------------

# 🎛 Propriedades da Família `animation`

  Propriedade                   Função
  ----------------------------- --------------------------
  `animation-name`              Nome da animação
  `animation-duration`          Duração do ciclo
  `animation-timing-function`   Curva de aceleração
  `animation-delay`             Atraso inicial
  `animation-iteration-count`   Quantidade de repetições
  `animation-direction`         Direção da animação
  `animation-fill-mode`         Estado antes/depois
  `animation-play-state`        Rodando ou pausado
  `animation`                   Shorthand

------------------------------------------------------------------------

# 🎯 Exemplo Completo

``` css
.card {
  animation: slideUp 0.6s ease-out 0.2s forwards;
}

@keyframes slideUp {
  0% {
    opacity: 0;
    transform: translateY(40px);
  }

  100% {
    opacity: 1;
    transform: translateY(0);
  }
}
```

------------------------------------------------------------------------

# 🔄 Interpolação e Easing

Por padrão, a interpolação é **linear**.

Pode ser alterada com:

-   `ease`
-   `ease-in`
-   `ease-out`
-   `ease-in-out`
-   `cubic-bezier()`
-   `steps()`

Exemplo com curva personalizada:

``` css
animation-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
```

------------------------------------------------------------------------

# 🚀 Performance e Renderização

## 🔥 O que é otimizado pela GPU?

Animações que usam:

-   `transform`
-   `opacity`

Essas propriedades são processadas na **compositor thread**, evitando
reflow e repaint.

## ❌ Evite animar:

-   `width`
-   `height`
-   `margin`
-   `top/left`

Essas causam **layout recalculation (reflow)**.

------------------------------------------------------------------------

# 🧱 Stacking Context e Camadas

Animações com `transform` criam novos contextos de empilhamento.

Isso impacta:

-   `z-index`
-   Renderização 3D
-   Sobreposição de elementos

------------------------------------------------------------------------

# ♿ Acessibilidade

Sempre respeite usuários sensíveis a movimento:

``` css
@media (prefers-reduced-motion: reduce) {
  * {
    animation: none !important;
  }
}
```

------------------------------------------------------------------------

# 🎮 Eventos JavaScript

Animações disparam eventos:

-   `animationstart`
-   `animationend`
-   `animationiteration`

Exemplo:

``` javascript
element.addEventListener("animationend", () => {
  console.log("Animação concluída");
});
```

------------------------------------------------------------------------

# 🎨 Exemplos Práticos

## 🔁 Rotação com Mudança de Cor

``` css
@keyframes colorSpin {
  0%   { background: red;   transform: rotate(0deg); }
  33%  { background: green; transform: rotate(120deg); }
  66%  { background: blue;  transform: rotate(240deg); }
  100% { background: red;   transform: rotate(360deg); }
}

.wheel {
  animation: colorSpin 4s linear infinite;
}
```

------------------------------------------------------------------------

## 🏀 Efeito Bounce

``` css
@keyframes bounce {
  0%, 100% { transform: translateY(0); }
  50%      { transform: translateY(-20px); }
}

.ball {
  animation: bounce 1s infinite ease-in-out;
}
```

------------------------------------------------------------------------

# 📌 Conclusão

`@keyframes` é a base da animação avançada no CSS moderno.

Ela permite:

-   Criar motion design sofisticado\
-   Melhorar experiência do usuário\
-   Trabalhar com microinterações\
-   Construir interfaces mais dinâmicas\
-   Manter alta performance quando usada corretamente

Dominar `@keyframes` significa dominar o movimento na web.