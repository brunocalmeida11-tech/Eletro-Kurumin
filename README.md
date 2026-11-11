# Eletro Kurumin — Gestão de Estoque

Sistema web para controlar componentes eletrônicos, usuários, entradas e saídas do estoque e relatório de valores.

## Tecnologias
- HTML, CSS e JavaScript
- Node.js e Express
- MySQL
- Sessões para autenticação e bcryptjs para proteger as senhas

## Requisitos
- Node.js instalado
- MySQL instalado e em execução (XAMPP também pode ser usado)

## Como executar

1. Abra o MySQL pelo XAMPP ou pelo serviço instalado.
2. Abra o arquivo `database.sql` no MySQL Workbench/phpMyAdmin e execute todo o script.
3. Abra o terminal na pasta do projeto e instale as dependências:

   ```bash
   npm install
   ```

4. Copie `.env.example` para um arquivo chamado `.env`.
5. Confira os dados de acesso do MySQL no `.env` (`DB_USER`, `DB_PASSWORD` e `DB_NAME`).
6. Inicie o sistema:

   ```bash
   npm start
   ```

7. Acesse `http://localhost:3000` no navegador e crie a primeira conta.

## Funcionalidades
- Cadastro de usuário e login com e-mail e senha.
- Cadastro, listagem, edição e exclusão de componentes.
- Categorias de componentes.
- Registro de entrada e saída com validação para não permitir estoque negativo.
- Histórico das últimas movimentações.
- Relatório detalhado com preço, quantidade e valor total por componente.
- Resumo do valor total do estoque.

## Estrutura do banco
- `usuario`: usuários que acessam o sistema.
- `categoria`: categorias dos componentes.
- `componente`: dados e quantidade disponível de cada componente.
- `movimentacao`: histórico de entradas e saídas.

O valor total de cada componente é calculado por `preco × quantidade_estoque`. O valor total do estoque é a soma desses valores.

## Rotas principais
| Método | Rota | Função |
|---|---|---|
| POST | `/api/auth/cadastro` | Criar usuário |
| POST | `/api/auth/login` | Entrar |
| GET | `/api/auth/sessao` | Consultar sessão |
| POST | `/api/auth/logout` | Sair |
| GET/POST | `/api/categorias` | Listar/criar categorias |
| GET/POST | `/api/componentes` | Listar/cadastrar componentes |
| PUT/DELETE | `/api/componentes/:id` | Editar/excluir componente |
| GET/POST | `/api/movimentacoes` | Listar/criar movimentações |
| GET | `/api/relatorios` | Gerar relatório |

## Observação
Projeto acadêmico para execução local. Para publicar em produção, configure HTTPS, armazenamento de sessão persistente, proteção contra tentativas repetidas de login e credenciais seguras. Não envie o arquivo `.env` ao GitHub.
