# EXG2_2023

Exercício em Grupo 2 - Analisador sintático

## Descrição

Escreva um programa em C que realiza a análise sintática de um ficheiro no formato [JavaScript Object Notation - JSON](https://pt.wikipedia.org/wiki/JSON "JSON - Wikipedia").

Este tipo de ficheiro apresenta a seguinte estrutura:

```json
{
  "alunos": [
    {
      "nome": "João da Silva",
      "idade": 18,
      "curso": "Engenharia Informatica",
      "matricula": "123456"
    },
    {
      "nome": "Maria Souza",
      "idade": 20,
      "curso": "Licenciatura em Informatica e Gestao",
      "matricula": "789012"
    },
    {
      "nome": "Pedro Santos",
      "idade": 19,
      "curso": "Licenciatura em Informatica e Ensino",
      "matricula": "345678"
    }
  ]
}
```

Seu programa começa por apresentar um menu ao utilizador com as seguintes opções:

* `1 - Analise sintatica`
* `2 - Sair`

---

# Requisitos:

O código deve compilar sem erros ou *warnings* utilizando o **`gcc`** com as seguintes flags:

- `-g -Wvla -Wall -Wpedantic -Wextra -Wdeclaration-after-statement`

---

### Opção 1:

A opção `1 - Analise sintatica` deve começar por pedir ao utilizador informações sobre o tamanho da stack que será utilizada para a análise sintática. O que deve ser feito através da seguinte mensagem: `Informe o tamanho da stack: `

Em seguida, o programa dever perguntar qual o nome do ficheiro no formato `JSON` para realizar a análise sintática será lido, fazendo a pergunta `Informe o nome do ficheiro a analisar:`. O programa deve verificar se o ficheiro existe e se está bem formado e exibir a mensagem apropriada para os seguintes casos:

- `FBF - Ficheiro bem formado!` se o ficheiro estiver bem formado
- `FMF - Ficheiro mal formado!` caso contrário
- `FNE - Ficheiro não existe!` se o ficheiro não existir

Desta forma, quando os símbolos que delimitam o escopo de um bloco de código "abrirem", isto é ao encontrar os símbolos `{` e `[` realizam-se as seguintes operações:

* `push` do símbolo `{` ou `[` na stack

Quando for encontrado um símbolo que fecha um bloco de código, isto é, `}` ou `]`, deve ser efetuada a seguinte operação:

* `pop` do símbolo `{` ou `[` com o indicativo desta operação no ecrã no seguinte formato: `pop {` ou `pop [`

### Erros:

Quando, durante a execução **desta opção** no programa, ocorrerem os seguintes erros:

- `push` e a `stack` estiver com sua **capacidade esgotada**, imprima `erro 01: stack overflow!` e imprime `FMF - Ficheiro mal formado!` e volta ao menu principal.
- `pop` e a `stack` estiver **vazia**, imprima `erro 02: stack underflow!` e imprime `FMF - Ficheiro mal formado!` e volta ao menu principal.

---


### Opção 2:

A opção `2 - Sair` deve permitir ao utilizador sair do programa.

---

# Dicas:

- Organizar e modularizar seu código fazendo o uso de funções
- Atenção para a exigência de leitura da **dimensão da stack**
- Apenas a operação de `pop` está a exigir a impressão no **console**, mas em fase de desenvolvimento pode ser útil imprimir o conteúdo da stack a cada operação.

# Exemplo de execução:

- Exemplo 1
```console
1 - Analise sintatica
3 - Sair
1
Informe o tamanho da stack: 10
Informe o nome do ficheiro a analisar: test.json
push {
push {
push [
pop  ]
pop  }
pop  }
FBF - Ficheiro bem formado!
1 - Analise sintatica
2 - Sair
2
```

- Exemplo 2
```console
1 - Analise sintatica
2 - Sair
1
Informe o tamanho da stack: 3
Informe o nome do ficheiro a analisar: experiencia.json
push }
push "
pop  "
push }
push "
pop  "
push }
push "
pop  "
push }
erro 01: stack overflow!
FMF - Ficheiro mal formado!

 1 - Analise sintatica
 2 - Sair
2
```

