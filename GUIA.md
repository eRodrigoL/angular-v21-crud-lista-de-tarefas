<!-- GUIA.md -->

# GUIA DOS PASSOS DADOS NESTE REPOSITÓRIO

Este GUIA relata cada etapa e seu motivo até a finalização do projeto.

> ---
>
> **NOTA IMPORTANTE:**
>
> _Todos os comandos aqui foram executados em ambiente Linux._
>
> ---

## Instalação do NVM

O **NVM (Node Version Manager)** é uma ferramenta que permite instalar, gerenciar e alternar entre múltiplas versões do Node.js no mesmo sistema, de forma simples e segura.  
Ele é especialmente útil em ambientes de desenvolvimento, onde diferentes projetos podem exigir versões diferentes do Node.js.

O comando abaixo baixa e executa o script oficial de instalação do NVM:

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
```

Após a instalação, é necessário **fechar e abrir o terminal** (ou executar `source ~/.bashrc`, `~/.zshrc`, etc.) para que o comando `nvm` fique disponível.

## Instalação do Node.js via NVM

A versão **LTS (Long Term Support)** possui suporte estendido, recebe correções de segurança por mais tempo e é a mais indicada para uso em produção e em projetos estáveis.  
Por esse motivo, tende a ser mais confiável do que versões Current (experimentais).

O comando abaixo instala a versão LTS mais recente do Node.js e já a define como padrão:

```bash
nvm install --lts
```

> É possível consultar a versão do Node.js ativa através do comando `node -v` e a versão do npm através de `npm -v`.

## Criação do projeto Angular usando npx

O **npx** é uma ferramenta que acompanha o npm e permite executar pacotes sem a necessidade de instalá-los globalmente.  
Isso evita conflitos de versão, dispensa instalações globais desnecessárias e garante que o Angular CLI utilizado seja exatamente o especificado no comando, tornando o ambiente mais limpo e previsível.

Neste projeto, o `npx` é utilizado para executar a versão mais recente do Angular CLI diretamente:

```bash
npx @angular/cli@latest new <nome-do-projeto>
```

O comando completo para criar o projeto foi: `npx @angular/cli@latest new angular-v21-crud-lista-de-tarefas`

### npx

O **npx** é uma ferramenta do ecossistema Node.js usada para executar pacotes diretamente, sem a necessidade de instalá-los globalmente ou adicioná-los permanentemente ao projeto.

O projeto foi iniciado com **npx** por 2 motivos:

1. (e principal) por causa do uso do **NVM** para gerenciamento de versões do Node.js
2. para minimizar a quantia de instalações globais, mantendo o ambiente de desenvolvimento mais limpo.

Ao optar por **não instalar o Angular CLI globalmente**, comandos `ng`, por exemplo, **não fica disponível diretamente no terminal**.  
Isso é um efeito esperado e consciente dessa decisão.

Nesse contexto, `npx` precisa ser adicionado antes de comandos `ng`. Ex.: `npx ng serve`

Ainda nesse contexto, instalações de dependências pertencente ao projeto devem ser instaladas normalmente. Ex.: `npm install json-server`.
