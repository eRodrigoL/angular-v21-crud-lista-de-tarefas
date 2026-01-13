# npx

[↩️ 1 - criaçã -do projeto angular usando npx](../GUIA.md#1---criação-do-projeto-angular-usando-npx)

O **npx** é uma ferramenta do ecossistema Node.js usada para executar pacotes diretamente, sem a necessidade de instalá-los globalmente ou adicioná-los permanentemente ao projeto.

O projeto foi iniciado com **npx** por 2 motivos:

- **principalmente** por causa do uso do **NVM** para gerenciamento de versões do Node.js
- e para minimizar a quantia de instalações globais, mantendo o ambiente de desenvolvimento mais limpo.

Ao optar por **não instalar o Angular CLI globalmente**, comandos `ng`, por exemplo, **não fica disponível diretamente no terminal**.  
Isso é um efeito esperado e consciente dessa decisão.

Nesse contexto, `npx` precisa ser adicionado antes de comandos `ng`. Ex.: `npx ng serve`

Ainda nesse contexto, instalações de dependências pertencente ao projeto devem ser instaladas normalmente. Ex.: `npm install json-server`.

[↩️ 1 - criaçã -do projeto angular usando npx](../GUIA.md#1---criação-do-projeto-angular-usando-npx)
