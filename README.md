# 📦 Conecta Doações

## 📌 Descrição / Problema e Justificativa
Na região metropolitana de Fortaleza, muitas famílias enfrentam dificuldades para acessar bens essenciais como roupas, móveis, eletrônicos e alimentos.  
Ao mesmo tempo, diversas pessoas possuem itens sem uso armazenados em casa.  

Essa disparidade é agravada pela falta de uma plataforma eficiente que conecte **diretamente doadores e recebedores**, dificultando a redistribuição de recursos dentro da própria comunidade.  

O projeto **Conecta Doações** surge para **facilitar o reaproveitamento de itens e promover a solidariedade**, permitindo que usuários possam doar, trocar ou solicitar produtos de forma simples, organizada e segura.

---

## 🎯 Objetivos do Sistema
- Facilitar o processo de doações e trocas comunitárias.  
- Reduzir o desperdício de itens em bom estado.  
- Aumentar a acessibilidade a bens essenciais para famílias em situação de vulnerabilidade.  
- Promover a solidariedade e o engajamento comunitário.  
- Contribuir com os Objetivos de Desenvolvimento Sustentável (ODS 11 – Cidades e Comunidades Sustentáveis).  

---

## 🗂 Escopo do Projeto
A plataforma contará com:  
- Cadastro de usuários.  
- Cadastro e categorização de itens disponíveis para doação ou troca.  
- Busca e solicitação de itens por parte dos usuários.  
- Inclusão de **pontos de apoio parceiros** para armazenamento e retirada de bens.  
- Funcionalidades acessíveis tanto em **web** quanto em **dispositivos móveis**.  

---

## 🏗 Visão Geral da Arquitetura
O sistema será multiplataforma, composto por:  

- **Frontend (Web e Mobile):** Interface intuitiva para usuários (React.js e React Native ou Flutter).  
- **Backend (API):** Gerenciamento da lógica de negócio e comunicação com o banco de dados (Node.js + Express).  
- **Banco de Dados:** Armazenamento estruturado de usuários, itens, categorias e pontos de apoio (PostgreSQL).  
- **APIs REST:** Serviços para cadastro, consulta e gerenciamento de dados.  

📌 O **diagrama detalhado** da arquitetura estará disponível em:  
- [docs/architecture/architecture.md](docs/architecture/architecture.md)  

---

## 🛠 Tecnologias Propostas
- **Frontend:** React.js / React Native ou Flutter  
- **Backend:** Node.js + Express  
- **Banco de Dados:** PostgreSQL  
- **Prototipação:** Visily 
- **Documentação de APIs:** Swagger  
- **Controle de versão:** Git + GitHub  

---

## 📅 Cronograma da Etapa 2 (N708)

- **Semanas 1–2**
  - Configuração do repositório de código
  - Criação do ambiente de desenvolvimento
  - Definição da estrutura do backend (Node.js + Express)
  - Configuração inicial do banco de dados PostgreSQL

- **Semanas 3–4**
  - Desenvolvimento dos endpoints principais da API:
    - Cadastro e autenticação de usuários
    - Cadastro e listagem de itens
    - Cadastro e gerenciamento de pontos de apoio
  - Documentação da API no Swagger

- **Semanas 5–6**
  - Desenvolvimento do frontend Web (React.js)
  - Implementação das telas de:
    - Login e cadastro
    - Página inicial com listagem de itens
    - Cadastro de itens para doação/troca
  - Integração com os endpoints já criados

- **Semanas 7**
  - Desenvolvimento do frontend Mobile (React Native / Flutter)
  - Implementação das telas principais equivalentes ao Web
  - Integração com APIs
  - Ajustes de usabilidade e responsividade

- **Semana 8**
  - Integração completa (Frontend + Backend + Banco)
  - Testes funcionais e validação do sistema
  - Correções de bugs
  - Preparação e entrega final do projeto
 

---

## 👥 Equipe e Papéis
- **Matheus Lima - 2323842** – README.md / Coordenação geral  
- **José William - 2326237** – Requisitos (`requirements.md`)  
- **João Rodrigues - 2319025** – Arquitetura (`architecture.md`)  
- **Wanderson Silva - 2323860** – Banco de Dados (`database_model.md`)  
- **Rayane Santos - 2326292** – APIs (`api_specification.md`)  
- **Kamilly Braz - 2323788** – Prototipação (`prototypes`)  

---

## 🔗 Links Importantes
- **Protótipo no Visily:** 

- Link do protótipo MOBILE: https://app.visily.ai/projects/d6fc3786-4d72-42c3-a96c-89e1877c4441/boards/1881133

- Link do protótipo WEB - https://app.visily.ai/projects/de093b13-424f-4045-a815-8eb03eef0480/boards/2213632)_ 

- **Documentação completa:**
  - [Requisitos](docs/requirements/requirements.md)
  - [Acesse a pasta de protótipos](./prototypes)
  - [Arquitetura](docs/architecture/architecture.md)  
  - [Banco de Dados](docs/database/database_model.md)  
  - [APIs](docs/api/api_specification.md)  

