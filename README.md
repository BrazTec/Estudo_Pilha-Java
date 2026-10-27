# Anotações de Java: pilha em array

Estudo de uma pilha genérica com capacidade fixa. A regra é **LIFO**: o último elemento inserido é o primeiro removido.

## Estrutura

| Arquivo | Responsabilidade |
| --- | --- |
| `Pilha/Stack.java` | Interface das operações da pilha |
| `Pilha/ArrayStack.java` | Implementação em um arranjo genérico |
| `Pilha/EmptyStackException.java` | Erro ao consultar/remover de pilha vazia |
| `Pilha/FullStackException.java` | Erro ao inserir em pilha cheia |
| `Pilha/testes/ArrayStackTest.java` | Teste com JUnit Jupiter (JUnit 5) |

## Como o código funciona

`top` começa em `-1`, indicando pilha vazia. `size()` retorna `top + 1`.

- `push(element)`: verifica capacidade e grava em `S[++top]`.
- `top()`: consulta o topo sem remover.
- `pop()`: retorna o topo, limpa sua referência no array e decrementa o índice.
- `toString()`: percorre da base ao topo, não na ordem de remoção.

O construtor sem argumentos usa capacidade 1000; o outro recebe a capacidade. O array não cresce automaticamente. As operações principais são O(1); a representação textual percorre os elementos.

## Compilação e testes

É necessário um JDK. Na raiz do repositório, compile apenas a implementação:

```sh
javac -encoding UTF-8 -d build Pilha/Stack.java Pilha/ArrayStack.java Pilha/EmptyStackException.java Pilha/FullStackException.java
```

Não há método `main`. Para executar `ArrayStackTest`, adicione JUnit Jupiter ao ambiente da IDE e execute a classe de teste. Não há configuração Maven/Gradle nem dependências de teste incluídas.

O teste existente usa capacidade 3, verifica inserções, remoções, representação textual e exceções de pilha cheia/vazia. Isso não equivale a cobertura de todos os casos; por exemplo, capacidades inválidas não são validadas explicitamente pelo construtor.

## Roteiro de estudo

Acompanhe `push(7)`, `push(9)`, `pop()`: o resultado removido é 9 e o topo volta a ser 7. Compare o contrato `Stack<E>` com sua implementação e observe o uso de genéricos e exceções.

A interface original atribui autoria a Roberto Tamassia e Michael Goodrich; essa atribuição foi preservada no fonte. Este repositório é material didático.
