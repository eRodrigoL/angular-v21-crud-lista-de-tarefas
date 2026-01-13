<!-- GUIA.md -->

# GUIA DOS PASSOS DADOS NESTE REPOSITÓRIO

Este GUIA relata cada etapa e seu motivo até a finalização do projeto.

> ---
>
> **NOTAS IMPORTANTES:**
>
> - **_Todos os comandos aqui foram executados em ambiente Linux._**
> - **_Estão espalhados no texto links de "saiba mais" e de sites de ducumentação oficial, respectivamente representados por 🔎 e 🌐 ._**
>
> ---

## 0 - Ambiente antes da criação do projeto

### 0.1 - Instalação do NVM

O **NVM (Node Version Manager)** [🌐](https://www.nvmnode.com/pt/guide/) é uma ferramenta que permite instalar, gerenciar e alternar entre múltiplas versões do Node.js no mesmo sistema, de forma simples e segura.  
Ele é especialmente útil em ambientes de desenvolvimento, onde diferentes projetos podem exigir versões diferentes do Node.js.

O comando abaixo baixa e executa o script oficial de instalação do NVM:

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
```

Após a instalação, é necessário **fechar e abrir o terminal** (ou executar `source ~/.bashrc`, `~/.zshrc`, etc.) para que o comando `nvm` fique disponível.

### 0.2 - Instalação do Node.js via NVM

A versão **LTS (Long Term Support)** possui suporte estendido, recebe correções de segurança por mais tempo e é a mais indicada para uso em produção e em projetos estáveis.  
Por esse motivo, tende a ser mais confiável do que versões Current (experimentais).

O comando abaixo instala a versão LTS mais recente do Node.js e já a define como padrão:

```bash
nvm install --lts
```

> É possível consultar a versão do Node.js ativa através do comando `node -v` e a versão do npm através de `npm -v`.

## 1 - Criação do projeto Angular usando npx

O **npx** [🔎](docs/npx.md) é uma ferramenta que acompanha o npm e permite executar pacotes sem a necessidade de instalá-los globalmente.  
Isso evita conflitos de versão, dispensa instalações globais desnecessárias e garante que o Angular CLI utilizado seja exatamente o especificado no comando, tornando o ambiente mais limpo e previsível.

Neste projeto, o `npx` é utilizado para executar a versão mais recente do Angular CLI [🌐](https://angular.dev/overview) diretamente:

```bash
npx @angular/cli@latest new <nome-do-projeto>
```

O comando completo para criar o projeto foi: `npx @angular/cli@latest new angular-v21-crud-lista-de-tarefas`

---

## 2 - Configuração do backend

### 2.Passo 1: Instalação do json-server

O **json-server** [🔎](docs/json-server.md) é uma ferramenta que permite criar rapidamente uma **API REST fake** a partir de um arquivo `.json`, sem a necessidade de implementar um backend real.

Neste projeto, o `json-server` foi utilizado para simular operações CRUD (Create, Read, Update, Delete) da lista de tarefas.

Instalação:

```bash
npm install json-server --save-dev
```

Assim como o `concurrently`, o `json-server` foi instalado como dependência de desenvolvimento, pois **não deve ser incluído no build final da aplicação**.

### 2.Passo 2: Instalação do concurrently

O **concurrently** [🔎](docs/json-server.md) é uma ferramenta que permite executar **múltiplos comandos simultaneamente** em um único terminal.  
Neste projeto o `concurrently` foi usada para iniciar, ao mesmo tempo, o servidor Angular e um servidor de API fake (`json-server`), simplificando o fluxo de desenvolvimento.

Instalação:

```bash
npm install concurrently --save-dev
```

Após a instalação, o pacote fica registrado em `devDependencies` no `package.json`, indicando que ele é utilizado apenas em ambiente de desenvolvimento.

---
