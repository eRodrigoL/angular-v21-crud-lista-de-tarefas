<!-- docs/alias.md -->

# Aliases (Path Mapping)

[↩️ Seção 3: Definição de Aliases](../GUIA.md#3---definição-de-aliases)

Os **aliases** (também chamados de _path aliases_ ou _path mapping_) permitem criar **atalhos semânticos** para caminhos de importação em um projeto.

Eles substituem caminhos relativos longos e frágeis:

```ts
import { Algo } from '../../../services/algum-servico';
```

por imports mais claros e padronizados:

```ts
import { Algo } from '@servicos/algum-servico';
```

Aliases são uma **boa prática** em projetos modernos porque:

- melhoram a legibilidade dos imports
- reduzem o uso excessivo de `../`
- facilitam refatorações e reorganização de pastas
- tornam o código mais previsível e manutenível

Esses benefícios se tornam mais evidentes à medida que o projeto cresce.

---

## Aliases no ecossistema TypeScript / Angular

Em projetos **Angular**, aliases são configurados no arquivo `tsconfig.json` por meio das propriedades:

- `baseUrl`
- `paths`

O **Angular CLI** reconhece automaticamente essas configurações, não sendo necessário nenhum ajuste adicional no build ou no runtime da aplicação.

---

## Estrutura básica de configuração de aliases

A definição de aliases segue uma estrutura declarativa no `tsconfig.json`, onde cada alias é mapeado para um caminho físico do projeto.

```json
{
  "compilerOptions": {
    "baseUrl": "./",
    "paths": {
      "<alias>": ["<caminho>"],
      "<alias>/*": ["<caminho>/*"]
    }
  }
}
```

Onde:

- `baseUrl` define o diretório base para resolução dos imports
- `paths` associa aliases a diretórios reais do projeto
- o uso de `/*` permite importar arquivos internos ao caminho mapeado

> **Nota:** `"./"` representa a raiz do projeto, mas em Angular também é comum usar `src` para apontar o ponto de partida direto para a pasta src/

---

## Considerações técnicas

- aliases atuam **apenas em tempo de compilação**
- não alteram a estrutura física do projeto
- são resolvidos pelo compilador TypeScript e pelo Angular CLI

> **Nota:** Em projetos Node.js sem Angular, pode ser necessário configurar aliases também no runtime ou no bundler.  
> No contexto deste projeto, isso não é necessário.

[↩️ Seção 3: Definição de Aliases](../GUIA.md#3---definição-de-aliases)
