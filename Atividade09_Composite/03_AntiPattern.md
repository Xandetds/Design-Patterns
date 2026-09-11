# Exercício 3 – Anti-pattern

Considere o código Java abaixo, usado em um sistema de pedidos de uma loja:

```java
public class Produto {
    String nome;
    double preco;
}

public class Caixa {           // pode conter produtos OU outras caixas
    String nome;
    List<Object> itens = new ArrayList<>();
}

public class Pedido {

    public double calcularTotal(Object item) {
        if (item instanceof Caixa c) {
            double soma = 0;
            for (Object filho : c.itens)
                soma += calcularTotal(filho);   // recursão "externa"
            return soma;
        } else if (item instanceof Produto p) {
            return p.preco;
        }
        return 0;
    }

    public void imprimir(Object item) {
        // ... de novo, um if para Caixa e outro para Produto ...
    }
}
```

## Perguntas

**1.** Por que calcular o total fora dos objetos, usando `instanceof`, é um problema de design? Onde mora a lógica da árvore e o que acontece se outro trecho do sistema precisar percorrer a mesma estrutura?

*Resposta:*
Porque a logica de somar fica fora dos objetos, na classe Pedido, usando instanceof pra saber o tipo. A logica da arvore mora no Pedido em vez de morar no proprio objeto, entao se outro lugar do sistema precisar percorrer a mesma estrutura (tipo pra imprimir), vai ter que reescrever o mesmo if/else de novo.

---

**2.** O que acontece ao adicionar um novo tipo (ex.: um `ProdutoComDesconto` ou um serviço de montagem)? Que bugs ou confusões esse código tende a gerar?

*Resposta:*
Se adicionar um ProdutoComDesconto, teria que colocar mais um else if em cada metodo que usa instanceof (calcularTotal, imprimir, etc), e é facil esquecer de atualizar algum deles, dando bug de nao contar o novo tipo direito.

---

**3.** Proponha uma solução usando o padrão Composite, explicando os papéis: a interface comum (`Component`), a folha (`Produto`) e o composto (`Caixa`). Onde a recursão passa a morar e por que o cliente passa a chamar um único método sem distinguir os tipos?

*Resposta:*
Criar uma interface Component com um metodo tipo getPreco(). Produto (folha) implementa e retorna o proprio preco. Caixa (composto) implementa somando o preco de cada item dela, chamando getPreco() de cada filho sem saber se é caixa ou produto. A recursao passa a morar dentro da propria Caixa, e o cliente so chama item.getPreco(), sem precisar de instanceof.
