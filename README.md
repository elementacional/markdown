# 📄 Academic DOCX to Markdown & GitHub Publisher

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![JavaScript](https://img.shields.io/badge/JavaScript-ES6%2B-yellow.svg)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3.x-38BDF8.svg)](https://tailwindcss.com/)
[![GitHub API](https://img.shields.io/badge/GitHub_API-v3-181717.svg)](https://docs.github.com/en/rest)

Um aplicativo web *client-side* completo, elegante e responsivo projetado para converter documentos **Microsoft Word (.docx)** em **Markdown limpo**, renderizando equações matemáticas em **LaTeX/KaTeX**, preservando blocos de destaque/caixas de texto e automatizando a publicação e commit diretamente em repositórios do **GitHub via REST API**.

---

## 🌟 Funcionalidades Principais

- 📦 **Processamento 100% Client-Side**: Nenhuma informação do seu documento ou token do GitHub é enviada para servidores de terceiros. Tudo é processado localmente no seu navegador.
- 📐 **Preservação de Equações (LaTeX/KaTeX)**: Converte notações de equações e fórmulas do documento em sintaxe KaTeX/LaTeX nativa.
- 💬 **Extração de Caixas de Texto**: Identifica blocos de destaque e caixas de texto do Word e os transforma em *blockquotes* limpos em Markdown (`>`).
- 🖼️ **Extração Automática de Imagens**: Extrai mídias incorporadas no `.docx` via JSZip e prepara o upload automático para a pasta de imagens no repositório.
- 📊 **Estatísticas em Tempo Real**: Métricas instantâneas de quantidade de palavras, número de caracteres e **taxa de extração fiel `( XX%)`**.
- 🚀 **Integração Nativa com GitHub API**:
  - Autenticação por **Personal Access Token (PAT)** com persistência local segura.
  - Seleção dinâmica de repositórios vinculados à conta.
  - Suporte a criação/chaveamento automático de **branches** customizadas.
  - Upload automatizado do Markdown e assets de imagem em um único fluxo.
- 🎨 **UI Moderna e Minimalista**: Layout inspirado nos temas *Navy Dark*, responsivo e com controles rápidos de cópia e download `.md`.

---

## 🖥️ Layout e Interface (4 Quadrantes)

O aplicativo está estruturado em uma interface fluida com quatro áreas principais de controle:

```
+------------------------------------------+------------------------------------------+
|  1. DROPZONE & ARQUIVO .DOCX             |  3. PRÉ-VISUALIZAÇÃO RENDERIZADA         |
|     - Arrastar / Soltar .docx            |     - Renderização HTML/CSS              |
|     - Pré-processamento XML              |     - KaTeX Math em Tempo Real           |
+------------------------------------------+------------------------------------------+
|  2. CÓDIGO MARKDOWN & ESTATÍSTICAS       |  4. PUBLICAR NO GITHUB (API)             |
|     - Editor / Área de Código MD         |     - Seleção de Repositório & Branch    |
|     - Estatísticas (Palavras, Caracteres)|     - Caminho do Arquivo & Commit Msg    |
|     - Extração Fiel ( XX%)               |     - Botão de Commit & Upload           |
+------------------------------------------+------------------------------------------+
```

---

## 🚀 Como Usar

### 1. Executando Localmente (Sem Instalação)

Como a aplicação consiste em um **único arquivo self-contained (`index.html`)**, basta:

1. Baixar ou clonar o repositório:
   ```bash
   git clone https://github.com/seu-usuario/docx-to-markdown-publisher.git
   ```
2. Dar dois cliques no arquivo `index.html` para abri-lo diretamente em qualquer navegador moderno (Chrome, Firefox, Edge, Safari).

---

### 2. Fluxo de Trabalho Passo a Passo

#### **Passo A: Autenticar no GitHub (Opcional)**
1. No cabeçalho superior ou no painel de publicação, insira seu **Personal Access Token (PAT)** do GitHub com permissão de escrita em repositórios (`repo`).
2. Clique em **Autenticar**. Se o token for válido, seus repositórios serão carregados no menu suspenso.

#### **Passo B: Converter o Arquivo .docx**
1. Arraste e solte o arquivo `.docx` na área pontilhada (**Dropzone**) ou clique para selecionar.
2. O sistema irá pré-processar a estrutura `word/document.xml`, extraindo texto, imagens e caixas de texto.
3. O código Markdown gerado e a prévia renderizada aparecerão simultaneamente nos painéis correspondentes.
4. Confira as estatísticas de contagem no rodapé do editor: `Palavras`, `Caracteres` e a porcentagem de `Extração Fiel ( XX%)`.

#### **Passo C: Exportar ou Publicar**
- **Download/Cópia Manual**: Utilize os botões **Copiar** ou **Baixar .md** para salvar o arquivo no seu computador.
- **Publicação Direta no GitHub**:
  1. Escolha o **Repositório** de destino.
  2. Especifique a **Branch** (ex: `main` ou `docs`). Se a branch não existir, ela será criada automaticamente.
  3. Defina o **Caminho do Arquivo** (ex: `docs/artigo.md`). As imagens extraídas serão enviadas para uma subpasta `imagens/` no mesmo diretório.
  4. Insira a **Mensagem de Commit** e clique em **Publicar Commit no GitHub**.

---

## 🔑 Como Gerar um Personal Access Token (PAT) no GitHub

Para utilizar a publicação direta no GitHub:

1. Acesse **Configurações do GitHub** > **Developer Settings** > **Personal Access Tokens** > **Tokens (classic)** (ou [clique aqui](https://github.com/settings/tokens)).
2. Clique em **Generate new token (classic)**.
3. Defina um nome (ex: `DOCX Publisher App`).
4. Selecione o escopo: **`repo`** (Acesso total aos repositórios privados e públicos).
5. Clique em **Generate token** e copie o código gerado (`ghp_...`).
6. Cole no campo **GitHub PAT Token** da aplicação.

---

## 🛠️ Tecnologias e Bibliotecas Utilizadas

| Biblioteca / Recurso | Versão / CDN | Finalidade |
| :--- | :--- | :--- |
| **Tailwind CSS** | `3.x CDN` | Estilização responsiva e tema Dark Slate/Navy |
| **Mammoth.js** | `1.6.0` | Conversão básica de estrutura Word (.docx) para HTML |
| **JSZip** | `3.10.1` | Descompactação do arquivo XML do `.docx` e extração de mídias |
| **KaTeX** | `0.16.8` | Renderização ultrarrápida de fórmulas e equações matemáticas |
| **GitHub REST API v3** | `Native Fetch` | Gerenciamento de commits, criação de branches e upload de imagens |

---

## 📜 Licença

Este projeto está licenciado sob a licença **MIT** - consulte o arquivo [LICENSE](LICENSE) para obter mais detalhes.

---
*Desenvolvido para simplificar o fluxo de publicação acadêmica e documentação técnica no GitHub.*