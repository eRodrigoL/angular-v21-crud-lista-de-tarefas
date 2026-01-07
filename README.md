<!-- README.md -->

# Lista de Tarefas

Aplicação web para treino do CRUD no framework Angular 21.

---

## Ambiente

Aplicação desenvolvida em **Angular** dentro de um ambiente Linux (WSL2) com **Node.js gerenciado via NVM**.

```txt
Node.js (LTS)  v24.12.0
npm            11.6.2
npx            11.6.2
```

### Frontend

Aplicação densenvolvida em **Angular 21** (versão LTS mais recente) através do comando:

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

#### Configurações escolhidas

- **Framework**: Angular 21
- **Estilos**: Sass (SCSS)
- **SSR / SSG**: não habilitado
- **Ferramentas de IA**: não configuradas

---

## Instruções de uso

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

---
