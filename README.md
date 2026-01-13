<!-- README.md -->

# Lista de Tarefas

Aplicação web para treino do CRUD no framework Angular 21.

---

## 1 - Ambiente

Aplicação desenvolvido em **Angular** dentro de um ambiente Linux (WSL2) com **Node.js gerenciado via NVM**.

```txt
Node.js (LTS)  v24.12.0
npm            11.6.2
npx            11.6.2
```

### 1.1 - Frontend

O frontend da aplicação foi densenvolvida em **Angular 21** (versão LTS mais recente) e criado através do comando:

```bash
npx @angular/cli@latest new angular-v21-crud-lista-de-tarefas
```

> Resultado da verificação `npx ng version` (logo após criação):
>
> ```bash
> Angular CLI       : 21.0.4
> Angular           : 21.0.6
> Node.js           : 24.12.0
> Package Manager   : npm 11.6.2
> Operating System  : linux x64
> ```

Durante a inicialização do projeto o CLI realiza algumas perguntas, as quais foram selecionadas as seguintes respostas:

- **Estilos**: Sass (SCSS)
- **SSR / SSG**: não habilitado
- **Ferramentas de IA**: não configuradas

### 1.2 - Backend

O backend da aplicação foi desenvolvido em **json-server** simulando uma API (**API REST fake**) a partir de um arquivo JSON. O Json Server foi instalado através do comando:

```bash
npm install json-server --save-dev
```

> Versão (logo após instalações)
>
> ```json
> "devDependencies": {
>   "json-server": "^1.0.0-beta.3"
> }
> ```

---

## 2 - Instruções de uso

Como o Angular CLI **não foi instalado globalmente**, os comandos devem ser executados a partir do contexto do projeto.

### Iniciar a aplicação em modo de desenvolvimento

```bash
npm start
```

> Este comando executa internamente `ng serve` utilizando o Angular CLI instalado localmente em `node_modules`.

Alternativamente, o comando abaixo também é válido:

```bash
npx ng serve
```
