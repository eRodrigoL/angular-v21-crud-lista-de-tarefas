# Json Server

[↩️ Passo 2.1: Instalação do json-server](../GUIA.md#2passo-1-instalação-do-json-server)

O **json-server** [🌐](https://www.npmjs.com/package/json-server) é uma ferramenta que permite criar rapidamente uma **API REST fake** a partir de um arquivo `.json`, sem a necessidade de implementar um backend real.

Ele é amplamente utilizado em projetos frontend para:

- simular um backend durante o desenvolvimento
- testar integrações HTTP
- desenvolver funcionalidades CRUD de forma independente do servidor real

Com ele, é possível realizar operações como **GET**, **POST**, **PUT**, **PATCH** e **DELETE** utilizando endpoints REST, de maneira simples e rápida.

## Subir API Falsa

Para inicializar (ou **subir**) a **API Falsa** utilizando o Json Server, é necessário executar um script que chama o serviço, informando:

- o arquivo que servirá como base de dados
- a porta na qual o servidor será exposto

No ecossistema **Node.js**, esse tipo de script é normalmente configurado no arquivo `package.json`, que centraliza os comandos de execução do projeto.

### Estrutura do script para rodar o json-server

```json
"scripts": {
  "<nome>": "json-server --watch <arquivo> --port <porta>"
}
//   │           │            │      │        │      └── número da porta a ser aberta
//   │           │            │      │        └── flag para abrar a porta
//   │           │            │      └── nome/caminho do arquivo monitorado
//   │           │            └── flag mandando monitorar o <arquivo>
//   │           └── invoca o json-server
//   └── nome do script
```

[↩️ Passo 2.1: Instalação do json-server](../GUIA.md#2passo-1-instalação-do-json-server)
