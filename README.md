# BiomaPetShop

> Sistema Web de Gestão e Agendamentos para Pet Shop com arquitetura SSR e banco de dados relacional.

Integrantes
- Anttonio Osório Molinaro Maccagnini
- Gabriel Lengert Guedes
- Heitor Lopes Reis
- João Pedro Alves de Lima
- João Vitor Paranhos
- Rafael Alexandre Alves Bandoch

Link do Repositório: https://github.com/RafaelBandoch/BiomaPetShop-MM

---

## 1. Sobre o Projeto

O BiomaPetShop é uma aplicação web desenvolvida para o gerenciamento de rotinas administrativas e operacionais em pet shops. O objetivo do sistema é otimizar o atendimento, prevenir conflitos de horários e centralizar as informações vitais do estabelecimento.

O sistema abrange o controle completo das seguintes entidades:
- Clientes e seus dados de contato.
- Pets associados aos seus respectivos tutores.
- Serviços com precificação adaptada de acordo com o porte do animal.
- Agendamentos e controle de status de atendimento.
- Dashboard contendo métricas e consolidados operacionais.

---

## 2. Funcionalidades Principais

### Autenticação e Controle de Acesso
- Autenticação com Login e Logout para controle de sessão.
- Perfis de acesso diferenciados (Administrador e Atendente).
- Proteção de rotas internas acessíveis apenas por usuários autenticados.

### Gestão de Clientes
- Operações completas de CRUD (Cadastro, Listagem, Edição e Exclusão).
- Validação de e-mail e telefone únicos para prevenir registros duplicados.
- Exibição da lista de pets vinculados ao perfil de cada cliente.

### Gestão de Pets
- Cadastro de pets associados ao cliente.
- Armazenamento de informações detalhadas: nome, espécie, raça, porte (pequeno, médio ou grande) e observações.
- Exclusão em cascata dos agendamentos e registros vinculados ao pet.

### Gestão de Serviços
- Cadastro e edição de serviços do estabelecimento.
- Tabela de preços diferenciada por porte do pet e definição da duração estimada em minutos.

### Agendamentos (Transação Principal)
- Criação de agendamentos associando cliente, pet, data/hora e múltiplos serviços.
- Cálculo automático do valor total com base nos preços dos serviços e no porte do pet.
- Controle do ciclo de vida do agendamento através dos status: Agendado, Concluído e Cancelado.
- Reagendamento e cancelamento de horários.
- Filtro por status na visualização geral.

### Dashboard e Relatórios
- Apresentação de métricas diárias (totais de agendamentos, clientes, pets e serviços).
- Listagem dos clientes cadastrados e exibição dos agendamentos mais recentes.

---

## 3. Regras de Negócio (RN)

1. Unicidade de Dados de Contato: O e-mail e o telefone informados no cadastro do cliente devem ser únicos no banco de dados.
2. Limite de Capacidade por Horário: Não é permitido registrar mais de 3 (três) agendamentos para a mesma tarefa/serviço no mesmo horário.
3. Validação de Agendamento do Pet: O mesmo pet não pode ter agendamentos sobrepostos para os mesmos serviços na mesma data e horário.
4. Dependência de Serviços: Os serviços de Tosa e Hidratação dependem obrigatoriamente do agendamento conjunto do serviço de Banho.
5. Privilégios do Administrador: A visualização de senhas e a exclusão de usuários do sistema são restritas ao perfil de Administrador.

---

## 4. Tecnologias e Arquitetura

O sistema foi estruturado seguindo o padrão arquitetural MVC (Model-View-Controller) com renderização no servidor (SSR):

- Linguagem / Runtime: Node.js
- Framework Web: Express
- Template Engine: EJS (Server-Side Rendering)
- Banco de Dados: SQLite (Relacional)
- Criptografia: bcrypt (hashing seguro para armazenamento de senhas)
- Versionamento: Git e GitHub

---

## 5. Estrutura de Diretórios
```
BiomaPetShop-MM/
├── src/
│   ├── controllers/   # Regras de controle e lógica das rotas
│   ├── models/        # Acesso e queries ao banco de dados SQLite
│   ├── routes/        # Mapeamento e definição das rotas do sistema
│   └── views/         # Interfaces e páginas renderizadas via EJS
├── public/            # Arquivos estáticos (CSS, imagens, scripts client-side)
├── database/          # Arquivos de migração ou script do banco de dados
├── app.js             # Arquivo principal e ponto de entrada da aplicação
└── package.json       # Gerenciamento de dependências e scripts do projeto
````
---

## 6. Instruções para Execução Local

### Pré-requisitos
- Node.js instalado na máquina.
- Git instalado.

### Passo a Passo

1. Clonar o repositório do projeto:
   git clone https://github.com/RafaelBandoch/BiomaPetShop-MM.git

2. Navegar para a pasta do repositório:
   cd BiomaPetShop-MM

3. Instalar as dependências do projeto:
   npm install

4. Iniciar o servidor da aplicação:
   npm start

   Para executar em ambiente de desenvolvimento (com auto-reload):
   npm run dev

5. Acessar no navegador:
   Abra o endereço http://localhost:3000 (ou a porta configurada no ambiente).

---

Projeto desenvolvido para a disciplina de Manutenção e Melhoria de Software.
