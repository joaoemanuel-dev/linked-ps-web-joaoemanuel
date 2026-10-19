# Linked — Desafio Web

Projeto desenvolvido como parte do **Processo Seletivo da Linked Empresa Júnior**, na modalidade de Desenvolvimento Front-End.

O desafio consiste na implementação de uma landing page a partir de um layout previamente disponibilizado no Figma, buscando manter fidelidade visual, organização do código, responsividade e boas práticas de desenvolvimento front-end.

---

## 👤 Autor

**João Emanuel Pereira do Nascimento**

---

## 📌 Sobre o projeto

A proposta do desafio foi transformar em código um layout desenvolvido no Figma para um consultório de psicologia e psicoterapia.

A página foi construída utilizando HTML e CSS, buscando reproduzir da forma mais fiel possível:

- estrutura do layout;
- cores;
- tipografia;
- espaçamentos;
- imagens;
- elementos decorativos;
- cards;
- botões;
- navegação;
- organização das seções;
- comportamento responsivo.

Além da reprodução visual, também foi necessário adaptar alguns elementos do Figma para que funcionassem corretamente em diferentes tamanhos de tela.

---

## 🖥️ Seções da página

A landing page é composta pelas seguintes áreas:

- **Header e menu de navegação**
- **Hero / seção inicial**
- **Serviços**
- **Horário de atendimento**
- **Feedbacks**
- **Contato**
- **Formulário de contato**
- **Footer**
- **Links para redes sociais e acessos rápidos**

A navegação principal utiliza links internos para permitir o deslocamento entre as seções da própria página.

---

## 🛠️ Tecnologias e ferramentas utilizadas

### Desenvolvimento

- HTML5
- CSS3

### Ferramentas

- Visual Studio Code
- Git
- GitHub
- Figma

Não foram utilizados frameworks ou bibliotecas externas de componentes. Embora o desafio permitisse o uso de JavaScript, optei por não utilizá-lo porque os comportamentos necessários para esta implementação puderam ser atendidos apenas com HTML e CSS.

A página é essencialmente estática e não possui interações que exigissem lógica em JavaScript. Por isso, preferi manter a solução mais simples e direta, evitando adicionar código desnecessário.

---

## 📂 Estrutura do projeto

A estrutura principal do projeto foi organizada da seguinte forma:

```text
.
├── assets/
│   └── images/
│       ├── imagens da página
│       ├── ícones
│       ├── elementos decorativos
│       └── redes sociais
│
├── css/
│   └── style.css
│
├── js/
│   └── script.js
│
├── index.html
└── README.md
```

Essa organização separa a estrutura HTML, os estilos, scripts e arquivos visuais utilizados pela página.

---

## ▶️ Como executar o projeto

O projeto não possui dependências externas e não exige instalação de pacotes.

### Opção 1 — Abrindo diretamente no navegador

1. Clone ou baixe este repositório.
2. Acesse a pasta do projeto.
3. Abra o arquivo:

```text
index.html
```

O projeto será executado diretamente no navegador.

### Opção 2 — Utilizando o VS Code

Também é possível abrir a pasta do projeto no Visual Studio Code e utilizar uma extensão como o **Live Server** para executar a página localmente.

---

# 📱 Responsividade

A página foi desenvolvida para se adaptar a diferentes tamanhos de tela.

Foram utilizadas principalmente:

- CSS Grid;
- Flexbox;
- `overflow`;
- medidas relativas;
- media queries;
- alterações de direção dos elementos;
- redução e reorganização de componentes;
- ajustes específicos de tamanho e espaçamento.

A responsividade foi dividida principalmente entre:

### Desktop

Telas a partir de aproximadamente:

```css
1024px
```

O layout mantém a estrutura original do Figma, com elementos distribuídos horizontalmente.

### Tablet

Em tamanhos intermediários são realizados ajustes de:

- espaçamento;
- largura;
- tamanho das imagens;
- distância entre elementos;
- distribuição das colunas.

### Mobile

Em telas menores que:

```css
768px
```

diversas áreas passam a utilizar uma estrutura vertical.

Entre as principais mudanças estão:

- menu reorganizado;
- Hero em uma única coluna;
- imagem principal reposicionada;
- card de horários reorganizado verticalmente;
- feedbacks empilhados;
- seção de contato reorganizada;
- mapa ocupando maior largura;
- formulário adaptado;
- footer reorganizado em grid.

---

# 🎨 Decisões técnicas relevantes

Durante o desenvolvimento, alguns elementos do layout exigiram soluções específicas para funcionar corretamente fora do Figma.

As principais decisões estão descritas abaixo.

---

## 🖼️ Imagem principal da seção Hero

Um dos maiores desafios encontrados durante a implementação foi a imagem principal da seção Hero.

Inicialmente, a imagem foi exportada diretamente do Figma no formato **SVG**.

Porém, o SVG exportado possuía dimensões internas maiores do que a região visual realmente utilizada na página.

As curvas presentes na lateral da imagem continuavam dentro da área do SVG mesmo depois do término visual da fotografia.

Com isso, o navegador considerava toda essa área excedente como parte da imagem.

### Problema encontrado

No desktop, era possível esconder parte dessa sobra utilizando:

```css
overflow: hidden;
```

Entretanto, ao reduzir a largura da tela, a proporção do container mudava.

Como consequência, o navegador recalculava o enquadramento da imagem e partes que deveriam permanecer escondidas voltavam a aparecer.

Isso fazia com que a imagem mudasse de posição conforme a largura da tela diminuía.

Foram testadas algumas abordagens para solucionar o problema, incluindo:

- alteração da altura do SVG;
- alteração da largura;
- modificação do `viewBox`;
- utilização de `object-fit`;
- alteração de `object-position`;
- recorte através do container;
- utilização de `overflow: hidden`;
- reposicionamento da imagem pelo CSS.

Apesar de algumas dessas soluções funcionarem no desktop, o resultado não permanecia consistente durante a responsividade.

### Solução adotada

Como solução final, a imagem foi exportada novamente no formato **PNG**.

A área excedente gerada pelas curvas foi então recortada manualmente, deixando apenas a região realmente necessária para a página.

Dessa forma, o navegador passou a trabalhar com uma imagem já preparada para o enquadramento correto.

No CSS, a imagem é colocada dentro de um container com:

```css
overflow: hidden;
```

A imagem mantém um tamanho visual controlado e permanece alinhada à direita.

Quando a largura disponível diminui, o container passa a recortar a imagem em vez de reduzir excessivamente o seu tamanho.

Essa abordagem permitiu manter o enquadramento visual da referência e produzir um comportamento mais previsível durante a responsividade.

---

## 🧩 Estrutura da seção Hero

A seção principal foi organizada utilizando **CSS Grid**.

No desktop, a estrutura é dividida em duas regiões principais:

```text
┌──────────────────────────────────────────┐
│                                          │
│       Conteúdo          Imagem           │
│                                          │
│       Texto             Psicóloga        │
│       Botões                             │
│                                          │
└──────────────────────────────────────────┘
```

A utilização de Grid facilitou a separação entre conteúdo e imagem.

Em dispositivos móveis, essa estrutura passa para:

```css
grid-template-columns: 1fr;
```

fazendo com que os elementos sejam reorganizados verticalmente.

---

## 🌸 Elementos decorativos de fundo

Outro ponto que exigiu bastante ajuste foram os elementos decorativos presentes nas seções de **Horário de Atendimento** e **Contato**.

Esses elementos aparecem parcialmente fora da área visível no layout do Figma.

Por isso, simplesmente inserir as imagens no fluxo normal da página não reproduzia corretamente o design.

A solução foi utilizar:

```css
position: absolute;
```

nas imagens decorativas.

As seções que recebem esses elementos utilizam:

```css
position: relative;
```

permitindo que cada decoração seja posicionada em relação à própria seção.

---

## 📐 Ajuste manual das flores

O posicionamento das flores foi realizado manualmente para manter a fidelidade com o Figma.

Foram ajustados individualmente:

- largura;
- posição horizontal;
- posição vertical;
- rotação;
- opacidade.

Exemplo de propriedades utilizadas:

```css
left
right
top
bottom
transform: rotate(...)
```

Os valores foram ajustados em pixels até que o enquadramento visual se aproximasse da referência.

Em alguns casos, o mesmo elemento decorativo foi reutilizado e rotacionado para representar a decoração presente no lado oposto da página.

Por exemplo:

```css
transform: rotate(180deg);
```

Isso permitiu reutilizar o mesmo arquivo visual sem a necessidade de criar uma segunda imagem.

---

## 🌸 Flores e responsividade

Os elementos decorativos também precisaram ser adaptados para telas menores.

No desktop, eles possuem dimensões maiores para manter a composição visual do Figma.

No mobile, a largura desses elementos é reduzida e suas posições são alteradas para evitar que ocupem espaço excessivo ou interfiram no conteúdo principal.

Além disso, foi utilizado:

```css
pointer-events: none;
```

nos elementos decorativos.

Dessa forma, mesmo quando uma dessas imagens fica visualmente sobre outra área da página, ela não interfere nos cliques ou na navegação do usuário.

---

## 🕒 Card de horário de atendimento

Na seção de horários, existe um card posicionado sobre os elementos decorativos.

Inicialmente, um fundo completamente branco escondia grande parte das flores posicionadas atrás do card.

Para aproximar o resultado do Figma, foi utilizado um fundo branco com transparência:

```css
background-color: rgba(255, 255, 255, 0.4);
```

Assim, o conteúdo do card continua legível, mas os elementos decorativos permanecem parcialmente visíveis ao fundo.

Também foi utilizada sombra e borda para destacar o card sem perder o efeito de transparência.

---

## 📚 Organização dos horários

Os horários foram organizados utilizando Flexbox.

Cada linha contém:

- dia ou período de atendimento;
- horário correspondente.

As linhas são separadas visualmente por uma borda inferior, com exceção da última linha.

No mobile, o card altera sua direção para coluna, permitindo que relógio e horários ocupem melhor o espaço disponível.

---

## 💬 Seção de feedbacks

A seção de feedbacks utiliza Flexbox para organizar:

```text
Texto | Imagem
```

No desktop, os elementos permanecem lado a lado.

Em telas menores, passam para:

```css
flex-direction: column;
```

fazendo com que o conteúdo seja empilhado verticalmente.

A imagem também possui largura máxima para impedir que ultrapasse o tamanho previsto no layout.

---

## 📍 Seção de contato

A seção de contato possui:

- card de endereço;
- mapa;
- formulário;
- elementos decorativos.

No desktop, endereço e mapa são posicionados lado a lado.

Em dispositivos móveis, o layout passa para uma única coluna.

O mapa também recebe altura específica para evitar distorções durante a redução da tela.

Assim como na seção de horários, as flores decorativas são posicionadas de forma absoluta e permanecem atrás do conteúdo principal através do controle de `z-index`.

---

# ♿ Acessibilidade

Foram aplicadas algumas práticas básicas de acessibilidade durante o desenvolvimento.

Entre elas:

### Navegação por teclado

Links podem ser acessados através da tecla `Tab`.

Também foram utilizados estados de:

```css
:focus-visible
```

para destacar visualmente elementos quando a navegação é feita utilizando teclado.

### Hover

Links e botões possuem alterações visuais no estado:

```css
:hover
```

fornecendo retorno visual durante a interação com o mouse.

### Textos alternativos

Imagens relevantes possuem atributos:

```html
alt=""
```

ou descrições apropriadas de acordo com sua função.

Imagens utilizadas apenas como decoração possuem `alt` vazio para não adicionar informações desnecessárias aos leitores de tela.

### HTML semântico

A estrutura utiliza elementos HTML semânticos como:

```html
<header>
<nav>
<main>
<section>
<footer>
```

facilitando a organização e interpretação da página.

---

# 🧭 Navegação

O menu principal utiliza âncoras internas para acessar diretamente as principais seções da landing page.

Entre elas:

```text
Início
Serviços
Horários
Feedbacks
Contato
```

Também foi utilizado:

```css
scroll-behavior: smooth;
```

para que o deslocamento entre essas áreas aconteça suavemente.

---

# 🎯 Objetivos considerados durante o desenvolvimento

Durante a implementação, os principais objetivos foram:

- manter fidelidade visual ao Figma;
- utilizar HTML semântico;
- organizar o CSS por seções;
- criar uma página responsiva;
- manter o código legível;
- evitar dependências desnecessárias;
- manter os elementos decorativos sem interferir na usabilidade;
- preservar o enquadramento das imagens;
- implementar estados visuais de interação;
- utilizar Git de forma contínua durante o desenvolvimento.

---

# 📋 Principais desafios encontrados

Durante o projeto, os pontos que exigiram maior atenção foram:

### 1. Responsividade da imagem principal

O SVG exportado do Figma possuía uma área maior do que a região visual necessária, causando alterações inesperadas durante o redimensionamento da página.

A solução adotada foi substituir o SVG por uma versão PNG recortada manualmente e controlar seu enquadramento através do CSS.

### 2. Posicionamento dos elementos decorativos

As flores presentes no Figma não seguem o fluxo normal da página.

Por isso, foi necessário utilizar posicionamento absoluto e ajustar manualmente tamanho, rotação e coordenadas até obter um resultado semelhante à referência.

### 3. Adaptação do layout para mobile

Alguns componentes desenvolvidos originalmente lado a lado precisaram mudar completamente de organização em telas menores.

Foram utilizados Grid, Flexbox e media queries para reorganizar os elementos sem alterar a estrutura principal do HTML.

### 4. Manutenção da fidelidade visual

Diversos valores de:

- `padding`;
- `margin`;
- `gap`;
- largura;
- altura;
- posicionamento;
- rotação;

foram ajustados manualmente durante o desenvolvimento para aproximar o resultado final do design disponibilizado no Figma.

---

# 🌱 Aprendizados

O desenvolvimento deste projeto permitiu praticar principalmente:

- reprodução de layouts desenvolvidos no Figma;
- HTML semântico;
- CSS Grid;
- Flexbox;
- responsividade;
- media queries;
- posicionamento relativo e absoluto;
- controle de sobreposição com `z-index`;
- tratamento e enquadramento de imagens;
- estados de interação;
- acessibilidade básica;
- organização de estilos;
- utilização de Git e GitHub durante o desenvolvimento.

Também foi possível perceber que arquivos exportados diretamente de ferramentas de design nem sempre possuem o comportamento ideal para utilização na Web.

Em alguns casos, adaptar ou preparar o arquivo antes de utilizá-lo pode resultar em uma solução mais simples, previsível e responsiva.

---

# 🔗 Referência visual

Todo o desenvolvimento visual da página foi baseado no layout fornecido pela **Linked Empresa Júnior através do Figma** para o desafio técnico do processo seletivo.

O objetivo não foi criar uma identidade visual nova, mas transformar em código o design disponibilizado, realizando apenas as adaptações técnicas necessárias para seu funcionamento no navegador.

---

## ✅ Status do projeto

Projeto desenvolvido para entrega do desafio técnico do processo seletivo da **Linked Empresa Júnior**.
