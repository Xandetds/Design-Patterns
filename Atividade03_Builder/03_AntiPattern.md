# Exercício 3 – Anti-pattern

Considere o código Java abaixo, usado em uma aplicação de e-commerce:

```java
public class Pedido {

    private final String cliente;
    private final String endereco;
    private final List<String> itens;
    private final double desconto;
    private final String cupom;
    private final double frete;
    private final String observacoes;

    public Pedido(String cliente) { ... }
    public Pedido(String cliente, String endereco) { ... }
    public Pedido(String cliente, String endereco, List<String> itens) { ... }
    public Pedido(String cliente, String endereco, List<String> itens, double desconto) { ... }
    public Pedido(String cliente, String endereco, List<String> itens, double desconto, String cupom) { ... }
    public Pedido(String cliente, String endereco, List<String> itens, double desconto, String cupom, double frete, String observacoes) { ... }

    // ...outros métodos de regras de negócio...
}
```

## Perguntas

**1.** Por que esse uso de construtores sobrecarregados (telescópicos) é um problema de design?

*Resposta:*
Porque cada vez que uma nova combinacao for possivel de ser criada, um novo construtor tera que ser criado. Alem disso, o codigo fica grande e feio.

---

**2.** Que tipo de bugs ou confusões podem acontecer quando um desenvolvedor cria um `Pedido` chamando esses construtores?

*Resposta:*
Como varios parametros podem ser variaveis de mesmo tipo, a ordem deles poderia ser trocada sem acusar erros, e tambem fica dificil ler o codigo
---

**3.** O que acontece com esse código a cada novo campo opcional adicionado à `Pedido`? Quantos construtores seriam necessários para `N` campos opcionais?

*Resposta:*
Todos os construtores teriam que ser analisados e passiveis de alteracao, alem de novos construtores tendo sido criados para cada nova variavel.

---

**4.** Sugira outra abordagem de design usando o padrão Builder e explique, em linhas gerais, como a criação do objeto passaria a funcionar (construtor privado, Builder interno, métodos fluentes e `build()`).

*Resposta:*

Em vez de vários construtores, Pedido teria um construtor privado, chamado só pelo Builder. O Pedido.Builder guardaria os mesmos campos, com métodos como setCliente setEndereco, setDesconto cada um retornando o próprio Builder (this), permitindo encadear as chamadas. Ai o build chama esse construtor privado com esses valores.