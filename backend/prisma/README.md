# LookOs Backend

Backend do sistema LookOs, um ERP desenvolvido para gerenciamento de salões de beleza.

O projeto tem como objetivo centralizar processos como cadastro de clientes, funcionários, serviços, produtos, agendamentos, controle de estoque e gerenciamento administrativo.

Este repositório contém somente a API do sistema. O frontend será executado separadamente.

---

## Tecnologias utilizadas

* Node.js
* TypeScript
* Express
* Prisma ORM
* PostgreSQL
* Docker
* JWT para autenticação
* Bcrypt para criptografia de senhas

---

# Pré-requisitos

Antes de iniciar o projeto, é necessário ter instalado na máquina:

* Node.js (versão 20 ou superior)
* npm
* Docker
* Docker Compose
* Git

Para verificar as versões instaladas:

```bash
node -v

npm -v

docker -v
```

---

# Clonando o projeto

Primeiro, clone o repositório:

```bash
git clone URL_DO_REPOSITORIO
```

Depois entre na pasta do backend:

```bash
cd backend
```

---

# Instalação das dependências

Dentro da pasta backend execute:

```bash
npm install
```

Esse comando irá instalar todas as dependências necessárias do projeto.

---

# Configuração das variáveis de ambiente

O projeto utiliza variáveis de ambiente para controlar configurações como banco de dados e porta da aplicação.

Crie um arquivo chamado:

```
.env
```

Na raiz do backend.

Adicione:

```env
DATABASE_URL="postgresql://postgres:postgres@localhost:5432/lookos"

PORT=3333

JWT_SECRET="secret_key"
```

---

# Subindo o banco de dados com Docker

O banco PostgreSQL é executado através do Docker.

Para iniciar o container:

```bash
docker compose up -d
```

Para verificar se o container está rodando:

```bash
docker ps
```

Caso precise parar os containers:

```bash
docker compose down
```

---

# Configuração do Prisma

Depois que o banco estiver funcionando, execute:

```bash
npx prisma generate
```

Esse comando cria o Prisma Client utilizado pela aplicação.

Para aplicar as tabelas no banco:

```bash
npx prisma migrate dev
```

---

# Executando o projeto

Para iniciar o servidor em ambiente de desenvolvimento:

```bash
npm run dev
```

Caso esteja tudo correto, a API estará disponível em:

```
http://localhost:3333
```

---

# Estrutura do projeto

```
backend
│
├── prisma
│   └── schema.prisma
│
├── src
│   │
│   ├── controllers
│   │   # Recebem as requisições HTTP
│   │
│   ├── routes
│   │   # Definição das rotas da API
│   │
│   ├── services
│   │   # Regras de negócio da aplicação
│   │
│   ├── middlewares
│   │   # Autenticação e validações
│   │
│   ├── app.ts
│   │   # Configuração do Express
│   │
│   └── server.ts
│       # Inicialização do servidor
│
├── .env
├── docker-compose.yml
├── package.json
└── tsconfig.json
```

---

# Comandos úteis

### Rodar o projeto

```bash
npm run dev
```

### Gerar Prisma Client

```bash
npx prisma generate
```

### Criar uma nova migration

```bash
npx prisma migrate dev --name nome_da_migration
```

### Abrir Prisma Studio

Interface visual para consultar o banco:

```bash
npx prisma studio
```

---

# Banco de Dados

O projeto utiliza PostgreSQL.

Configuração padrão:

```
Banco: lookos
Usuário: postgres
Senha: postgres
Porta: 5432
```

---

# Rotas principais

A API seguirá o padrão REST.

Exemplo:

## Usuários

Criar usuário:

```
POST /users
```

Listar usuários:

```
GET /users
```

Buscar usuário por ID:

```
GET /users/:id
```

Atualizar usuário:

```
PUT /users/:id
```

Remover usuário:

```
DELETE /users/:id
```

---

# Autenticação

O sistema utiliza autenticação através de JWT.

Após o login, o usuário recebe um token que deve ser enviado nas requisições protegidas.

Formato:

```
Authorization: Bearer TOKEN
```

---

# Desenvolvimento em equipe

Antes de iniciar uma alteração:

Atualize o projeto:

```bash
git pull origin main
```

Crie uma nova branch:

```bash
git checkout -b nome-da-feature
```

Depois das alterações:

```bash
git add .

git commit -m "descrição da alteração"

git push origin nome-da-feature
```

---

# Problemas comuns

## Erro de conexão com banco

Verifique se o Docker está rodando:

```bash
docker ps
```

Caso o banco não esteja ativo:

```bash
docker compose up -d
```

---

## Prisma não encontrado

Execute:

```bash
npx prisma generate
```

---

## Porta ocupada

Caso a porta 3333 esteja sendo usada, altere no arquivo:

```
.env
```

Exemplo:

```env
PORT=3334
```

---

# Objetivo do projeto

O LookOs busca facilitar a gestão de pequenos salões de beleza, substituindo controles manuais como planilhas, cadernos e mensagens, trazendo organização para:

* Agendamentos
* Clientes
* Funcionários
* Serviços
* Produtos
* Estoque
* Financeiro
* Administração do salão

---

Desenvolvido como Trabalho de Conclusão de Curso - Tecnologia em Sistemas para Internet.
