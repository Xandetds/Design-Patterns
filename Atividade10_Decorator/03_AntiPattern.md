# Exercício 3 – Anti-pattern

Considere o código Java abaixo, usado na tela de pedidos de uma cafeteria:

```java
public class Cafe {
    boolean comLeite;
    boolean comChantilly;
    boolean comCanela;

    public double custo() {
        double total = 5.0;
        if (comLeite) total += 1.5;
        if (comChantilly) total += 2.0;
        if (comCanela) total += 0.5;
        return total;
    }

    public String getDescricao() {
        String descricao = "Café";
        if (comLeite) descricao += " com leite";
        if (comChantilly) descricao += " com chantilly";
        if (comCanela) descricao += " com canela";
        return descricao;
    }
}
```

## Perguntas

**1.** Por que modelar os complementos como flags booleanas dentro de `Cafe` é um problema de design? O que acontece com essa classe a cada novo complemento (ex.: café com caramelo)?

*Resposta:*
Porque toda vez que aparece um complemento novo tem que mexer direto na classe Cafe, adicionando mais um boolean e mais um if em cada metodo (custo e getDescricao). A classe cresce a cada complemento novo em vez de só adicionar algo por fora dela.

---

**2.** Que bugs e confusões esse código tende a gerar (ex.: esquecer de atualizar um dos métodos, combinações que fazem sentido juntas, comportamentos que não são só "somar preço")?

*Resposta:*
É facil esquecer de atualizar um dos dois metodos quando adiciona um boolean novo, tipo colocar o if no custo() e esquecer no getDescricao(), ai a descricao fica errada mesmo cobrando certo. Tambem fica dificil lidar com complemento que faz mais que só somar preco, tipo um que muda o preco dependendo da combinacao com outro.

---

**3.** Proponha uma solução usando o padrão Decorator, explicando os papéis: a interface (`Bebida`), o componente concreto (`Cafe`), o decorator abstrato e os decorators concretos (`Leite`, `Chantilly`). Como as combinações passam a ser montadas sem tocar na classe `Cafe`?

*Resposta:*
Cria uma interface Bebida com getDescricao() e custo(). Cafe implementa e retorna os valores base. Cria um decorator abstrato Complemento que tambem implementa Bebida e guarda uma Bebida dentro dele. Cada complemento concreto (Leite, Chantilly) extende Complemento, chama o metodo da bebida de dentro e soma o que falta (preco e descricao). Assim pra combinar é só ir embrulhando uma Bebida dentro da outra, sem precisar tocar na classe Cafe pra cada complemento novo.
