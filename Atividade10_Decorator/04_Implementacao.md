# Exercício 4 – Implementação

Imagine que você foi contratado para criar o sistema de pedidos de uma cafeteria que acabou de abrir.

A casa serve uma bebida base (o café) e permite que o cliente combine complementos: leite, chantilly, calda de caramelo, entre outros. A equipe quer poder lançar novos complementos toda semana sem alterar a bebida base nem os complementos antigos.

## Sua missão

Implemente, em Java, um sistema de bebidas que some complementos dinamicamente, usando o padrão Decorator.

**1.** Crie a interface `Bebida` (o `Component`):
- Métodos: `String getDescricao()` e `double custo()`.

**2.** Crie o componente concreto `Cafe`:
- `getDescricao()` retorna `"Café"`.
- `custo()` retorna o preço base (ex.: `5.0`).

**3.** Crie o decorator abstrato `Complemento`:
- Um campo `protected final Bebida bebida` (recebido no construtor).
- Implementa a interface `Bebida` (pode deixar os métodos abstratos).

**4.** Crie os decorators concretos:
- `Leite`: soma `" com leite"` à descrição e `1.5` ao custo.
- `Chantilly`: soma `" com chantilly"` à descrição e `2.0` ao custo.
- Cada um recebe uma `Bebida` no construtor e delega ao objeto interno.

**5.** Crie uma classe de teste, por exemplo `Main`, que:
- Monte e imprima as combinações: um `Cafe` puro, um `Cafe` com `Leite`, e um `Cafe` com `Leite` e `Chantilly` (a ordem dos complementos deve ficar visível na descrição).
- Mostre que todas as combinações usam a mesma interface `Bebida` e que os custos somam camada por camada.
- Explique, em um comentário ou README, como adicionar um novo complemento (ex.: `CaldaDeCaramelo` por `+3.0`) exigiria apenas uma nova classe `Complemento`, sem alterar `Cafe`, `Leite` nem a `Main`.

---

## Anotações / código

*(cole aqui o código ou o link do repositório com a implementação)*
