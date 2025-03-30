# 🚀 Forum API - NestJS Clean Architecture

Bem-vindo ao **Forum API**, uma API RESTful robusta de perguntas e respostas construída com **NestJS** seguindo os princípios de **Clean Architecture**. Este projeto foi desenvolvido para demonstrar minhas habilidades como desenvolvedor back-end, focando em escalabilidade, manutenibilidade e boas práticas de desenvolvimento.

## 🎯 Objetivo do Projeto

O objetivo desta API é fornecer uma plataforma completa de fórum estilo Stack Overflow, onde usuários podem interagir através de perguntas, respostas, comentários e sistema de notificações. Com uma arquitetura limpa e bem estruturada, o projeto facilita a manutenção, testes e evolução contínua do código.

## 💡 Abordagem Arquitetural

Este projeto utiliza **Clean Architecture**, separando responsabilidades em camadas bem definidas:

- **Domain Layer**: Contém as entidades de negócio, casos de uso e regras de domínio puras
- **Application Layer**: Implementa os casos de uso específicos da aplicação
- **Infrastructure Layer**: Gerencia detalhes técnicos como banco de dados, cache, autenticação e HTTP
- **Separação de Conceitos**: Cada camada tem sua responsabilidade, facilitando testes e manutenção

## ⚡ Funcionalidades Principais

- **🔐 Autenticação JWT**: Sistema seguro de autenticação com tokens JSON Web
- **❓ Gestão de Perguntas**: Criação, edição, exclusão e listagem de perguntas
- **💬 Sistema de Respostas**: Responder perguntas e marcar melhor resposta
- **💭 Comentários**: Comentar em perguntas e respostas
- **📎 Upload de Arquivos**: Sistema de anexos com suporte a cloud storage
- **🔔 Notificações**: Sistema completo de notificações em tempo real
- **⚡ Cache Redis**: Otimização de consultas frequentes
- **🗄️ PostgreSQL**: Banco de dados relacional robusto
- **✅ Testes**: Cobertura completa com testes unitários e E2E

## 🛠️ Tecnologias Utilizadas

- **[NestJS](https://nestjs.com/)**: Framework Node.js progressivo para aplicações server-side
- **[TypeScript](https://www.typescriptlang.org/)**: Superset JavaScript com tipagem estática
- **[Prisma ORM](https://www.prisma.io/)**: ORM moderno para TypeScript e Node.js
- **[PostgreSQL](https://www.postgresql.org/)**: Banco de dados relacional de código aberto
- **[Redis](https://redis.io/)**: Cache em memória de alta performance
- **[JWT](https://jwt.io/)**: Autenticação stateless com JSON Web Tokens
- **[Vitest](https://vitest.dev/)**: Framework de testes rápido e moderno
- **[Zod](https://zod.dev/)**: Validação de schemas com TypeScript
- **[AWS SDK](https://aws.amazon.com/sdk-for-javascript/)**: Integração com serviços AWS
- **Clean Architecture**: Padrões de arquitetura limpa e SOLID

## 📁 Estrutura do Projeto

```
src/
├── core/              # Lógica de negócio genérica e blocos de construção
│   ├── entities/      # Entidades base, Value Objects, Aggregate Roots
│   ├── events/        # Sistema de eventos de domínio
│   ├── errors/        # Tratamento de erros customizados
│   └── repositories/  # Interfaces de repositórios
├── domain/            # Lógica de negócio específica
│   ├── forum/         # Contexto do fórum (perguntas, respostas)
│   └── notification/  # Contexto de notificações
├── infra/             # Detalhes de implementação
│   ├── auth/          # Autenticação JWT e guards
│   ├── cache/         # Implementação Redis
│   ├── cryptography/  # Hashing e encriptação
│   ├── database/      # Prisma e repositórios
│   ├── events/        # Event handlers
│   ├── http/          # Controllers e DTOs
│   └── storage/       # Upload de arquivos
└── test/              # Testes unitários e E2E
```

## 🌐 Endpoints da API

### 🔐 Autenticação
- `POST /sessions` - Autentica usuário e retorna access_token
- `POST /accounts` - Cria nova conta de usuário

### ❓ Perguntas
- `POST /questions` - Cria nova pergunta
- `GET /questions` - Lista perguntas recentes (paginado)
- `GET /questions/:slug` - Busca pergunta por slug
- `PUT /questions/:id` - Edita pergunta
- `DELETE /questions/:id` - Deleta pergunta
- `POST /questions/:questionId/comments` - Adiciona comentário
- `GET /questions/:questionId/comments` - Lista comentários
- `DELETE /questions/comments/:id` - Deleta comentário

### 💬 Respostas
- `POST /questions/:questionId/answers` - Adiciona resposta
- `GET /questions/:questionId/answers` - Lista respostas
- `PUT /answers/:id` - Edita resposta
- `DELETE /answers/:id` - Deleta resposta
- `PATCH /answers/:answerId/choose-as-best` - Marca melhor resposta
- `POST /answers/:answerId/comments` - Adiciona comentário
- `GET /answers/:answerId/comments` - Lista comentários
- `DELETE /answers/comments/:id` - Deleta comentário

### 📎 Anexos & Notificações
- `POST /attachments` - Upload de arquivo
- `PATCH /notifications/:notificationId/read` - Marca notificação como lida

## ⚙️ Como Executar o Projeto

### Pré-requisitos

- [Node.js](https://nodejs.org/) (versão 18 ou superior)
- [Docker](https://www.docker.com/get-started) (para PostgreSQL e Redis)
- [npm](https://www.npmjs.com/) ou [pnpm](https://pnpm.io/)

### Instalação

1. **Clone o repositório:**
   ```bash
   git clone https://github.com/geovanigcs/Forum-API-Nest.git
   cd Forum-API-Nest
   ```

2. **Instale as dependências:**
   ```bash
   npm install
   ```

3. **Configure as variáveis de ambiente:**
   ```bash
   cp .env.example .env
   ```
   
   Edite o arquivo `.env` com suas configurações:
   ```env
   DATABASE_URL="postgresql://postgres:docker@localhost:5433/nest-clean?schema=public"
   REDIS_HOST="127.0.0.1"
   REDIS_PORT=6380
   JWT_PRIVATE_KEY="your-private-key"
   JWT_PUBLIC_KEY="your-public-key"
   ```

4. **Inicie os containers Docker:**
   ```bash
   docker-compose up -d
   ```

5. **Execute as migrações do banco:**
   ```bash
   npx prisma migrate deploy
   npx prisma generate
   ```

### 🚀 Rodando a Aplicação

**Modo desenvolvimento:**
```bash
npm run start:dev
```
A API estará disponível em `http://localhost:3333`

**Modo produção:**
```bash
npm run build
npm run start:prod
```

### 🧪 Executando Testes

**Testes unitários:**
```bash
npm test
```

**Testes E2E:**
```bash
npm run test:e2e
```

**Cobertura de testes:**
```bash
npm run test:cov
```



## 🤝 Contribuindo

Contribuições são sempre bem-vindas! Para contribuir:

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/MinhaFeature`)
3. Commit suas mudanças (`git commit -m 'feat: adiciona nova feature'`)
4. Push para a branch (`git push origin feature/MinhaFeature`)
5. Abra um Pull Request

## 📄 Licença

Este projeto está sob a licença MIT. Consulte o arquivo `LICENSE` para mais detalhes.

## 📞 Contato

**Geovani Cordeiro**

- 📧 Email: geovanigcs.dev@gmail.com
- 💼 LinkedIn: [Geovani Cordeiro](https://linkedin.com/in/geovanigcs)
- 🐙 GitHub: [@geovanigcs](https://github.com/geovanigcs)

---

Desenvolvido com ❤️ e ☕ por [Geovani Cordeiro](https://github.com/geovanigcs)
