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

### 2.Passo 3: Banco de dados + scripts de otimização

**1 -** O `json-server` necessita de um arquivo JSON que atua como banco de dados da API, fornecendo e/ou recebendo os dados.

Para garantir previsibilidade durante o desenvolvimento, foi adotado o padrão de **arquivo matriz (seed)**, mantendo versionado apenas o arquivo `dados-iniciais.json`.

```bash
# ÁRVORE DE ARQUIVOS
📁 projeto/
├── [...]
├── 📁 api-simulada/
│   └── 📄 dados-iniciais.json
├── [...]
```

O arquivo efetivamente utilizado pelo `json-server` (`dados.json`) **não é versionado** e é gerado automaticamente a partir da matriz.

---

**2 -** O `json-server` funciona como um serviço de API, cujo servidor é iniciado por meio de um script que aponta para o arquivo de dados gerado.

```json
// package.json
//[...]
"scripts": {
  //[...]
  "api": "json-server --watch api-simulada/dados.json --port 3000"
},
//[...]
```

> _**Nota**: A flag `--watch` permite que alterações no arquivo de dados sejam refletidas automaticamente durante o desenvolvimento._

---

**3 -** Antes de iniciar a API fake, é necessário garantir que o arquivo `dados.json` exista e esteja em seu estado inicial.

Para isso, foi criado um script responsável por copiar a matriz (`dados-iniciais.json`) e gerar o banco utilizado pela API.

```json
// package.json
//[...]
"scripts": {
  //[...]
  "seed": "node -e \"require('fs').copyFileSync('api-simulada/dados-iniciais.json', 'api-simulada/dados.json')\""
}
//[...]
```

---

**4 -** Com auxílio do `concurrently`, o script `start` foi ajustado para executar, em um único comando:

- a geração do banco de dados para a API simulada (**dados.json**)
- o servidor da API simulada (**json-server**)
- o servidor da aplicação **Angular**

```json
// package.json
//[...]
"scripts": {
  //[...]
  "start": "npm run seed && concurrently \"npm run api\" \"ng serve\"",
  "api": "json-server --watch api-simulada/dados.json --port 3000"
}
//[...]
```

Esse fluxo evita commits desnecessários, garante consistência nos testes CRUD e mantém o ambiente de desenvolvimento sempre previsível.
