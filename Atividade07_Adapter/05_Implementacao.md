# Exercício 5 – Implementação

Imagine que você foi contratado para integrar um módulo de previsão do tempo a dois sistemas externos diferentes.

A sua aplicação precisa consultar a temperatura em graus Celsius e não deve depender das classes dos fornecedores. Os fornecedores (SDKs de terceiros, que não podem ser alterados) são:

- `OpenWeatherApi` — expõe `public double temperatura(String cidade)` (retorna °C como `double`).
- `AccuWeatherApi` — expõe `public int getTemperature(String cidade)` (retorna °F como `int`).

## Sua missão

Implemente, em Java, um sistema que adapte os dois fornecedores a uma interface comum, usando o padrão Adapter.

**1.** Crie a interface do cliente `PrevisaoService`:
- Contrato: `int obterTemperatura(String cidade)` — sempre em °C.

**2.** Crie as classes dos fornecedores externos (como se fossem SDKs de terceiros, sem modificar):
- `OpenWeatherApi` com `public double temperatura(String cidade)`.
- `AccuWeatherApi` com `public int getTemperature(String cidade)`.

**3.** Crie os adaptadores:
- `OpenWeatherAdapter implements PrevisaoService`, que encapsula um `OpenWeatherApi` (o valor já vem em °C — converta `double` para `int` com `(int)`).
- `AccuWeatherAdapter implements PrevisaoService`, que encapsula um `AccuWeatherApi` e converte de °F para °C (`(fahrenheit - 32) * 5 / 9`).

**4.** Crie a classe `PainelClima` (o cliente):
- Recebe uma `PrevisaoService` (por exemplo, no construtor).
- Método `exibir(String cidade)` que imprime a temperatura usando apenas a interface.

**5.** Crie uma classe de teste, por exemplo `Main`, que:
- Crie um `PainelClima` com cada fornecedor (passando o adaptador correspondente) e mostre o resultado para uma cidade.
- Demonstre que o `PainelClima` não muda quando o fornecedor é trocado.
- Explique, em um comentário ou README, como adicionar um terceiro fornecedor exigiria apenas uma nova classe de adaptador, sem alterar o `PainelClima`.

---

## Anotações / código

*(cole aqui o código ou o link do repositório com a implementação)*
