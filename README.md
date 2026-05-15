# 🎬 Projeto CineData — Plataforma Interativa de Catalogação e Análise Cinematográfica

<p align="center">
  <img src="https://img.shields.io/badge/STATUS-CONCLUÍDO-008000?style=for-the-badge" alt="Status do Projeto">
  <img src="https://img.shields.io/badge/VERSÃO-2.0-0A66C2?style=for-the-badge" alt="Versão">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=node.js&logoColor=white" alt="Node.js">
  <img src="https://img.shields.io/badge/Express.js-000000?style=for-the-badge&logo=express&logoColor=white" alt="Express">
  <img src="https://img.shields.io/badge/SQLite-07405E?style=for-the-badge&logo=sqlite&logoColor=white" alt="SQLite">
  <img src="https://img.shields.io/badge/BASH-4EAA25?style=for-the-badge&logo=gnu-bash&logoColor=white" alt="BASH">
  <img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white" alt="HTML5">
  <img src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white" alt="CSS3">
</p>

---

## 📸 Interface do Sistema

<p align="center">
  <img width="48%" alt="Captura 1" src="./captura/captura1.png" />
  <img width="48%" alt="Captura 2" src="./captura/captura2.png" />
</p>

---

## 🏗️ Estrutura e Arquitetura do Sistema

Abaixo apresentamos o diagrama estrutural que detalha o fluxo de dados desde a interface (DOM) até a persistência no banco de dados SQLite.

<p align="center">
  <img src="./captura/diagrama_estrutura.png" alt="Diagrama de Estrutura do Sistema" width="90%" style="border: 2px solid #333; border-radius: 10px;">
</p>

---

## 📖 Sobre o Projeto (Situação-Problema)
O **CineData** foi desenvolvido como solução para o desafio acadêmico de criar um sistema web capaz de coletar, processar e apresentar dados temáticos. O tema escolhido foi **Artes e Filmes**. O projeto simula uma rede social onde o conteúdo é gerado automaticamente via **Web Scraping** de fontes externas ou cadastro manual.

---

## 🛠️ Tecnologias e Requisitos Técnicos

Para cumprir as normas exigidas, o sistema utiliza:

- **Backend:** Node.js com Express.js.
- **Frontend:** HTML5, CSS3 (Design Moderno) e JavaScript Nativo (Manipulação de DOM).
- **Web Scraping:** `Axios` para requisições e `Cheerio` para extração de dados HTML.
- **Validação:** Uso de `Regex` para validar URLs de fontes e dados de formulários.
- **Banco de Dados:** SQLite3 com relacionamentos complexos.
- **Relatórios:** Geração automática de `PDF` com estatísticas de coleta.
- **Automação:** Scripts `BASH` para setup e execução do terminal.

---

## 🗄️ Modelo do Banco de Dados (Relacional)

O banco de dados `cine_data.sqlite` foi estruturado com 3 tabelas principais e relacionamentos via chaves estrangeiras:

### Tabelas Principais:
1.  **`temas`**: Identificação do escopo (ID, Nome, Descrição).
2.  **`sites`**: Fontes de pesquisa cadastradas (ID, Nome, URL, ID_Tema).
3.  **`coletas`**: Dados extraídos (ID, ID_Site, Título, Sinopse, Quantidade de Links/Imagens, Data).

### Consulta SQL (INNER JOIN Obrigatório):
```sql
SELECT 
    temas.nome_tema, 
    sites.nome_site, 
    coletas.titulo_pagina, 
    coletas.data_coleta
FROM coletas
INNER JOIN sites ON coletas.id_site = sites.id_site
INNER JOIN temas ON sites.id_tema = temas.id_tema;
```

---

## 🕷️ Processo de Coleta (Web Scraping)
O robô de coleta segue o fluxo lógico:

1.  **Validação:** O usuário submete uma URL válida (validada rigorosamente por **Regex**).
2.  **Requisição:** O servidor utiliza a biblioteca **Axios** para realizar o download do código-fonte HTML da página alvo.
3.  **Parsing:** O **Cheerio** isola e extrai as tags de interesse (títulos, capas e sinopses).
4.  **Persistência:** Os dados tratados são salvos no banco **SQLite** e renderizados no **Dashboard** em tempo real via manipulação do DOM.

---

## 📊 Gestão do Projeto (Metodologia SCRUM)
O desenvolvimento foi organizado em **2 Sprints intensivas** com papéis bem definidos:

* **Product Owner:** Rafaela Oliveira
* **Scrum Master:** Paolla Veronez
* **Dev Team:** Breno, Felipe, Isabella, Vitor.

### 🛠️ Ferramentas de Gestão:
* **Kanban:** Monitoramento visual do fluxo de trabalho (*To Do, Doing, Done*).
* **5W2H:** Framework utilizado para o planejamento estratégico e definição de requisitos.
* **Sprint Retrospective:** Reunião final para análise de bugs críticos (como dependências circulares) e lições aprendidas.

---

## 🚀 Como Executar
Siga os comandos abaixo no seu terminal **BASH**:

```bash
# 1. Instale as dependências do projeto
npm install

# 2. Inicie o servidor Express
npm start 
# ou
node server.js

# 3. Acesse a interface no navegador
# URL: http://localhost:3000
```

---

## 👥 Equipe

| Nome | Função |
|------|------|
| **Breno Oliveira** | Desenvolvedor |
| **Felipe Heitor** | Desenvolvedor |
| **Isabella Dias** | Desenvolvedora |
| **Paolla Veronez** | Scrum Master |
| **Rafaela Oliveira** | Product Owner |
| **Vitor Canali** | Desenvolvedor |

> **Orientadores:** Prof. Raul Lopes & Prof. Paulo Camargo

---

## 🏁 Conclusão

O **CineData** transcende um exercício simples, unificando conceitos de extração de dados reais (Web Scraping) com persistência relacional (SQLite) e arquitetura de rede social. 

[cite_start]A conclusão deste projeto atesta o conhecimento de ponta a ponta da equipe no ecosssistema Node.js, uso do Express, formatação de relatórios automáticos, e governança e gerenciamento ágil de tarefas[cite: 184, 186, 205].

---
<p align="center">
  <i>Projeto desenvolvido para fins educacionais no curso Técnico em Desenvolvimento de Sistemas — SENAI “A. Jacob Lafer”.</i>
</p>
