# VR Stones — Landing Page Institucional

Este repositório contém a página de destino (landing page) institucional e interativa da **VR Stones**, uma marmoraria e marcenaria de alto padrão focada no segmento de luxo residencial e comercial. 

O site serve como o principal canal de captação de leads qualificados (arquitetos, designers de interiores e construtoras), destacando a precisão técnica das operações CNC, o acabamento artesanal e um catálogo de pedras nobres.

---

## 🚀 Como Executar o Projeto Localmente

O projeto foi projetado como uma **Single-Page Application (SPA) Estática**, o que significa que todos os recursos fundamentais estão contidos em um único arquivo de entrada principal. Não é necessário compilar ou instalar dependências pesadas para visualizar a interface.

### Opção 1: Abertura Direta
Você pode visualizar o site imediatamente dando um duplo clique no arquivo [index.html](file:///c:/Users/joaop/antigravity%20projects/VR%20STONES%20LANDPAGE/index.html) no seu navegador de preferência.

### Opção 2: Servidor Local (Recomendado para melhor carregamento de fontes e recursos externos)
Para simular um ambiente de produção real, execute um servidor HTTP simples no diretório raiz do projeto:

*   **Usando Python (3.x):**
    ```bash
    python -m http.server 8000
    ```
    Em seguida, acesse `http://localhost:8000` em seu navegador.
*   **Usando VS Code:**
    Utilize a extensão **Live Server** para iniciar um servidor de desenvolvimento com recarga automática ao salvar alterações.

---

## 📁 Estrutura de Arquivos do Projeto

A organização dos arquivos é enxuta e centralizada para garantir desempenho e portabilidade:

*   [index.html](file:///c:/Users/joaop/antigravity%20projects/VR%20STONES%20LANDPAGE/index.html): Arquivo principal do site. Contém toda a estrutura HTML5 semântica, as estilizações (Tailwind CSS estendido via script inline + CSS Customizado para efeitos especiais) e a interatividade Vanilla JavaScript.
*   [design.md](file:///c:/Users/joaop/antigravity%20projects/VR%20STONES%20LANDPAGE/design.md): Especificação completa do sistema de design (*Design System*), incluindo tokens de cores, regras de tipografia, espaçamentos, elevação e comportamento de componentes.
*   [RELATORIO.md](file:///c:/Users/joaop/antigravity%20projects/VR%20STONES%20LANDPAGE/RELATORIO.md): Relatório técnico abrangente documentando as decisões arquiteturais, o funcionamento detalhado dos algoritmos em JavaScript e as boas práticas de desempenho gráfico empregadas.

---

## 🎯 Onde Encontrar Informações Específicas

Para evitar a redundância de documentação e facilitar a navegação dos desenvolvedores e designers, os detalhes específicos de implementação foram divididos estrategicamente entre os arquivos complementares:

### 🎨 Identidade Visual e Estilo (Design System)
Se você precisa entender a lógica das cores, os tamanhos de fonte recomendados, os arredondamentos das bordas, ou o conceito da estética *Cyber-Stone Architectural*, consulte o documento [design.md](file:///c:/Users/joaop/antigravity%20projects/VR%20STONES%20LANDPAGE/design.md).
> **Exemplos de tópicos cobertos lá:**
> *   Paleta de cores (fundo escuro obsidian com realce verde neon `#00FF41`).
> *   Emparelhamento tipográfico (*Space Grotesk* para títulos arquitetônicos e *Outfit* para leitura).
> *   Filosofia de componentes (botões arredondados no estilo *pill* versus contêineres de imagem com bordas retas).

### 🛠️ Lógica de Interatividade, Algoritmos e Arquitetura
Se você deseja compreender como as interações da página foram construídas no nível de código JavaScript ou as decisões de performance estrutural, consulte o documento [RELATORIO.md](file:///c:/Users/joaop/antigravity%20projects/VR%20STONES%20LANDPAGE/RELATORIO.md).
> **Exemplos de tópicos cobertos lá:**
> *   **Intersection Observer:** A lógica usada para disparar as animações de scroll (`.reveal`) e atualizar gradualmente os contadores dinâmicos de estatísticas da seção "Sobre".
> *   **Carrossel & Filtros:** O cálculo responsivo de translação e a filtragem assíncrona por categoria dos cards de materiais do catálogo.
> *   **Modal de Detalhes:** O sistema de transporte de dados dinâmico via atributos `data-*` para popular um único modal de exibição estrutural.
> *   **Otimizações de Performance:** Uso de aceleração por hardware (GPU) nas transições e prevenção de *layout thrashing*.

---

## 🛠️ Tecnologias Utilizadas

*   **HTML5:** Estrutura semântica focada em SEO e acessibilidade.
*   **Tailwind CSS (via CDN):** Desenvolvimento de layout ágil com estilizações utilitárias e configuração estendida em tempo de execução.
*   **CSS3 Customizado:** Implementação de efeitos como *Grain Overlay* (textura tátil de grão sobre o layout), animação de *Ken Burns* nas imagens e o cursor customizado que interage com os botões.
*   **Vanilla JavaScript (ES6+):** Programação de toda a interatividade de forma nativa, garantindo carregamento rápido e eliminando dependências de frameworks externos pesados.
*   **Google Fonts & Material Symbols:** Carregamento de famílias tipográficas personalizadas e ícones vetoriais responsivos.

---

Este projeto demonstra como unir estética minimalista, interações fluidas e desenvolvimento puramente nativo para atingir alta performance e uma experiência marcante para o usuário final.
