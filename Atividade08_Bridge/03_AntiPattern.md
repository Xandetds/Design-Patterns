# Exercício 3 – Anti-pattern

Considere o código Java abaixo, usado em um editor gráfico:

```java
public abstract class Forma {
    public abstract void desenhar();
}

public class CirculoVermelho extends Forma {
    @Override
    public void desenhar() {
        System.out.println("Desenhando círculo vermelho");
        // lógica de desenhar círculo + lógica da cor vermelho
    }
}

public class CirculoAzul extends Forma {
    @Override
    public void desenhar() {
        System.out.println("Desenhando círculo azul");
        // mesma lógica de círculo, cor azul
    }
}

public class QuadradoVermelho extends Forma {
    @Override
    public void desenhar() {
        System.out.println("Desenhando quadrado vermelho");
    }
}

public class QuadradoAzul extends Forma {
    @Override
    public void desenhar() {
        System.out.println("Desenhando quadrado azul");
    }
}
```

## Perguntas

**1.** Por que essa hierarquia (uma classe por combinação de forma × cor) é um problema de design?

*Resposta:*
Cada combinação de forma e cor vira uma classe própria, mesmo forma e cor sendo conceitos independentes. A lógica de desenhar círculo se repete em duas classes diferentes, só variando a cor, o que é duplicação desnecessária, crescendo por uma relação de herança que não devia existir entre tipo de forma e cor.



---

**2.** O que acontece ao adicionar uma nova forma (ex.: `Triangulo`) ou uma nova cor (ex.: `Verde`)? Quantas classes existiriam para `N` formas e `M` cores?

*Resposta:*
Cada forma nova precisa de uma classe para cada cor já existente, e cada cor nova precisa de uma classe para cada forma já existente. No total, para N formas e M cores, seriam N vezes M classes, um crescimento multiplicativo.



---

**3.** Proponha uma solução usando o padrão Bridge, explicando em linhas gerais: as duas hierarquias (forma e cor), como a `Forma` passaria a referenciar uma `Cor` e por que cada lado passaria a evoluir de forma independente.

*Resposta:*
Duas hierarquias separadas: Forma, a abstração, com Circulo e Quadrado, e Cor, a implementação, com Vermelho, Azul, Verde. A Forma passaria a guardar uma referência a uma Cor, por composição, recebida no construtor, e delegaria a ela a aplicação da cor ao desenhar, em vez de cada forma saber desenhar a própria cor. Assim, forma nova não mexe em cor, cor nova não mexe em forma, e cada combinação é montada na hora, sem precisar de mais uma classe.


