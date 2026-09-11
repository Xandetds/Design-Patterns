# Exercício 4 – Implementação

Imagine que você foi contratado para criar o sistema de cardápio e comandas de um restaurante.

A casa vende pratos individuais e combos promocionais. Um combo pode conter pratos individuais e também outros combos (por exemplo, um "Combo Família" que inclui o "Combo Duplo" dentro dele). Sem o padrão, calcular o preço de um combo exigiria distinguir, item a item, se é um prato ou um sub-combo.

## Sua missão

Implemente, em Java, um sistema que trate pratos e combos de forma uniforme, usando o padrão Composite.

**1.** Crie a interface `ItemMenu` (o `Component`):
- Métodos: `String getNome()` e `double getPreco()`.

**2.** Crie a folha `Prato`:
- Campos `nome` e `preco` (recebidos no construtor).
- `getPreco()` retorna o preço do prato.

**3.** Crie o composto `Combo`:
- Campo `nome` e uma lista de `ItemMenu` (filhos).
- Métodos `adicionar(ItemMenu item)` e `remover(ItemMenu item)`.
- `getPreco()` deve somar recursivamente o preço dos filhos.
- `getNome()` devolve o nome do combo.

**4.** Crie uma classe de teste, por exemplo `Main`, que:
- Monte pratos (ex.: `Hamburguer`, `BatataFrita`, `Refrigerante`) com preços.
- Monte um `Combo Duplo` contendo dois hambúrgueres e um refrigerante.
- Monte um `Combo Família` contendo o `Combo Duplo` dentro dele, mais batatas e refrigerantes.
- Imprima o preço de um prato isolado, do combo duplo e do combo família, sempre chamando o mesmo método `getPreco()` sobre a interface `ItemMenu`.
- Mostre que o preço do combo família já inclui o preço do sub-combo (recursão).
- Explique, em um comentário ou README, como adicionar um novo tipo de item (ex.: `BebidaAlcoolica` com imposto especial) exigiria apenas uma nova folha, sem alterar o `Combo` nem a `Main`.

---

## Anotações / código

*(cole aqui o código ou o link do repositório com a implementação)*
