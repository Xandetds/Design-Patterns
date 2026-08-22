# Exercício 3 – Anti-pattern

Considere o código Java abaixo, usado em uma aplicação desktop de vendas:

```java
public class CarrinhoDeComprasSingleton {

    private static CarrinhoDeComprasSingleton instancia;
    private List<Item> itens = new ArrayList<>();

    private CarrinhoDeComprasSingleton() { }

    public static CarrinhoDeComprasSingleton getInstancia() {
        if (instancia == null) {
            instancia = new CarrinhoDeComprasSingleton();
        }
        return instancia;
    }

    public void adicionarItem(Item item) {
        itens.add(item);
    }

    public List<Item> getItens() {
        return itens;
    }

    // ...outros métodos de regras de negócio...
}
```

Em uma versão futura, essa aplicação passa a ser multiusuário (cada cliente loga com sua conta, possivelmente em paralelo).

## Perguntas

**1.** Por que esse uso de Singleton é um problema arquitetural nesse cenário?

*Resposta:*

Porque o correto seria cada cliente ter a sua propria instancia de carrinho, e nao terem carrinhos compartilhados.
---

**2.** Que tipo de bugs ou comportamentos estranhos podem acontecer quando vários usuários utilizarem o sistema ao mesmo tempo?

*Resposta:*
itens de uns clientes aparecendo do nada no carrinho dos outros

---

**3.** Sugira outra abordagem de design para o carrinho (sem usar Singleton) e explique, em linhas gerais, como as instâncias deveriam ser gerenciadas.

*Resposta:*
Criar somente uma instancia por cliente, entao seria um carrinho com sua instancia separado por cliente