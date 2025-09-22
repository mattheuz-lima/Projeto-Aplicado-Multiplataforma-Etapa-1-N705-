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
`docs/architecture/architecture.md`

---

## 🛠 Tecnologias Propostas
- **Frontend:** React.js / React Native ou Flutter  
- **Backend:** Node.js + Express  
- **Banco de Dados:** PostgreSQL  
- **Prototipação:** Figma  
- **Documentação de APIs:** Swagger  
- **Controle de versão:** Git + GitHub  

---

## 📅 Cronograma da Etapa 2 (N708)
- **Semanas 1–2:** Desenvolvimento do Backend (APIs, banco de dados).  
- **Semanas 3–4:** Desenvolvimento do Frontend (Web e Mobile).  
- **Semana 5:** Integração, testes e ajustes finais.  

---

## 👥 Equipe e Papéis
- **Matheus Lima - 2323842** – README.md / Coordenação geral  
- **José William - 2326237** – Requisitos (`requirements.md`)  
- **João Rodrigues - 2319025** – Arquitetura (`architecture.md`)  
- **Wanderson Silva - 2323860** – Banco de Dados (`database_model.md`)  
- **Rayane Santos - 2326292** – APIs (`api_specification.md`)  
- **Kamilly Braz - 2323788** – Prototipação (Visily, wireframes)  

---

## 🔗 Links Importantes
- **Protótipo no Figma:** _(inserir link aqui)_  
- **Documentação completa:**  
  - [Requisitos](docs/requirements/requirements.md)  
  - [Arquitetura](docs/architecture/architecture.md)  
  - [Banco de Dados](docs/database/database_model.md)  
  - [APIs](docs/api/api_specification.md)  

