# Relatório Técnico: Funcionalidade, Arquitetura e Construção do Projeto VR Stones

Este relatório descreve detalhadamente o projeto da Landing Page institucional da **VR Stones**, uma marmoraria e marcenaria de alto padrão. O documento aborda a finalidade do site, as decisões de arquitetura de software adotadas, a estrutura de marcação, o sistema de estilização e a lógica JavaScript que rege a interatividade da página.

---

## 1. Visão Geral e Proposta de Valor
A landing page da **VR Stones** foi desenvolvida para atuar como o principal canal digital de atração e conversão de clientes qualificados, incluindo arquitetos, designers de interiores, construtoras e consumidores finais do segmento residencial e comercial de luxo.

O objetivo do site é:
*   Apresentar o catálogo selecionado de rochas e superfícies nobres.
*   Evidenciar a precisão técnica do maquinário CNC e o know-how de acabamento artesanal.
*   Exibir o portfólio de projetos concluídos.
*   Prover canais diretos e funcionais de contato rápido (WhatsApp, telefone e formulário de orçamento).

---

## 2. Arquitetura do Projeto
O projeto adota a arquitetura de **Single-Page Application (SPA) Estática**, em que toda a interface é estruturada em um único arquivo autossuficiente (`index.html`). 

### Benefícios dessa abordagem:
1.  **Velocidade de Carregamento:** Sem requisições adicionais de páginas separadas. Os recursos principais são resolvidos imediatamente.
2.  **Facilidade de Implantação (Deploy):** Por consistir de um arquivo HTML estático associado a ativos hospedados em CDNs seguras, o deploy pode ser feito em qualquer provedor de hospedagem de arquivos estáticos de maneira direta.
3.  **Manutenibilidade Centralizada:** Facilita alterações rápidas em termos de marcação, estilo e lógica de script.

---

## 3. Estrutura Semântica (HTML5)
O esqueleto do projeto foi construído respeitando as tags semânticas recomendadas pela W3C, maximizando os índices de SEO (Search Engine Optimization) e acessibilidade:

*   `<nav>`: Barra de menu flutuante superior com logotipo e navegação principal por âncoras internas.
*   `<main>`: Invólucro principal que engloba o fluxo de conteúdo dinâmico.
*   `<section>`: Divisão clara de áreas temáticas do site:
    *   `#inicio` (Hero): Destaque inicial do site com imagem de fundo, título e CTAs primários.
    *   `#sobre`: Apresentação institucional e estatísticas chaves da empresa.
    *   `#materiais`: Catálogo dinâmico com filtros e carrossel interativo de pedras.
    *   `#projetos`: Portfólio visual com grade assimétrica.
    *   Recursos/Diferenciais: Demonstração de infraestrutura e serviços (corte de precisão, logística, etc.).
    *   Depoimentos: Provas sociais com avaliações de parceiros.
    *   `#contato`: Formulário de captação de leads e dados físicos de atendimento.
*   `<footer>`: Área institucional inferior contendo copyright, mapa de links rápidos, horários de atendimento e elementos decorativos de fundo.

---

## 4. Estilização e Design Visual (CSS & Tailwind CSS)
O sistema de estilo utiliza uma abordagem híbrida: a velocidade e padronização dos utilitários do **Tailwind CSS** combinada com regras personalizadas inseridas na tag `<style>`.

### 4.1. Configuração Customizada do Tailwind CSS
Um script de configuração estende o tema padrão do Tailwind injetando a identidade visual da VR Stones:
*   **Cores:** Uma paleta de tons escuros profundos (background `#0A0A0A` e superfícies `#131313`, `#1C1B1B`, `#2A2A2A`) associada ao verde neon luminoso (`#00FF41`) usado para elementos interativos primários e botões de chamada rápida.
*   **Tipografia:** Combinação de duas famílias do Google Fonts:
    *   *Space Grotesk:* Fontes geométricas modernas com alto contraste para cabeçalhos e títulos.
    *   *Outfit:* Fonte de alta legibilidade corporativa voltada para textos corridos e rótulos secundários.
*   **Espaçamento:** Definição de tokens de calha (`24px`), margens para desktops (`80px`), margens móveis (`20px`) e espaçamento regulado entre seções (`120px`).

### 4.2. Efeitos Visuais Premium via CSS Customizado
*   **Grain Overlay (Textura de Grão Analógico):** Uma imagem de ruído de alta frequência com apenas `0.04` de opacidade é fixada por cima de toda a interface. Isso cria um aspecto tátil sofisticado sobre as superfícies pretas, reduzindo o visual chapado do background.
*   **Cursor Personalizado:** A ocultação do cursor original do sistema operacional permite a injeção de uma `div` circular verde (`#00FF41`) que segue as coordenadas do mouse. Ao passar sobre links e botões, o círculo se expande suavemente, fornecendo feedback de clique.
*   **Ken Burns Effect:** Animação infinita e gradual no eixo de escala da imagem do Hero (`scale(1)` a `scale(1.15)`), simulando movimento cinematográfico nas rochas de Nero Marquina no topo da página.
*   **Marquee Text (Loop Infinito):** Animação horizontal em 2D na barra inferior da seção Hero. Os elementos de texto de materiais são duplicados na marcação para preencher o contêiner horizontal, permitindo que a animação desloque `-50%` do contêiner continuamente sem que o usuário perceba o reset do ciclo.
*   **Scrollbars Customizadas:** Substituição da barra padrão cinza do navegador por uma versão ultrafina preta integrada à identidade visual da página.

---

## 5. Lógica de Interatividade (Vanilla JavaScript)
Toda a lógica de comportamento interativo do site foi desenvolvida puramente em **Vanilla JavaScript** (sem a dependência de bibliotecas externas como jQuery), garantindo melhor performance e tempo de resposta.

### 5.1. Intersection Observer (Animação de Scroll e Contadores)
Para criar o efeito de surgimento dos blocos à medida que o usuário rola a página, é utilizada a API nativa `IntersectionObserver`:
*   Elementos com a classe `.reveal` são registrados no observador.
*   Ao atingirem um limiar de visibilidade de 10% (`threshold: 0.1`), a classe `.active` é inserida via JavaScript, fazendo o elemento subir de baixo para cima com suavidade via transições CSS.
*   O mesmo observador analisa e ativa os contadores numéricos da seção `#sobre`. A contagem dinâmica é gerada incrementalmente por meio de uma função de atualização recursiva com `setTimeout`, que calcula o valor atual em relação ao valor contido no atributo `data-count` do HTML.

### 5.2. Mecanismo do Carrossel de Materiais
O carrossel de exibição de pedras no catálogo opera de forma dinâmica no trilho flexível `#catalog-track`:
*   **Cálculo de Responsividade:** A função `getVisibleCount()` analisa dinamicamente a largura da janela (`window.innerWidth`) e determina se exibe 3 cards (desktops), 2 cards (tablets) ou 1 card (smartphones).
*   **Movimentação:** Ao clicar nas setas de paginação, o índice atual aumenta ou diminui. O trilho sofre uma translação no eixo X (`translateX`) calculada a partir da largura do card ativo acrescida do espaçamento entre eles (`gap = 24px`).
*   **Tratamento de Limites:** O índice máximo é cravado na quantidade total de cards ativos menos a quantidade visível de cards na tela. Caso atinja os extremos (início ou fim), os botões de setas são desativados visualmente (redução de opacidade) e cliques são bloqueados.
*   **Compatibilidade com Redimensionamento:** O evento `resize` da janela recalcula instantaneamente a translação de transição para evitar que os cards saiam do grid quando o navegador é esticado ou encolhido.

### 5.3. Sistema Dinâmico de Filtragem
Os materiais podem ser filtrados por categorias (Mármores, Granitos, Exóticos e Todos). 
*   Quando uma categoria é selecionada, o script varre todos os cards verificando a propriedade `data-category`.
*   Os cards não correspondentes recebem a classe utilitária `.hidden-card` (`display: none`).
*   Os cards correspondentes são revelados com transições suaves que modificam sua opacidade e translação de baixo para cima.
*   A lista de cards ativos do carrossel (`activeCards`) é atualizada dinamicamente com base nos elementos visíveis, reiniciando o índice geral (`currentIndex = 0`) para a posição zero, permitindo que a navegação do carrossel funcione de forma fluida mesmo com subconjuntos reduzidos de materiais.

### 5.4. Ponte de Dados via Atributos `data-*` e Modal de Detalhes
Para evitar a replicação desnecessária de múltiplos elementos de modal ou chamadas em bases de dados externas, foi construído um sistema de **ponte de dados no DOM**:
1.  Cada card do carrossel armazena os seus dados técnicos em formato de strings inseridas em atributos HTML:
    *   `data-name`: Nome do material.
    *   `data-category-display`: Categoria amigável para exibição.
    *   `data-origin`: País de extração original do bloco.
    *   `data-price`: Estimativa média de custo por metro quadrado.
    *   `data-use`: Recomendações técnicas detalhadas de uso na arquitetura.
    *   `data-desc`: Descrição conceitual do material.
    *   `data-img`: Link de imagem associado.
2.  Quando o botão "Detalhes" de um card é clicado, o JavaScript intercepta o evento, localiza o card pai mais próximo e captura todos esses atributos dinamicamente em um objeto de dados.
3.  Estes valores são inseridos nos elementos HTML internos do modal global único (`#material-modal`).
4.  O modal realiza a animação de abertura (fade-in de fundo com desfoque de vidro e aproximação suave de escala de `95%` para `100%`).
5.  O fechamento é acionado ao clicar no botão "X", fora da área do conteúdo do modal ou no próprio botão interno de orçamento.

### 5.5. Menu Lateral Responsivo
Em telas de dispositivos móveis, o menu clássico de navegação é ocultado, abrindo espaço para o ícone de hambúrguer. Ao ser acionado:
*   Um overlay escuro em tela cheia (`#mobile-menu-overlay`) é exibido com fade-in.
*   Os links de âncoras da página são mostrados em tamanho expandido.
*   Ao clicar em qualquer link de seção ou no botão de fechar, o menu realiza o fade-out e é reocultado do fluxo, evitando obstrução de tela.

---

## 6. Desempenho e Boas Práticas Técnicas
O site foi construído sob severas premissas de otimização de processamento de máquina:
*   **Prevenção de layout thrashing:** Operações críticas no DOM (como leitura e escrita de classes nos cards filtrados) forçam reflows de forma controlada (`card.offsetHeight;`) para manter as transições ativas e livres de quebras visuais.
*   **Hardware Acceleration:** O deslocamento do carrossel no trilho flexível utiliza a propriedade CSS `transform: translateX()`, o que delega a renderização gráfica do movimento diretamente para a GPU do dispositivo, preservando a suavidade das transições sem sobrecarregar a CPU.
*   **Segurança de Eventos:** Uso de `e.stopPropagation()` no clique dos botões internos dos cards para evitar que bolhas de eventos gerem disparos indesejados em outras áreas clicáveis da página.
*   **Uso eficiente do viewport:** Atribuição de desfoque de fundo via CSS (`backdrop-filter`) apenas nos componentes modais e de navegação de alta importância, economizando renderização em máquinas de desempenho básico.
