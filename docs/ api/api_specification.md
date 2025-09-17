
# API – Conecta Doações

**Objetivo:**  
Conectar doadores e beneficiários, permitindo o gerenciamento de doações, solicitações e pontos de coleta.

---

## Endpoints

### Autenticação
- **POST /auth/login** → Login (JWT)  
- **POST /auth/logout** → Logout  
- **POST /auth/refresh** → Atualiza token  

### Usuários
- **POST /usuarios** → Criar usuário  
- **GET /usuarios/{id}** → Consultar usuário  
- **PUT /usuarios/{id}** → Atualizar usuário  
- **DELETE /usuarios/{id}** → Remover usuário  

### Doações
- **POST /doacoes** → Registrar doação  
- **GET /doacoes** → Listar doações  
- **GET /doacoes/{id}** → Detalhar doação  
- **PUT /doacoes/{id}** → Atualizar doação  
- **DELETE /doacoes/{id}** → Excluir doação  

### Solicitações (Beneficiários)
- **POST /solicitacoes** → Registrar solicitação  
- **GET /solicitacoes** → Listar solicitações  
- **GET /solicitacoes/{id}** → Detalhar solicitação  
- **PUT /solicitacoes/{id}** → Atualizar solicitação  
- **DELETE /solicitacoes/{id}** → Excluir solicitação  

### Pontos de Coleta
- **POST /pontos** → Cadastrar ponto de coleta  
- **GET /pontos** → Listar pontos  
- **GET /pontos/{id}** → Detalhar ponto  
- **PUT /pontos/{id}** → Atualizar ponto  
- **DELETE /pontos/{id}** → Remover ponto  

---

## Estrutura de Respostas

**Sucesso:**  
```json
{
  "status": "success",
  "data": {...},
  "message": "Sucesso"
}
```

**Erro:**  
```json
{
  "status": "error",
  "message": "Descrição do erro"
}
```

---

## Autenticação
- Todas as requisições protegidas usam **JWT**:  
```
Authorization: Bearer <token>
```

---

## Tecnologias Sugeridas
- **Backend:** Node.js/Express ou Python/FastAPI  
- **Banco de Dados:** PostgreSQL ou MongoDB  
- **Hospedagem:** Heroku, Railway ou AWS  

---

## Contribuição para o ODS 11
A API apoia o **ODS 11 – Cidades e Comunidades Sustentáveis**, conectando doadores e beneficiários, promovendo solidariedade, reaproveitamento de recursos e impacto social positivo.  

