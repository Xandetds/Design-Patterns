# Exercício 5 – Implementação

Imagine que você foi contratado para criar o sistema de montagem de lanches de uma lanchonete.

O sistema precisa montar lanches passo a passo, permitindo:
- escolher o pão (obrigatório),
- escolher a proteína (obrigatória),
- e adicionar itens opcionais: queijo, vegetais, molhos, ponto da carne (`bemPassado`) e observações.

Como as combinações são muitas, usar um construtor gigante ou vários construtores sobrecarregados deixaria o código ilegível.

## Sua missão

Implemente, em Java, um sistema que monte lanches de forma fluente e passo a passo, usando o padrão Builder.

**1.** Crie a classe `Lanche` que seja o Produto:
- Campos obrigatórios: `pao` e `proteina`.
- Campos opcionais: `queijo`, `vegetais`, `molho`, `bemPassado` e `observacoes`.
- Construtor privado — apenas o Builder instancia o objeto.
- Métodos `get` para leitura dos campos (sem `set`, o objeto é imutável).

**2.** Crie a classe interna estática `Lanche.Builder`:
- Métodos de configuração fluentes (por exemplo, `setPao(...)`, `setProteina(...)`, `setQueijo(...)`, `addVegetal(...)`, `setMolho(...)`, `setBemPassado(...)`) que retornam o próprio `Builder`.
- Um método `build()` que valida os campos obrigatórios (`pao` e `proteina`) e lança `IllegalStateException` caso algum esteja ausente.

**3.** Crie uma classe `LancheDirector` com pelo menos três variações de lanche (por exemplo, `criarMisto()`, `criarXSalada()` e `criarEspecialDaCasa()`) reutilizando o Builder.

**4.** Crie uma classe de teste, por exemplo `Main`, que:
- Monte lanches pela API fluente, alguns apenas com os campos obrigatórios e outros com várias opções.
- Gere lanches através do Director e imprima a descrição de cada um.
- Tente montar um lanche sem informar um campo obrigatório e mostre que o `build()` lança a exceção de validação.

---

## Anotações / código

*(cole aqui o código ou o link do repositório com a implementação)*
