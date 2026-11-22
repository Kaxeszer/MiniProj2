# MiniProj2 — Desenvolvimento do Front-end

Projeto desenvolvido no âmbito da unidade curricular **Programação Web Avançada**, do **Mestrado em Engenharia Informática e Tecnologia Web (UAb / UTAD)**.

**Tarefa 3.2 — Miniprojeto: Desenvolvimento do Front-end**

## Objetivo

Dar continuidade ao projeto **Animalec**, através da configuração e execução local da aplicação e da integração das funcionalidades desenvolvidas para as entidades **Sponsors (Patrocinadores)** e **Experts (Especialistas)**, planeadas e implementadas na Tarefa 3.1.

O projeto aproveita os wireframes, mockups e protótipos HTML5 anteriormente desenvolvidos, permitindo explorar a estrutura do Animalec, a interação do utilizador e a comunicação entre o front-end e o back-end através de uma API REST.

## Projeto de referência

O projeto utiliza como base o código original do **Animalec**, organizado em duas componentes:

- **Front-end:** aplicação desenvolvida em Vue.js 2.
- **Back-end:** API desenvolvida em Node.js e Express, com persistência de dados em MongoDB.

Repositório de referência: [josthelvish/Animalec](https://github.com/josthelvish/Animalec).

O trabalho realizado na **Tarefa 3.1b** foi aproveitado como ponto de partida para este miniprojeto.

## Estrutura do projeto

```text
MiniProj2/
├── Animalec/
│   ├── backend/                  # API Node.js / Express
│   └── frontend/                 # Aplicação Vue.js 2
│       └── public/
│           └── prototipos_LP/    # Implementação Sponsors e Experts
├── database/                     # Exportação da base de dados MongoDB
├── docs/
│   ├── Mockups_LP_Animalec.pdf
│   └── Wireframes_LP_Animalec.pdf
├── .gitignore
└── README.md
```

A pasta `database/` contém uma exportação da base de dados local `test`, realizada através do Studio 3T em formato **BSON (mongodump)**, com compressão gzip.

## Tecnologias utilizadas

- **Front-end:** Vue.js 2, Vue CLI, HTML5, CSS3 e JavaScript.
- **Back-end:** Node.js e Express.
- **Base de dados:** MongoDB e Mongoose.
- **Gestão de dependências:** npm.
- **Ferramentas:** WebStorm, MongoDB Community, Studio 3T, Postman e GitHub Desktop.
- **Controlo de versões:** Git e GitHub.

## Instalação e execução

O projeto foi configurado e testado localmente com **Node.js 16.20.2**, gerido através do **nvm**, devido à compatibilidade com as dependências da versão original do Animalec.

É necessário ter o MongoDB instalado e em execução na porta `27017`.

### 1. Preparação da base de dados

A aplicação utiliza uma base de dados MongoDB local denominada `test`.

A base de dados foi preparada através dos seguintes procedimentos:

1. Instalação do MongoDB Community.
2. Instalação e configuração do Studio 3T.
3. Criação de uma ligação à instância MongoDB local (`localhost:27017`).
4. Criação da base de dados `test`.
5. Cópia das coleções da base de dados de referência para a base de dados local.
6. Verificação e correção do documento do utilizador administrador para permitir a autenticação.
7. Exportação da base de dados local para a pasta `database/` do projeto.

#### Restaurar a base de dados disponibilizada

O repositório inclui uma exportação da base de dados em formato **BSON (mongodump)**, com compressão gzip.

Para restaurar os dados através do Studio 3T:

1. Iniciar o serviço MongoDB local.
2. Abrir o Studio 3T e estabelecer ligação a `localhost:27017`.
3. Selecionar a funcionalidade **Import**.
4. Escolher o formato **BSON — mongodump**.
5. Selecionar a exportação existente na pasta `database/`, utilizando a opção correspondente ao formato exportado (pasta ou arquivo).
6. Configurar a importação para a base de dados local `test`.
7. Executar a importação e confirmar a existência das coleções.

A exportação permite recuperar os dados utilizados nos testes locais, incluindo os registos necessários ao funcionamento da aplicação.

### 2. Configuração do back-end

No ficheiro:

`Animalec/backend/config/config.js`

O endereço de ligação à base de dados deve estar configurado da seguinte forma:

```javascript
uri: 'mongodb://localhost:27017/test'
```

A partir da raiz do repositório, executar:

```bash
nvm use 16
cd Animalec/backend
npm install
npm start
```

O back-end deverá iniciar na porta `8080`.

**Endereço da API:** http://localhost:8080

No terminal deverá surgir uma mensagem semelhante a:

```text
Your app is listening on 8080
```

A ligação à base de dados deverá também ser estabelecida com sucesso.

### 3. Configuração do front-end

No ficheiro:

`Animalec/frontend/src/api/config.js`

O endereço da API deverá ser:

```javascript
const API_URL = "http://localhost:8080";
```

Num segundo terminal, a partir da raiz do repositório:

```bash
nvm use 16
cd Animalec/frontend
npm install
npm run serve
```

O front-end deverá iniciar na porta `8081`, conforme a configuração utilizada.

**Endereço da aplicação:** http://localhost:8081

É importante utilizar **Node.js 16**, uma vez que versões mais recentes, como a versão 22, podem provocar erros de compatibilidade com o Webpack utilizado neste projeto.

## Testes realizados

### Testes do back-end com Postman

A API foi testada através do Postman, utilizando a base de dados MongoDB local.

#### Autenticação

**Método:** `POST`

**Endpoint:**

```text
http://localhost:8080/auth
```

**Corpo do pedido (JSON):**

```json
{
  "username": "admin",
  "password": "admin"
}
```

**Resultado:** autenticação efetuada com sucesso, com resposta HTTP `200 OK` e disponibilização do token no cabeçalho `Authorization`.

#### Consulta de animais

**Método:** `GET`

**Endpoint:**

```text
http://localhost:8080/animals
```

Foi utilizado o token obtido na autenticação, através do cabeçalho:

```text
Authorization: <token obtido no login>
```

**Resultado:** resposta HTTP `200 OK`, com o código `AnimalFound` e uma lista de **10 animais** em formato JSON.

Este teste confirmou a comunicação entre a API e a base de dados MongoDB local.

### Testes do front-end

O front-end foi iniciado com sucesso através do Vue CLI, utilizando Node.js 16.

Foram verificados:

- A abertura da aplicação Animalec no navegador.
- O funcionamento da navegação.
- A autenticação com o utilizador administrador.
- O acesso à área de administração.
- O funcionamento das funcionalidades desenvolvidas anteriormente.

Durante os testes, foi necessário limpar os dados de sessão anteriormente guardados no navegador para efetuar uma nova autenticação.

Após esse procedimento, o funcionamento da aplicação foi confirmado.

## Trabalho desenvolvido na Tarefa 3.1b

Na Tarefa 3.1b foram desenvolvidos **seis protótipos HTML5** relacionados com as entidades:

- **Sponsors (Patrocinadores)**.
- **Experts (Especialistas)**.

Para cada entidade foram desenvolvidas interfaces de:

- Listagem de registos.
- Formulário de criação e edição.
- Visualização de detalhes.

Os protótipos permitem demonstrar operações de criação, consulta, edição e remoção de registos, recorrendo ao armazenamento local do navegador (`localStorage`).

Foram também realizados ajustes de navegação, apresentação e responsividade na interface do Animalec.

Os protótipos encontram-se disponíveis em:

`Animalec/frontend/public/prototipos_LP/`

Os documentos de planeamento e desenho da interface encontram-se na pasta `docs/`:

- `Wireframes_LP_Animalec.pdf`
- `Mockups_LP_Animalec.pdf`

## Estado do trabalho

### Tarefa 3.1b — Prototipagem

- [x] Análise da interface original do Animalec.
- [x] Elaboração dos wireframes e mockups.
- [x] Desenvolvimento dos seis protótipos HTML5.
- [x] Implementação das funcionalidades previstas para Sponsors e Experts.
- [x] Integração dos protótipos na navegação da área de administração.
- [x] Testes de navegação e responsividade.

### Tarefa 3.2 — Desenvolvimento do front-end

- [x] Preparação da estrutura do MiniProj2 a partir do trabalho anterior.
- [x] Instalação e configuração do MongoDB local.
- [x] Cópia das coleções para a base de dados local `test`.
- [x] Configuração do back-end para utilizar o MongoDB local.
- [x] Correção e validação da autenticação do utilizador administrador.
- [x] Teste de autenticação através do Postman (`POST /auth`).
- [x] Teste da consulta de animais através do Postman (`GET /animals`).
- [x] Configuração e execução do front-end com Node.js 16.
- [x] Validação do login e do funcionamento da aplicação no navegador.
- [x] Verificação das funcionalidades das entidades Sponsors e Experts desenvolvidas anteriormente.
- [x] Exportação da base de dados MongoDB local para a pasta `database/`.
- [x] Atualização da documentação do projeto.

## Repositório e entrega

O projeto é disponibilizado no GitHub através do repositório **MiniProj2**, contendo o código do front-end e do back-end, os protótipos, os documentos de planeamento, a exportação da base de dados e as instruções de instalação.

## Autor

**Nome:** Luís Carlos Crispim Pereira  
**N.º de estudante:** 2026106983  
**Curso:** Mestrado em Engenharia Informática e Tecnologia Web  
**Unidade curricular:** Programação Web Avançada  
**Instituições:** Universidade Aberta / Universidade de Trás-os-Montes e Alto Douro
