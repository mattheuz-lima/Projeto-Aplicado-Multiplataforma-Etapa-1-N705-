# API Specification - Sistema Conecta Doações

## 📌 Visão Geral

A API do Sistema Conecta Doações é uma API REST que facilita o gerenciamento de doações, trocas e solicitações comunitárias. Desenvolvida para suportar aplicações web e móveis, a API conecta doadores, receptores e pontos de apoio, promovendo a solidariedade e o reaproveitamento de recursos na Região Metropolitana de Fortaleza.

**Base URL:** `https://api.conectadoacoes.com/v1`

---

## 🔐 Autenticação e Autorização

### Método de Autenticação
A API utiliza **JWT (JSON Web Token)** para autenticação. Todas as rotas protegidas requerem o token no header:

```
Authorization: Bearer <jwt_token>
```

### Tipos de Usuário
- **Doador:** Pode cadastrar itens para doação/troca
- **Receptor:** Pode buscar e reservar itens
- **Administrador:** Acesso completo ao sistema
- **Ponto de Apoio:** Gerencia itens intermediados

---

## 📋 Endpoints Detalhados

### 1. **Autenticação**

#### POST /auth/login
Realiza login do usuário no sistema.

**Parâmetros de Requisição:**
```json
{
  "email": "usuario@email.com",
  "senha": "senha123"
}
```

**Resposta de Sucesso (200):**
```json
{
  "status": "success",
  "data": {
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "refresh_token": "refresh_token_aqui",
    "expires_in": 3600,
    "user": {
      "id": 1,
      "nome": "João Silva",
      "email": "usuario@email.com",
      "tipo_usuario": "doador"
    }
  },
  "message": "Login realizado com sucesso"
}
```

**Resposta de Erro (401):**
```json
{
  "status": "error",
  "message": "Credenciais inválidas",
  "code": "INVALID_CREDENTIALS"
}
```

#### POST /auth/register
Cadastra novo usuário no sistema.

**Parâmetros de Requisição:**
```json
{
  "nome": "Maria Santos",
  "email": "maria@email.com",
  "telefone": "(85) 99999-9999",
  "senha": "senha123",
  "endereco": "Rua das Flores, 123",
  "bairro": "Aldeota",
  "cidade": "Fortaleza",
  "tipo_usuario": "ambos"
}
```

**Resposta de Sucesso (201):**
```json
{
  "status": "success",
  "data": {
    "user_id": 2,
    "message": "Usuário cadastrado com sucesso"
  }
}
```

#### POST /auth/refresh
Renova o token de acesso.

**Parâmetros de Requisição:**
```json
{
  "refresh_token": "refresh_token_aqui"
}
```

#### POST /auth/logout
Invalida o token atual.

**Headers:** `Authorization: Bearer <token>`

---

### 2. **Usuários**

#### GET /usuarios/{id}
Consulta dados de um usuário específico.

**Headers:** `Authorization: Bearer <token>`

**Resposta de Sucesso (200):**
```json
{
  "status": "success",
  "data": {
    "id": 1,
    "nome": "João Silva",
    "email": "joao@email.com",
    "telefone": "(85) 98765-4321",
    "endereco": "Rua A, 100",
    "bairro": "Messejana",
    "cidade": "Fortaleza",
    "tipo_usuario": "doador",
    "ativo": true,
    "data_cadastro": "2024-01-15T10:30:00Z"
  }
}
```

#### PUT /usuarios/{id}
Atualiza dados do usuário.

**Headers:** `Authorization: Bearer <token>`

**Parâmetros de Requisição:**
```json
{
  "nome": "João Silva Santos",
  "telefone": "(85) 91234-5678",
  "endereco": "Rua Nova, 200"
}
```

**Resposta de Sucesso (200):**
```json
{
  "status": "success",
  "message": "Usuário atualizado com sucesso"
}
```

---

### 3. **Itens**

#### POST /itens
Cadastra novo item para doação/troca.

**Headers:** `Authorization: Bearer <token>`

**Parâmetros de Requisição:**
```json
{
  "titulo": "Sofá em Bom Estado",
  "descricao": "Sofá de 3 lugares, cor marrom, em ótimo estado de conservação",
  "id_categoria": 2,
  "tipo": "doacao",
  "imagem_url": "https://exemplo.com/imagem.jpg",
  "id_ponto_apoio": 1
}
```

**Resposta de Sucesso (201):**
```json
{
  "status": "success",
  "data": {
    "id_item": 15,
    "titulo": "Sofá em Bom Estado",
    "status": "disponivel",
    "data_cadastro": "2024-09-25T14:30:00Z"
  },
  "message": "Item cadastrado com sucesso"
}
```

#### GET /itens
Lista itens disponíveis com filtros opcionais.

**Parâmetros de Query (opcionais):**
- `categoria`: ID da categoria
- `tipo`: "doacao" ou "troca"
- `status`: "disponivel", "reservado", "doado"
- `cidade`: nome da cidade
- `bairro`: nome do bairro
- `page`: página (padrão: 1)
- `limit`: itens por página (padrão: 20)

**Exemplo:** `GET /itens?categoria=1&tipo=doacao&page=1&limit=10`

**Resposta de Sucesso (200):**
```json
{
  "status": "success",
  "data": {
    "itens": [
      {
        "id_item": 1,
        "titulo": "Roupas Infantis",
        "descricao": "Lote de roupas infantis tamanho 2-4 anos",
        "categoria": "Roupas",
        "tipo": "doacao",
        "imagem_url": "https://exemplo.com/roupa.jpg",
        "status": "disponivel",
        "doador": {
          "nome": "Ana Costa",
          "bairro": "Aldeota"
        },
        "data_cadastro": "2024-09-20T08:00:00Z"
      }
    ],
    "pagination": {
      "current_page": 1,
      "total_pages": 5,
      "total_items": 48,
      "items_per_page": 10
    }
  }
}
```

#### GET /itens/{id}
Consulta detalhes de um item específico.

**Resposta de Sucesso (200):**
```json
{
  "status": "success",
  "data": {
    "id_item": 1,
    "titulo": "Roupas Infantis",
    "descricao": "Lote completo de roupas infantis, tamanhos variados de 2 a 4 anos. Inclui camisetas, calças, vestidos e casacos. Todas em excelente estado.",
    "categoria": {
      "id": 1,
      "nome": "Roupas"
    },
    "tipo": "doacao",
    "imagem_url": "https://exemplo.com/roupa.jpg",
    "status": "disponivel",
    "doador": {
      "id": 5,
      "nome": "Ana Costa",
      "telefone": "(85) 99888-7777",
      "endereco": "Rua das Palmeiras, 45",
      "bairro": "Aldeota"
    },
    "ponto_apoio": {
      "id": 2,
      "nome": "Centro Comunitário Aldeota",
      "endereco": "Av. Santos Dumont, 1000",
      "telefone": "(85) 3333-4444"
    },
    "data_cadastro": "2024-09-20T08:00:00Z"
  }
}
```

#### PUT /itens/{id}
Atualiza informações de um item (apenas o doador).

**Headers:** `Authorization: Bearer <token>`

**Parâmetros de Requisição:**
```json
{
  "titulo": "Roupas Infantis - Lote Completo",
  "descricao": "Descrição atualizada do item",
  "status": "reservado"
}
```

#### DELETE /itens/{id}
Remove um item (apenas o doador).

**Headers:** `Authorization: Bearer <token>`

**Resposta de Sucesso (200):**
```json
{
  "status": "success",
  "message": "Item excluído com sucesso"
}
```

---

### 4. **Transações**

#### POST /transacoes
Cria nova transação (reserva/solicitação).

**Headers:** `Authorization: Bearer <token>`

**Parâmetros de Requisição:**
```json
{
  "id_item": 15,
  "tipo": "doacao",
  "mensagem": "Gostaria de receber este item para minha família"
}
```

**Resposta de Sucesso (201):**
```json
{
  "status": "success",
  "data": {
    "id_transacao": 8,
    "status": "pendente",
    "data_solicitacao": "2024-09-25T15:00:00Z"
  },
  "message": "Solicitação enviada com sucesso"
}
```

#### GET /transacoes
Lista transações do usuário logado.

**Headers:** `Authorization: Bearer <token>`

**Parâmetros de Query (opcionais):**
- `status`: "pendente", "confirmada", "concluida"
- `tipo`: "doacao" ou "troca"

**Resposta de Sucesso (200):**
```json
{
  "status": "success",
  "data": [
    {
      "id_transacao": 1,
      "item": {
        "titulo": "Sofá em Bom Estado",
        "imagem_url": "https://exemplo.com/sofa.jpg"
      },
      "doador": {
        "nome": "Maria Santos"
      },
      "recebedor": {
        "nome": "João Silva"
      },
      "tipo": "doacao",
      "status": "confirmada",
      "data_solicitacao": "2024-09-20T10:00:00Z"
    }
  ]
}
```

#### PUT /transacoes/{id}/status
Atualiza status da transação.

**Headers:** `Authorization: Bearer <token>`

**Parâmetros de Requisição:**
```json
{
  "status": "confirmada",
  "observacoes": "Item pronto para retirada"
}
```

---

### 5. **Categorias**

#### GET /categorias
Lista todas as categorias disponíveis.

**Resposta de Sucesso (200):**
```json
{
  "status": "success",
  "data": [
    {
      "id_categoria": 1,
      "nome": "Roupas",
      "descricao": "Roupas e acessórios",
      "ativo": true
    },
    {
      "id_categoria": 2,
      "nome": "Móveis",
      "descricao": "Móveis e decoração",
      "ativo": true
    },
    {
      "id_categoria": 3,
      "nome": "Eletrônicos",
      "descricao": "Equipamentos eletrônicos",
      "ativo": true
    }
  ]
}
```

---

### 6. **Pontos de Apoio**

#### GET /pontos-apoio
Lista pontos de apoio disponíveis.

**Parâmetros de Query (opcionais):**
- `cidade`: filtro por cidade
- `ativo`: true/false

**Resposta de Sucesso (200):**
```json
{
  "status": "success",
  "data": [
    {
      "id_ponto_apoio": 1,
      "nome": "Centro Comunitário Messejana",
      "endereco": "Rua Principal, 500 - Messejana",
      "telefone": "(85) 3333-1111",
      "horario_funcionamento": "Segunda a Sexta: 8h às 17h",
      "ativo": true
    }
  ]
}
```

---

### 7. **Mensagens**

#### POST /mensagens
Envia mensagem entre usuários.

**Headers:** `Authorization: Bearer <token>`

**Parâmetros de Requisição:**
```json
{
  "id_destinatario": 5,
  "conteudo": "Olá! Gostaria de saber mais sobre o sofá que você está doando."
}
```

#### GET /mensagens
Lista mensagens do usuário.

**Headers:** `Authorization: Bearer <token>`

**Parâmetros de Query (opcionais):**
- `id_conversa`: ID do usuário da conversa
- `limit`: quantidade de mensagens (padrão: 50)

---

### 8. **Avaliações**

#### POST /avaliacoes
Cria avaliação de uma transação.

**Headers:** `Authorization: Bearer <token>`

**Parâmetros de Requisição:**
```json
{
  "id_transacao": 8,
  "nota": 5,
  "comentario": "Excelente doador! Item exatamente como descrito."
}
```

**Resposta de Sucesso (201):**
```json
{
  "status": "success",
  "message": "Avaliação registrada com sucesso"
}
```

---

## 📊 Códigos de Status HTTP

| Código | Significado | Uso |
|--------|-------------|-----|
| 200 | OK | Requisição bem-sucedida |
| 201 | Created | Recurso criado com sucesso |
| 400 | Bad Request | Parâmetros inválidos |
| 401 | Unauthorized | Token inválido ou ausente |
| 403 | Forbidden | Sem permissão para o recurso |
| 404 | Not Found | Recurso não encontrado |
| 409 | Conflict | Conflito (ex: email já existe) |
| 422 | Unprocessable Entity | Dados inválidos |
| 500 | Internal Server Error | Erro interno do servidor |

---

## 🔒 Segurança

### Headers de Segurança
```
Content-Security-Policy: default-src 'self'
X-Content-Type-Options: nosniff
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block
```

### Rate Limiting
- **Autenticação:** 5 tentativas por minuto
- **APIs gerais:** 100 requisições por minuto por usuário
- **Upload de imagens:** 10 por minuto

### Validações
- Todos os inputs são sanitizados
- Senhas devem ter no mínimo 8 caracteres
- Email deve ser único no sistema
- Imagens limitadas a 5MB

---

## 🧪 Exemplos de Uso

### Fluxo Completo de Doação

1. **Login do Doador:**
```bash
curl -X POST https://api.conectadoacoes.com/v1/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email": "doador@email.com", "senha": "senha123"}'
```

2. **Cadastro de Item:**
```bash
curl -X POST https://api.conectadoacoes.com/v1/itens \
  -H "Authorization: Bearer <token>" \
  -H "Content-Type: application/json" \
  -d '{"titulo": "Mesa de Jantar", "descricao": "Mesa para 6 pessoas", "id_categoria": 2, "tipo": "doacao"}'
```

3. **Receptor Busca Itens:**
```bash
curl -X GET "https://api.conectadoacoes.com/v1/itens?categoria=2&tipo=doacao"
```

4. **Receptor Solicita Item:**
```bash
curl -X POST https://api.conectadoacoes.com/v1/transacoes \
  -H "Authorization: Bearer <token_receptor>" \
  -H "Content-Type: application/json" \
  -d '{"id_item": 15, "tipo": "doacao", "mensagem": "Preciso para minha casa nova"}'
```

---

## 🌍 Contribuição para o ODS 11

Esta API contribui diretamente para o **ODS 11 - Cidades e Comunidades Sustentáveis** através de:

- **Redução de Desperdício:** Facilita o reaproveitamento de itens
- **Inclusão Social:** Conecta pessoas em situação de vulnerabilidade com recursos
- **Fortalecimento Comunitário:** Promove solidariedade local
- **Economia Circular:** Incentiva práticas sustentáveis de consumo
- **Tecnologia Social:** Utiliza tecnologia para impacto social positivo

---

## 📚 Tecnologias e Padrões

- **Arquitetura:** RESTful API
- **Autenticação:** JWT (JSON Web Token)
- **Formato de Dados:** JSON
- **Protocolo:** HTTPS
- **Documentação:** OpenAPI 3.0 (Swagger)
- **Versionamento:** Semantic Versioning (v1, v2, etc.)

---

## 📖 Documentação Adicional

- **Swagger UI:** `https://api.conectadoacoes.com/docs`
- **Postman Collection:** Disponível no repositório
- **SDK:** Bibliotecas para JavaScript, Python e PHP em desenvolvimento
