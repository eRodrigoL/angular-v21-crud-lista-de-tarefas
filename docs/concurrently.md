<!-- docs/concurrently.md -->

# Concurrently

[↩️ Passo 2.2: Instalação do concurrently](../GUIA.md#2passo-2-instalação-do-concurrently)

O **concurrently** [🌐](https://www.npmjs.com/package/concurrently) é uma ferramenta que permite executar **múltiplos comandos simultaneamente** em um único terminal.

Ela é amplamente utilizada em projetos para:

- iniciar múltiplos serviços ao mesmo tempo
- reduzir a quantidade de terminais abertos durante o desenvolvimento
- simplificar o fluxo de execução de aplicações que dependem de mais de um processo

No contexto deste projeto, o `concurrently` é utilizado para executar, de forma paralela:

- o servidor da aplicação Angular
- o servidor da API fake (Json Server)

## Executar múltiplos serviços em paralelo

Para iniciar mais de um serviço simultaneamente, o `concurrently` executa diversos comandos em paralelo dentro de um único script.

No ecossistema **Node.js**, esse tipo de configuração é normalmente definida no arquivo `package.json`, que centraliza os scripts de execução do projeto.

### Estrutura do script para rodar múltiplos serviços

```json
"scripts": {
  "<nome>": "concurrently \"<comando-1>\" \"<comando-2>\""
}
//   │           │              │               │
//   │           │              │               └── segundo comando executado em paralelo
//   │           │              └── primeiro comando executado em paralelo
//   │           └── invoca o concurrently
//   └── nome do script
```

A partir dessa estrutura, é possível combinar qualquer número de comandos, permitindo que serviços independentes sejam iniciados de forma integrada.

> **NOTA:** Esse padrão é utilizado exclusivamente em ambiente de desenvolvimento, pois tem como objetivo **otimizar a produtividade**, e não compor o processo final de build da aplicação.

[↩️ Passo 2.2: Instalação do concurrently](../GUIA.md#2passo-2-instalação-do-concurrently)
