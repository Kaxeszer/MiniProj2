# MiniProj2 — Desenvolvimento do Front-end

Projeto desenvolvido no âmbito da unidade curricular **Programação Web Avançada**, do **Mestrado em Engenharia Informática e Tecnologia Web (UAb / UTAD)**.

**Tarefa 3.2 — Miniprojeto: Desenvolvimento do front-end**

## Objetivo

Dar continuidade ao projeto **Animalec**, através da configuração e execução local da aplicação e do desenvolvimento das funcionalidades das novas entidades **Sponsors (Patrocinadores)** e **Experts (Especialistas)**, planeadas na Tarefa 3.1.

O trabalho parte dos wireframes, mockups e protótipos HTML5 anteriormente desenvolvidos, com o objetivo de implementar as novas funcionalidades no front-end e explorar a comunicação com a API do Animalec.

## Projeto de referência

O projeto utiliza como base o código original do Animalec, organizado em duas partes: front-end e back-end.

Repositório de referência: [josthelvish/Animalec](https://github.com/josthelvish/Animalec).

O trabalho realizado na Tarefa 3.1b foi aproveitado como ponto de partida para este miniprojeto.

## Estrutura do projeto

```text
MiniProj2/
├── Animalec/
│   ├── backend/                  # API Node.js / Express
│   └── frontend/                 # Aplicação Vue.js 2
│       └── public/
│           └── prototipos_LP/   # Protótipos HTML5
├── docs/
│   ├── Mockups_LP_Animalec.pdf
│   └── Wireframes_LP_Animalec.pdf
├── .gitignore
└── README.md
```

## Tecnologias

- **Front-end:** Vue.js 2, Vue CLI, HTML5, CSS3 e JavaScript
- **Back-end:** Node.js e Express
- **Base de dados:** MongoDB / Mongoose
- **Gestão de dependências:** npm
- **Ferramentas:** MongoDB Community, Studio 3T e Postman

## Instalação e execução

O projeto utiliza **Node.js 16**, devido à compatibilidade com as dependências do Animalec. A versão utilizada nos testes anteriores foi a `16.20.2`, gerida através do **nvm**.

### Base de dados

A configuração prevista utiliza uma base de dados MongoDB local, com o nome `test`, na porta `27017`.

No ficheiro `Animalec/backend/config/config.js`, o endereço de ligação deverá ser:

```javascript
uri: 'mongodb://localhost:27017/test'
```

As coleções necessárias serão copiadas da base de dados de referência para a base de dados local através do Studio 3T.

### Back-end

A partir da raiz do repositório:

```bash
nvm use 16
cd Animalec/backend
npm install
npm start
```

Endereço previsto: [http://localhost:8080](http://localhost:8080).

### Front-end

Num segundo terminal, a partir da raiz do repositório:

```bash
nvm use 16
cd Animalec/frontend
npm install
npm run serve
```

O front-end deverá comunicar com a API disponível em `http://localhost:8080`.

Endereço previsto: [http://localhost:8081](http://localhost:8081).

## Trabalho desenvolvido anteriormente

Na Tarefa 3.1b foram criados seis protótipos HTML5 para as entidades **Sponsors** e **Experts**, incluindo páginas de listagem, formulário e detalhe.

Os protótipos permitem demonstrar operações de criação, consulta, edição e remoção de registos, utilizando armazenamento local no navegador (`localStorage`).

Foram também realizados ajustes de navegação, apresentação e responsividade no front-end do Animalec.

Os wireframes e mockups encontram-se disponíveis na pasta `docs/`.

## Estado do trabalho

### Tarefa 3.1b — Prototipagem

- [x] Análise da interface original do Animalec.
- [x] Elaboração dos wireframes e mockups.
- [x] Desenvolvimento dos protótipos HTML5.
- [x] Integração dos protótipos na navegação da área de administração.
- [x] Testes de navegação e responsividade.

### Tarefa 3.2 — Desenvolvimento do front-end

- [x] Preparação da estrutura inicial do MiniProj2 a partir do trabalho anterior.
- [ ] Instalação e configuração da MongoDB local.
- [ ] Cópia das coleções para a base de dados local.
- [ ] Configuração e testes do back-end com a base de dados local.
- [ ] Testes da API através do Postman.
- [ ] Configuração e validação do front-end com a API local.
- [ ] Implementação das novas entidades no front-end Vue.js.
- [ ] Testes finais das funcionalidades e da comunicação com a API.

## Autor

**Nome:** Luís Carlos Crispim Pereira  
**N.º de estudante:** 2026106983