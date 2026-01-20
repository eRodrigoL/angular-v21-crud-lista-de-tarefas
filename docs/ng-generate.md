<!-- docs/ng-generate.md -->

# Angular CLI — ng generate

[↩️ Seção 4: Geração dos Artefatos](../GUIA.md#4---geração-dos-artefatos)

O comando **ng generate** (ou `ng g`) [🌐](https://angular.dev/cli/generate) é uma funcionalidade do **Angular CLI** responsável por gerar artefatos da aplicação de forma **padronizada e automatizada**.

Ele é amplamente utilizado em projetos Angular para:

- criar estruturas comuns da aplicação
- garantir consistência na organização de pastas e arquivos
- aplicar automaticamente boas práticas e convenções do framework
- reduzir erros manuais e retrabalho

O uso do `ng generate` assegura que cada artefato esteja corretamente integrado ao sistema de tipagem, injeção de dependências e build do Angular.

---

## Estrutura básica do comando

O comando `ng generate` gera o artefato criando automaticamente os arquivos necessários. Basta informar o **tipo** e o **caminho/nome** desejado, conforme a estrutura abaixo:

```bash
ng generate <tipo> <caminho/nome>
#              │         └── nome e localização do artefato
#              └── tipo do artefato (component, service, etc.)
```

> **Nota:** Em projetos onde o Angular CLI não está instalado globalmente, o comando pode ser executado via `npx`.

---

## Tipos de artefatos

**IMPORTANTE:** Para a maioria dos tipos, existem aliases oficiais que permitem encurtar o comando.

```bash
# EXEMPLO

# comando completo:
ng generate component user

# comando curto:
ng g c user
```

A tabela abaixo apresenta os principais **tipos** suportados pelo Angular CLI, destacando sua **responsabilidade**, seus **aliases oficiais** e uma descrição resumida.

| Schematic (Artefato) | Alias (CLI) | Responsabilidade | Descrição resumida                                        |
| -------------------- | ----------- | ---------------- | --------------------------------------------------------- |
| `component`          | `c`         | Interface        | Unidade visual reutilizável com template, estilo e lógica |
| `service`            | `s`         | Serviço          | Centraliza lógica de negócio, estado ou acesso a dados    |
| `module`             | `m`         | Organização      | Agrupa componentes, diretivas e serviços                  |
| `directive`          | `d`         | Comportamento    | Altera comportamento ou aparência de elementos do DOM     |
| `pipe`               | `p`         | Transformação    | Transforma valores para exibição nos templates            |
| `guard`              | `g`         | Acesso           | Restringe ou permite acesso a rotas                       |
| `resolver`           | `r`         | Dados            | Resolve dados antes da ativação de uma rota               |
| `interceptor`        | `i`         | HTTP             | Intercepta requisições e respostas HTTP                   |
| `interface`          | `i`\*       | Tipagem          | Define a forma (shape) de dados em TypeScript             |
| `class`              | `cl`        | Estrutura        | Classe TypeScript simples, sem semântica Angular          |
| `enum`               | `e`         | Enumeração       | Conjunto finito de valores constantes                     |
| `application`        | —           | Bootstrap        | Cria uma nova aplicação Angular                           |
| `library`            | —           | Reuso            | Cria uma biblioteca Angular reutilizável                  |
| `service-worker`     | —           | PWA              | Adiciona suporte a cache, offline e push notifications    |
| `web-worker`         | —           | Paralelismo      | Executa código fora da thread principal                   |

\* Observação técnica: os schematics `interface` e `interceptor` compartilham o alias `i`.  
O Angular CLI resolve corretamente o alias com base no contexto do comando.

---

[↩️ Seção 4: Geração dos Artefatos](../GUIA.md#4---geração-dos-artefatos)
