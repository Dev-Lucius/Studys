# HTML & CSS — Guia melhorado

Este documento é uma apostila compacta sobre HTML (com notas sobre CSS e JavaScript). Corrigi erros, removi duplicações e adicionei um Índice para facilitar a leitura e os estudos.

---

## Índice

- [Introdução](#introducao)
- [Metáfora: casa, HTML, CSS e JS](#metafora)
- [Estrutura básica de um documento](#estrutura-basica-de-um-documento)
- [Metadados (`head`)](#metadados-head)
- [Elementos de sectioning](#elementos-de-sectioning)
  - [`main`, `article`, `section`, `nav`, `aside`, `header`, `footer`, `address`]
- [Conteúdo textual e inline](#conteudo-textual-e-inline)
- [Listas e definições](#listas-e-definicoes)
- [Figuras e multimídia](#figuras-e-multimidia)
- [Conteúdo incorporado (`iframe`, `embed`, `object`)](#conteudo-incorporado)
- [Tabelas](#tabelas)
- [Formulários](#formularios)
- [Boas práticas rápidas](#boas-praticas-rapidas)
- [Referências](#referencias)

---

## Introdução

- HTML (Linguagem de Marcação de Hipertexto) é a base estrutural da Web: define o que cada parte da página significa.
- CSS trata da aparência; JavaScript trata do comportamento e da interatividade.

## Metáfora

- Pense no HTML como a estrutura da casa (paredes, cômodos, portas).
- O CSS é o design de interiores (cores, fontes, espaçamentos).
- O JavaScript é a automação (luzes, portas automáticas, interações).

## Estrutura básica de um documento

Um documento HTML típico:

```html
<!doctype html>
<html lang="pt-BR">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Meu Projeto — Página Inicial</title>
    <link rel="stylesheet" href="/styles/main.css">
  </head>
  <body>
    <header>...</header>
    <main>...</main>
    <footer>...</footer>
  </body>
</html>
```

## Metadados (`head`)

- `<meta charset>` define a codificação (use `utf-8`).
- `<meta name="viewport">` é essencial para páginas responsivas.
- `<title>` aparece na aba do navegador e nos resultados de busca.
- `<link>` conecta recursos externos (CSS, favicons, preload).
- Use `<style>` apenas para trechos pequenos; prefira CSS externo para projetos maiores.

## Elementos de sectioning

Esses elementos criam a estrutura semântica (outline) do documento.

### `<main>`
- Conteúdo principal da página. Deve existir apenas um por página e estar dentro do `<body>`.

### `<article>`
- Conteúdo autocontido que pode fazer sentido isoladamente (post, card, comentário).

### `<section>`
- Seção temática; normalmente deve ter um título.

### `<nav>`
- Blocos de navegação; use para menus principais, índices e navegações repetitivas.

### `<aside>`
- Conteúdo tangencial (sidebars, links relacionados, biografia do autor).

### `<header>` e `<footer>`
- Introdução e rodapé de uma seção ou do documento. Podem aparecer em `article`, `section` e no `body`.

### `<address>`
- Informações de contato relacionadas ao conteúdo (autor, publicação). Não use para endereços genéricos.

### Títulos (`<h1>`–`<h6>`)
- Use-os em ordem lógica para formar o outline; são importantes para acessibilidade e SEO.

## Conteúdo textual e inline

### `<p>` — parágrafo
- Bloco básico de texto; pode conter elementos inline.

### Citações
- `<blockquote>` para citações longas (pode usar `cite`).
- `<q>` para citações curtas inline.
- `<cite>` indica a fonte/obra.

### Ênfase e destaque
- `<em>` (ênfase semântica);
- `<strong>` (importância);
- `<b>`, `<i>` — estilização semântica menor (use com critério);
- `<mark>` para destaque temporário;
- `<u>` para anotação textual (evite usar apenas por estilo);
- `<small>` para notas secundárias;
- `<s>` para conteúdo obsoleto; para alterações use `<del>`/`<ins>`.

### Trechos de código e entradas
- `<code>`, `<kbd>`, `<samp>`, `<var>` são usados para marcar código, entrada do usuário, saída e variáveis.

### Abreviações e definições
- `<abbr title="...">` e `<dfn>` para definições.

### Direção e internacionalização
- `<bdi>`, `<bdo>` para controle de direção do texto.

## Listas e definições

- `<ul>`, `<ol>` e `<li>` para listas.
- `<dl>`, `<dt>`, `<dd>` para listas de definição (glossários).

## Figuras e multimídia

### Imagens

- `<img src="..." alt="descrição">` — sempre inclua `alt` para acessibilidade.
- Para imagens responsivas e formatos múltiplos, use `<picture>` + `<source>`:

```html
<picture>
  <source srcset="imagem.webp" type="image/webp">
  <source srcset="imagem.jpg" type="image/jpeg">
  <img src="imagem.jpg" alt="Descrição da imagem">
</picture>
```

### Áudio e vídeo

- `<audio controls>` com `<source>` e `<track>` (WebVTT) para legendas.
- `<video controls>` com múltiplas fontes e `<track>` para legendas.
- Evite autoplay sem controle do usuário.

### Mapas de imagem
- `<map>` + `<area>` define hotspots clicáveis em imagens antigas; use com parcimônia.

## Conteúdo incorporado

- `<iframe>`: incorpora outra página (isolamento, histórico próprio).
- `<embed>` e `<object>`: incorporação de recursos externos (PDFs, conteúdos legados).
- `<portal>`: recurso experimental para transições de navegação — suporte limitado.

## Tabelas

- Estrutura: `<table>`, `<caption>`, `<colgroup>`, `<thead>`, `<tbody>`, `<tfoot>`, `<tr>`, `<th>`, `<td>`.
- Use `scope="col"`/`scope="row"` em `<th>` para acessibilidade.

Exemplo mínimo:

```html
<table>
  <caption>Relatório de Notas</caption>
  <thead>
    <tr><th scope="col">Aluno</th><th scope="col">Nota</th></tr>
  </thead>
  <tbody>
    <tr><td>Lucas</td><td>9.5</td></tr>
  </tbody>
</table>
```

## Formulários

- `<form action="..." method="GET|POST">` contém controles de entrada.
- `<input>` com vários `type` (text, email, number, checkbox, radio, file, hidden, etc.).
- `<textarea>`, `<select>` + `<option>`, `<datalist>`, `<optgroup>`.
- Use `<label for="id">` para associar rótulos e melhorar acessibilidade.
- `<fieldset>` e `<legend>` agrupam campos relacionados.

Exemplo:

```html
<form action="/cadastro" method="POST">
  <fieldset>
    <legend>Cadastro</legend>
    <label for="nome">Nome</label>
    <input id="nome" name="nome" required>
    <button type="submit">Enviar</button>
  </fieldset>
</form>
```

### Indicadores e resultados

- `<meter>` para um valor dentro de um intervalo (ex.: bateria).
- `<progress>` para progresso concluído.
- `<output>` para resultados calculados.

## Boas práticas rápidas

- Sempre inclua `alt` em imagens.
- Use `lang` no `<html>` e `charset="utf-8"` no `<head>`.
- Prefira CSS externo e evite estilos inline quando possível.
- Use elementos semânticos (`main`, `article`, `nav`, `section`) em vez de `div` genéricas.
- Valide seu HTML (W3C/validators) e teste com leitores de tela.

## Referências

- MDN Web Docs — HTML: https://developer.mozilla.org/pt-BR/docs/Web/HTML

---

Se quiser, posso:
- aplicar exemplos interativos (pequenas páginas de demonstração);
- gerar um índice com links internos mais detalhado;
- adicionar exercícios e respostas ao final de cada seção.


## Tags de Semântica Textual

Os **elementos de semântica textual inline** são utilizados para definir o **significado, estrutura ou estilo de pequenos trechos de texto** dentro de um fluxo textual maior, como palavras, frases ou partes específicas de um parágrafo.

Eles são chamados de **inline** porque:
- Não criam quebras de linha automaticamente
- Funcionam dentro do fluxo do texto
- Enriquecem o significado semântico do conteúdo

Esses elementos são fundamentais para:
- Acessibilidade
- SEO
- Clareza semântica
- Organização de conteúdo técnico
- Experiência do usuário

---

# Links e Navegação

## `<a>` — hiperlink (âncora)

O elemento `<a>` cria ligações para:
- Outras páginas
- Arquivos
- E-mails
- Partes da mesma página
- URLs externas

### Características:
- O atributo `href` define o destino do link
- O conteúdo da tag deve indicar claramente o destino
- Base da navegação na web

---

# Destaques e Ênfase Textual

## `<em>` — ênfase semântica

Marca texto com **ênfase**, indicando maior importância na leitura.

### Características:
- Pode ser aninhado para aumentar o nível de ênfase
- Possui significado semântico real

---

## `<strong>` — forte importância

Representa texto com **alta importância semântica**.

### Diferença importante:
- `<strong>` transmite relevância
- `<b>` apenas estiliza visualmente

---

## `<b>` — destaque visual sem importância semântica

Usado para destacar texto visualmente sem indicar importância.

### Exemplos comuns:
- Palavras-chave
- Nomes de produtos
- Frase inicial de parágrafos

---

## `<i>` — destaque contextual

Representa texto diferenciado por contexto, como:
- Termos técnicos
- Expressões estrangeiras
- Pensamentos de personagens

---

## `<mark>` — destaque por relevância

Destaca texto relevante dentro de um contexto específico.

### Uso comum:
- Resultados de busca
- Informações importantes temporariamente destacadas

---

## `<u>` — anotação textual

Indica texto com anotação não textual.

### Observação:
- Não deve ser usado apenas para estilização
- Representa significado adicional no conteúdo

---

## `<small>` — comentários secundários

Representa observações menores, como:
- Informações legais
- Direitos autorais
- Notas de rodapé

---

## `<s>` — conteúdo não mais relevante

Representa texto que não está mais correto ou relevante.

⚠️ Não deve ser usado para edições.  
Para edições, utilize `<del>` e `<ins>`.

---

# Citações e Referências

## `<cite>` — referência a obras

Representa referência a:
- Livros
- Filmes
- Artigos
- Obras artísticas

---

## `<q>` — citação curta

Representa citações curtas dentro do texto.

### Diferença:
- `<q>` → citações curtas
- `<blockquote>` → citações longas

---

# Abreviações e Definições

## `<abbr>` — abreviação

Representa abreviações e siglas.

### Boa prática:
- Usar atributo `title` com significado completo

---

## `<dfn>` — definição de termo

Indica a primeira ocorrência onde um termo está sendo definido.

---

# Programação, Computação e Variáveis

## `<code>` — fragmento de código

Indica pequenos trechos de código.

### Características:
- Fonte monoespaçada
- Muito usado em documentação técnica

---

## `<kbd>` — entrada do usuário

Representa dados inseridos pelo usuário:
- Teclado
- Comandos
- Entrada por voz

---

## `<samp>` — saída de programa

Representa saída gerada por programas ou sistemas.

---

## `<var>` — variável

Representa variáveis matemáticas ou de programação.

---

# Dados, Datas e Informações Estruturadas

## `<data>` — valor legível por máquina

Associa conteúdo visual com um valor estruturado para máquinas.

---

## `<time>` — data e hora

Representa datas e horários com significado semântico.

### Pode incluir:
- Data completa
- Horário
- Fuso horário

---

# Direção e Internacionalização de Texto

## `<bdi>` — isolamento bidirecional

Isola trechos que podem possuir direção de leitura diferente.

---

## `<bdo>` — sobrescrita de direção

Força uma direção específica do texto.

---

# Ruby Annotations (Pronúncia Asiática)

## `<ruby>` — anotação fonética

Usado para exibir pronúncia de caracteres asiáticos.

---

## `<rt>` — texto de pronúncia

Define a pronúncia dentro de `<ruby>`.

---

## `<rp>` — fallback de compatibilidade

Fornece parênteses alternativos para navegadores sem suporte a ruby.

---

# Estrutura e Organização Inline

## `<span>` — container genérico inline

Agrupa conteúdo sem significado semântico próprio.

### Uso correto:
- Aplicação de estilos
- Organização via classes e IDs

---

# Elementos Tipográficos

## `<sub>` — subscrito

Exibe texto abaixo da linha base.

### Exemplos:
- Fórmulas químicas
- Índices matemáticos

---

## `<sup>` — sobrescrito

Exibe texto acima da linha base.

### Exemplos:
- Potências matemáticas
- Referências

---

# Controle de Quebra de Linha

## `<br>` — quebra de linha

Força uma quebra de linha sem iniciar novo parágrafo.

### Uso ideal:
- Poemas
- Endereços
- Formatações específicas

---

## `<wbr>` — quebra opcional

Indica posição onde o navegador pode quebrar a linha se necessário.

---

# Importância Semântica Geral

Essas tags permitem:

- Melhor compreensão do conteúdo por leitores de tela
- Organização semântica refinada
- Melhor indexação por buscadores
- Representação correta de conteúdos técnicos e acadêmicos
- Melhor experiência do usuário

---

# Tabela-Resumo

| Elemento | Função |
|----------|----------|
| `<a>` | Criar hyperlinks |
| `<abbr>` | Abreviações |
| `<b>` | Destaque visual |
| `<bdi>` | Isolamento direcional |
| `<bdo>` | Forçar direção do texto |
| `<br>` | Quebra de linha |
| `<cite>` | Referência a obras |
| `<code>` | Fragmento de código |
| `<data>` | Valor legível por máquina |
| `<dfn>` | Definição de termo |
| `<em>` | Ênfase |
| `<i>` | Destaque contextual |
| `<kbd>` | Entrada do usuário |
| `<mark>` | Destaque relevante |
| `<q>` | Citação curta |
| `<ruby>` | Anotação fonética |
| `<rt>` | Pronúncia ruby |
| `<rp>` | Fallback ruby |
| `<s>` | Texto obsoleto |
| `<samp>` | Saída de programa |
| `<small>` | Comentários secundários |
| `<span>` | Container inline genérico |
| `<strong>` | Forte importância |
| `<sub>` | Subscrito |
| `<sup>` | Sobrescrito |
| `<time>` | Datas e horários |
| `<u>` | Anotação textual |
| `<var>` | Variáveis |
| `<wbr>` | Quebra opcional de linha |

---

# Síntese Final

> As **tags de semântica textual inline** refinam o significado do conteúdo textual, permitindo que o HTML represente não apenas aparência, mas também intenção, contexto e função comunicativa do texto.

Elas são essenciais para a construção de documentos HTML modernos, acessíveis e semanticamente corretos.

---

## Tags de Semântica e Multimídia

O HTML oferece suporte nativo a **recursos multimídia**, permitindo a incorporação de **imagens, áudio e vídeo** diretamente em páginas web, sem a necessidade de plugins externos. Esses elementos são essenciais para enriquecer a experiência do usuário, transmitir informações de forma visual e sonora e tornar aplicações web mais interativas e acessíveis.

As **tags de imagem e multimídia** fazem parte do conteúdo exibido ao usuário e devem ser usadas de forma semântica, considerando **acessibilidade, desempenho e compatibilidade entre navegadores**.

---

## `<img>` — inserção de imagens

O elemento `<img>` representa a **inserção de uma imagem** no documento HTML.

### Características:
- É um elemento vazio (não possui tag de fechamento)
- O atributo `src` define o caminho da imagem
- O atributo `alt` fornece um texto alternativo (essencial para acessibilidade e SEO)
- Integra-se muito bem com `<figure>` e `<figcaption>`

### Importância do `alt`:
- Leitores de tela utilizam o texto alternativo
- Exibido quando a imagem não pode ser carregada
- Ajuda mecanismos de busca a entender o conteúdo visual

---

## `<figure>` e `<figcaption>` — imagem como unidade semântica

Embora não sejam exclusivamente multimídia, `<figure>` e `<figcaption>` são amplamente usados com imagens.

- `<figure>` agrupa um conteúdo visual autocontido
- `<figcaption>` fornece uma legenda descritiva associada à figura

A imagem e sua legenda passam a ser tratadas como **uma única unidade semântica**.

---

## `<audio>` — conteúdo de áudio

O elemento `<audio>` é usado para **incorporar sons** em um documento HTML. Foi introduzido no HTML5.

### Características:
- Suporta controles nativos (`controls`)
- Pode conter múltiplas fontes (`<source>`) para compatibilidade
- Permite reprodução, pausa e controle de volume
- Pode ser usado para músicas, podcasts, efeitos sonoros, etc.

### Acessibilidade:
- Pode ser combinado com `<track>` para legendas ou transcrições
- Deve evitar reprodução automática sem controle do usuário

---

## `<video>` — conteúdo de vídeo

O elemento `<video>` permite **incorporar vídeos** diretamente no HTML, também introduzido no HTML5.

### Características:
- Suporta controles nativos
- Pode conter múltiplas fontes para diferentes formatos
- Permite reprodução local sem plugins externos
- Suporta legendas, descrições e capítulos

O `<video>` é amplamente usado em:
- Plataformas educacionais
- Streaming
- Apresentações institucionais
- Conteúdo interativo

---

## `<track>` — faixas de texto temporizadas

O elemento `<track>` é usado como **filho de `<audio>` ou `<video>`** para fornecer **faixas de texto sincronizadas com o tempo**.

### Usos comuns:
- Legendas
- Closed captions
- Descrições de áudio
- Capítulos

### Características:
- Utiliza arquivos no formato **WebVTT (`.vtt`)**
- Essencial para acessibilidade
- Pode definir idioma, tipo da faixa e se é padrão

O `<track>` torna o conteúdo multimídia mais inclusivo e compreensível.

---

## `<map>` — mapa de imagem

O elemento `<map>` define um **mapa de imagem**, permitindo criar áreas clicáveis dentro de uma imagem.

### Características:
- Trabalha em conjunto com `<img>` e `<area>`
- Associa regiões específicas da imagem a links
- Muito usado em diagramas interativos e plantas ilustradas

O `<map>` não exibe nada visualmente por si só, apenas define as áreas interativas.

---

## `<area>` — região clicável da imagem

O elemento `<area>` define uma **região interativa (hot-spot)** dentro de um mapa de imagem.

### Características:
- Deve estar dentro de um `<map>`
- Pode ter formatos como retângulo, círculo ou polígono
- Pode conter links, descrições e textos alternativos

Cada `<area>` representa uma área específica da imagem que pode ser clicada ou acionada.

---

## Boas práticas para imagens e multimídia

- Sempre usar `alt` em `<img>`
- Oferecer controles ao usuário em `<audio>` e `<video>`
- Utilizar `<track>` para legendas e acessibilidade
- Evitar autoplay sem consentimento
- Usar formatos otimizados para desempenho
- Combinar elementos multimídia com semântica adequada

---

## Importância semântica e acessibilidade

O uso correto dessas tags permite:
- Melhor experiência para usuários com deficiência
- Conteúdo acessível a leitores de tela
- Melhor indexação por buscadores
- Menor dependência de tecnologias externas
- Maior controle sobre mídia nativa no navegador

---

## Tabela-Resumo

| Elemento | Função principal |
|--------|------------------|
| `<img>` | Inserção de imagens |
| `<figure>` | Agrupar conteúdo visual |
| `<figcaption>` | Legenda da figura |
| `<audio>` | Incorporar áudio |
| `<video>` | Incorporar vídeo |
| `<track>` | Legendas e faixas temporizadas |
| `<map>` | Definir mapa de imagem |
| `<area>` | Região clicável da imagem |

---

## Síntese Final

> As **tags de imagem e multimídia** permitem que o HTML vá além do texto, incorporando elementos visuais e sonoros de forma nativa, semântica e acessível.

---

## Tags de Imagem e Multimídia

O HTML oferece suporte nativo a **recursos multimídia**, permitindo a incorporação de **imagens, áudio e vídeo** diretamente em páginas web, sem a necessidade de plugins externos. Esses elementos são essenciais para enriquecer a experiência do usuário, transmitir informações de forma visual e sonora e tornar aplicações web mais interativas e acessíveis.

As **tags de imagem e multimídia** fazem parte do conteúdo exibido ao usuário e devem ser usadas de forma semântica, considerando **acessibilidade, desempenho e compatibilidade entre navegadores**.

---

## `<img>` — inserção de imagens

O elemento `<img>` representa a **inserção de uma imagem** no documento HTML.

### Características:
- É um elemento vazio (não possui tag de fechamento)
- O atributo `src` define o caminho da imagem
- O atributo `alt` fornece um texto alternativo (essencial para acessibilidade e SEO)
- Integra-se muito bem com `<figure>` e `<figcaption>`

### Importância do `alt`:
- Leitores de tela utilizam o texto alternativo
- Exibido quando a imagem não pode ser carregada
- Ajuda mecanismos de busca a entender o conteúdo visual

---

## `<figure>` e `<figcaption>` — imagem como unidade semântica

Embora não sejam exclusivamente multimídia, `<figure>` e `<figcaption>` são amplamente usados com imagens.

- `<figure>` agrupa um conteúdo visual autocontido
- `<figcaption>` fornece uma legenda descritiva associada à figura

A imagem e sua legenda passam a ser tratadas como **uma única unidade semântica**.

---

## `<audio>` — conteúdo de áudio

O elemento `<audio>` é usado para **incorporar sons** em um documento HTML. Foi introduzido no HTML5.

### Características:
- Suporta controles nativos (`controls`)
- Pode conter múltiplas fontes (`<source>`) para compatibilidade
- Permite reprodução, pausa e controle de volume
- Pode ser usado para músicas, podcasts, efeitos sonoros, etc.

### Acessibilidade:
- Pode ser combinado com `<track>` para legendas ou transcrições
- Deve evitar reprodução automática sem controle do usuário

---

## `<video>` — conteúdo de vídeo

O elemento `<video>` permite **incorporar vídeos** diretamente no HTML, também introduzido no HTML5.

### Características:
- Suporta controles nativos
- Pode conter múltiplas fontes para diferentes formatos
- Permite reprodução local sem plugins externos
- Suporta legendas, descrições e capítulos

O `<video>` é amplamente usado em:
- Plataformas educacionais
- Streaming
- Apresentações institucionais
- Conteúdo interativo

---

## `<track>` — faixas de texto temporizadas

O elemento `<track>` é usado como **filho de `<audio>` ou `<video>`** para fornecer **faixas de texto sincronizadas com o tempo**.

### Usos comuns:
- Legendas
- Closed captions
- Descrições de áudio
- Capítulos

### Características:
- Utiliza arquivos no formato **WebVTT (`.vtt`)**
- Essencial para acessibilidade
- Pode definir idioma, tipo da faixa e se é padrão

O `<track>` torna o conteúdo multimídia mais inclusivo e compreensível.

---

## `<map>` — mapa de imagem

O elemento `<map>` define um **mapa de imagem**, permitindo criar áreas clicáveis dentro de uma imagem.

### Características:
- Trabalha em conjunto com `<img>` e `<area>`
- Associa regiões específicas da imagem a links
- Muito usado em diagramas interativos e plantas ilustradas

O `<map>` não exibe nada visualmente por si só, apenas define as áreas interativas.

---

## `<area>` — região clicável da imagem

O elemento `<area>` define uma **região interativa (hot-spot)** dentro de um mapa de imagem.

### Características:
- Deve estar dentro de um `<map>`
- Pode ter formatos como retângulo, círculo ou polígono
- Pode conter links, descrições e textos alternativos

Cada `<area>` representa uma área específica da imagem que pode ser clicada ou acionada.

---

## Boas práticas para imagens e multimídia

- Sempre usar `alt` em `<img>`
- Oferecer controles ao usuário em `<audio>` e `<video>`
- Utilizar `<track>` para legendas e acessibilidade
- Evitar autoplay sem consentimento
- Usar formatos otimizados para desempenho
- Combinar elementos multimídia com semântica adequada

---

## Importância semântica e acessibilidade

O uso correto dessas tags permite:
- Melhor experiência para usuários com deficiência
- Conteúdo acessível a leitores de tela
- Melhor indexação por buscadores
- Menor dependência de tecnologias externas
- Maior controle sobre mídia nativa no navegador

---

## Tabela-Resumo

| Elemento | Função principal |
|--------|------------------|
| `<img>` | Inserção de imagens |
| `<figure>` | Agrupar conteúdo visual |
| `<figcaption>` | Legenda da figura |
| `<audio>` | Incorporar áudio |
| `<video>` | Incorporar vídeo |
| `<track>` | Legendas e faixas temporizadas |
| `<map>` | Definir mapa de imagem |
| `<area>` | Região clicável da imagem |

---

## Síntese Final

> As **tags de imagem e multimídia** permitem que o HTML vá além do texto, incorporando elementos visuais e sonoros de forma nativa, semântica e acessível.

Quando bem utilizadas, essas tags transformam páginas web em **experiências ricas, interativas e inclusivas**, alinhadas com os padrões modernos da web.


---

## Tags de Conteúdo Integrado

Além dos conteúdos multimídia tradicionais como **imagens, áudio e vídeo**, o HTML permite a incorporação de **recursos externos e contextos de navegação completos**, possibilitando experiências mais ricas, interativas e dinâmicas na Web.

Essas tags são amplamente utilizadas para conteúdos responsivos, mídia alternativa, integração com outras páginas e aplicações externas.

## `<embed>` - Incorporação de Conteúdo Externo

O elemento <embed> é **utilizado para incorporar conteúdo externo diretamente no documento HTML**, como PDFs, animações, vídeos antigos ou aplicações fornecidas por plugins.

### Características 

- Insere Conteúdo que não é nativamente
- Não possui conteúdo alternativo interno
- Uso comum para PDFs, animações e recursos legados
- Exemplo
    ```html
    <embed src="arquivo.pdf" type="application/pdf">
    ```
- 📌 Seu uso vem sendo substituído por alternativas mais modernas, como `<iframe>` e `<object>`

---

## `<iframe>` - Contexto de Navegação Aninhado

O elemento `<iframe>` permite incorporar uma página HTML completa dentro de outra, 
criando um contexto de navegação independente.

### Características:

- Possui histórico de navegação próprio
- Isola o conteúdo incorporado da página principal
- Amplamente utilizado para vídeos, mapas, formulários externos e sistemas integrados
- Exemplos: 
    ```html
    <iframe src="https://exemplo.com" width="600" height="400"></iframe>
    ```
- Cada `<iframe>` cria um contexto de navegação filho, enquanto a página principal atua como contexto pai.

---

## `<object>` - Recurso Externo Multifuncional

O elemento `<object>` representa um recurso externo genérico, que pode ser tratado 
como imagem, documento, conteúdo interativo ou recurso controlado por plugin.

### Vantagens:

- Permite definir conteúdos alternativos
- Mais flexível que `<embed>`
- Compatível com diversos tipos de mídia
- Exemplos:
    ```html
    <object data="arquivo.pdf" type="application/pdf">
        Seu navegador não suporta este conteúdo.
    </object>
    ```

---

## `<portal>` - Incorporação para Navegação Suave

O elemento `<portal>` permite **incorporar outra página HTML com foco em transições suaves de naveção**, de tal modo a permitir 
que o conteúdo incorporado se torne a página principal

### Observações:

- Trata-se de recurso moderno e experimental
- Suporte limitado em navegadores
- Voltado para experiências de navegação imersivas
- Exemplos:
    ```html
    <portal src="outra-pagina.html"></portal>
    ```

--- 

## `<pictures>` - Imagens Responsivas

O elemento `<picture>` trata-se de um **container para imagens adapatativas**, de tal modo a permitir 
que o navegador selecione automaticamente a imagem mais adequada com base em nos seguintes aspectos:

- Tamanho da Tela
- Resolução do Dispositivo (HiDPI)
- Suporte a formatos de Imagem

### Estrutura:

- Usa múltiplos `<source>`
- Contém obrigatoriamente um `<img>` como fallback
- Exemplos:
    ```html
    <picture>
        <source srcset="imagem.webp" type="image/webp">
        <source srcset="imagem.png" type="image/png">
        <img src="imagem.jpg" alt="Imagem responsiva">
    </picture>
    ```

---

## `<source>` - Fontes Alternativas de Mídia

O elemento `<source>` é usado para **definir múltiplos formatos de mídia**, a fim de garantir 
compatibilidade entre navegadores


### Pode ser usado dentro de:

- `<picture>`
- `<audio>`
- `<video>`
- Exemplos:
    ```html
    <video controls>
        <source src="video.mp4" type="video/mp4">
        <source src="video.webm" type="video/webm">
    </video>

    ```
## Tabela Resumo

| Tag         | Função Principal                      | Uso Comum                   |
| ----------- | ------------------------------------- | --------------------------- |
| `<embed>`   | Incorpora conteúdo externo via plugin | PDFs, mídia legada          |
| `<iframe>`  | Incorpora páginas HTML completas      | Vídeos, mapas, sistemas     |
| `<object>`  | Recurso externo genérico com fallback | PDFs, conteúdos interativos |
| `<picture>` | Imagens responsivas e adaptativas     | Design responsivo           |
| `<portal>`  | Navegação suave entre páginas         | Experiências modernas       |
| `<source>`  | Define múltiplos formatos de mídia    | Compatibilidade             |

---

## Tags de Tabelas (Tabulação) no HTML

Os elementos de tabulação em HTML são utilizados para organizar dados em formato bidimensional (linhas e colunas). 
Eles são ideais para representar informações estruturadas, como:

- Relatórios
- Planilhas
- Listas Comparativas
- Dados comparativos
- Resultados de Sistemas

Uma tabela HTML é composta por diferentes elementos que definem sua estrutura semântica, melhorando acessibilidade, 
organização e interpretação por navegadores e leitores de tela

### Estrutura básica de uma Tabela

Uma tabela em HTML começa com o elemento <table>, que atua como o contêiner principal.

```html
<table>
  <tr>
    <th>Nome</th>
    <th>Idade</th>
  </tr>
  <tr>
    <td>Lucas</td>
    <td>20</td>
  </tr>
</table>
```

### `<table>` - Estrutura Principal

Representa uma **Tabela de Dados em duas ou mais Dimensões**.

Trata-se do elemento pai de todos os demais elementos da tabulação

### `<tr>` - Table Row (Linha)

Define uma Linha da tabela.

Cada `<tr>` pode conter:

- `<td>` (células de dados)
    * Define uma célula comum que contém **dados informativos**
    * Participa diretamente do modelo estrutural da Tabela
    * Exemplo:
    ```html
    <td> conteúdo </td>
    ```

- `<th>` (células de cabeçalho)
    * Define uma Célula de **Cabeçalho**, normalmente exibida em negrito e centralizada por padrão
    * Pode usar atributos como: 
        - **scope = "col"** -> Cabeçalho de coluna 
        - **scope = "row"** ->  Cabeçalho de Linha
    * Exemplo
    ```html
    <th scope = "col"> nome </th>
    ```

##
HTML permite dividir a tabela em três grandes blocos semânticos:

- Cabeçalho
- Corpo
- Rodapé

### `<thead>` - Cabeçalho da Tabela

Define o conjunto de linhas que compõem o **cabeçalho da tabela**

```html
<thead>
  <tr>
    <th>Produto</th>
    <th>Preço</th>
  </tr>
</thead>
```

### `<tbody>` - Corpo da Tabela

Agrupa Linhas que compõem o **corpo principal da tabela**

```html
<tbody>
  <tr>
    <td>Notebook</td>
    <td>R$ 3000</td>
  </tr>
</tbody>
```

### `<tfoot>` - Rodapé da Tabela

Define o conjunto de linhas que pertencem ao **rodapé da tabela**, geralmente usado para:

- Totais
- Resumos
- Observações finais

```html
<tfoot>
  <tr>
    <td>Total</td>
    <td>R$ 3000</td>
  </tr>
</tfoot>
```

## Organização de Colunas

Além das linhas, o HTML permite organizar e estilizar colunas.

### `<colgroup>` — Grupo de Colunas

Define um grupo de colunas dentro da tabela.
Usado principalmente para:

- Aplicar estilos em múltiplas colunas
- Organização estrutural

### `<col>`— Coluna Individual

Define propriedades semânticas e de estilo para uma coluna específica.
Normalmente usado dentro de `<colgroup>`.

- Exemplo: 
```html
<colgroup>
  <col style="background-color: lightgray;">
  <col>
</colgroup>
```

### `<caption>` - Legenda da Tabela

Define a **legenda ou título da tabela**.
Deve ser o primeiro elemento de `<table>`

```html
<table>
  <caption>Relatório de Vendas 2026</caption>
</table>
```

Importante para: 
- Acessibilidade 
- Organização Semântica
- Contextualização dos Dados

### Estrutura Completa de Exemplo:

```html
<table>
  <caption>Relatório de Notas</caption>

  <colgroup>
    <col>
    <col>
  </colgroup>

  <thead>
    <tr>
      <th scope="col">Aluno</th>
      <th scope="col">Nota</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>Lucas</td>
      <td>9.5</td>
    </tr>
  </tbody>

  <tfoot>
    <tr>
      <td>Média</td>
      <td>9.5</td>
    </tr>
  </tfoot>
</table>
```

### Tabela Resumo

| Tag          | Função Principal               | Papel na Estrutura     |
| ------------ | ------------------------------ | ---------------------- |
| `<table>`    | Contêiner principal da tabela  | Estrutura base         |
| `<tr>`       | Define uma linha               | Organização horizontal |
| `<td>`       | Célula de dados                | Conteúdo comum         |
| `<th>`       | Célula de cabeçalho            | Identificação de dados |
| `<thead>`    | Cabeçalho da tabela            | Organização semântica  |
| `<tbody>`    | Corpo da tabela                | Dados principais       |
| `<tfoot>`    | Rodapé da tabela               | Totais e resumos       |
| `<caption>`  | Título da tabela               | Contextualização       |
| `<colgroup>` | Agrupa colunas                 | Organização estrutural |
| `<col>`      | Define propriedades de colunas | Estilização            |

---

## Tags de Formulário no HTML

O HTML fornece diversos elementos que podem ser usados em conjunto para criar **formulários interativos**, permitindo que o usuário envie dados para um servidor ou aplicação.

Formulários são utilizados para:

- Login e autenticação  
- Cadastro de usuários  
- Pesquisas  
- Envio de mensagens  
- Compras online  
- Upload de arquivos  
- Configurações de sistemas  

Eles representam o principal mecanismo de interação entre usuário e backend.

---

# 🧠 Estrutura Fundamental

## `<form>`

Elemento principal que representa uma seção contendo controles interativos.

### Atributos principais:

- `action` → URL que receberá os dados  
- `method` → Método HTTP (`GET` ou `POST`)  
- `autocomplete` → Ativa ou desativa preenchimento automático  

### Exemplo:

```html
<form action="/processar" method="POST">
  <input type="text" name="nome">
  <button type="submit">Enviar</button>
</form>
```

## Controles de Entrada

### `<input>`

Elemento mais versátil dos formulários.
Seu comportamento depende do atributo **type**
Tipos comuns:

- text
- password 
- email
- number
- date
- checkbox
- radio
- file
- submit
- reset
- hidden

Exemplo: 

```html
<input type="email" name="email" required>
```

### `<textarea>` 

Cria um campo de texto multilinha
É ideal usar para:

- Comentários
- Feedback
- Mensagens Longas

Exemplos: 

```html
<textarea name="mensagem" rows="5" cols="30"></textarea>
```

### `<select>` 

Cria um Menu Suspenso (dropdown)
As opções são definidas por `<option>` que também é usado com `<optgroup>` e `<datalist>`

Exemplos: 

```html
<select name="cidade">
  <option value="rs">Rio Grande</option>
  <option value="sp">São Paulo</option>
</select>
```

### `<optgroup>`

Agrupa Opções dentro de um `<select>`

Exemplo:

```html
<select>
  <optgroup label="Brasil">
    <option>Rio Grande</option>
  </optgroup>
</select>
```

### `<datalist>`

Fornece sugestões automáticas para um `<input>`

Exemplo:

```html
<input list="cidades">
<datalist id="cidades">
  <option value="Rio Grande">
  <option value="Pelotas">
</datalist>
```

---

## Associação e Organização

### `<label>`

Define um rótulo para um campo
Pode ser associado de duas formas:

- Envolvendo o Input
- usando **for** e **id**

Exemplo:

```html
<!-- Importante para Acessibilidade e SEO -->
<label for="email">Email:</label>
<input id="email" type="email">
```

### `<fieldset>`

Agrupa campos relacionados dentro de um formulário.

### `<legend>`

Define o título do `<fieldset>`

Exemplo: 

```html
<fieldset>
  <legend>Dados Pessoais</legend>
</fieldset>
```

### Botões

Cria um botão clicável

Tipos: 

- submit
- reset
- button

Exemplo:

```html
<button type="submit"> Enviar </button>
```

---

## Elementos de Medição

### `<metter>`
Representa um valor dentro de um intervalo conhecido.

Exemplo:

```html
<meter value="0.6">60%</meter>
```

### `<progress>`
Exibe o Progresso de uma Tabela
Exemplo:

```html
<progress value="70" max="100"></progress>
```

### `<output>`
Exibe o resultado de um cálculo ou ação do usuário.

Exemplo:

```html
<output name="resultado"></output>
```

## Exemplo Completo

```html
<form action="/cadastro" method="POST">

  <fieldset>
    <legend>Cadastro</legend>

    <label for="nome">Nome:</label>
    <input id="nome" type="text" name="nome" required>

    <label for="email">Email:</label>
    <input id="email" type="email" name="email" required>

    <label for="cidade">Cidade:</label>
    <select id="cidade" name="cidade">
      <option>Rio Grande</option>
      <option>Pelotas</option>
    </select>

    <button type="submit">Enviar</button>

  </fieldset>

</form>
```

## Tabela Resumo

| Tag          | Função                            |
| ------------ | --------------------------------- |
| `<form>`     | Contêiner principal do formulário |
| `<input>`    | Campo de entrada versátil         |
| `<textarea>` | Campo de texto multilinha         |
| `<select>`   | Menu suspenso                     |
| `<option>`   | Opção dentro de select            |
| `<optgroup>` | Agrupa opções                     |
| `<datalist>` | Lista de sugestões                |
| `<label>`    | Rótulo de campo                   |
| `<fieldset>` | Agrupa campos relacionados        |
| `<legend>`   | Título do fieldset                |
| `<button>`   | Botão clicável                    |
| `<meter>`    | Indicador de valor                |
| `<progress>` | Barra de progresso                |
| `<output>`   | Exibe resultados                  |


## Demais tags HTML consultar

https://developer.mozilla.org/pt-BR/docs/Web/HTML
