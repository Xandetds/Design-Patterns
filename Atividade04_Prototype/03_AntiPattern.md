# Exercício 3 – Anti-pattern

Considere o código Java abaixo, usado em um jogo para criar os inimigos de cada fase:

```java
public class Fase {
    private Inimigo criarCopia(Inimigo antigo) {
        Inimigo copia = new Inimigo();
        copia.setTipo(antigo.getTipo());
        copia.setVida(antigo.getVida());
        copia.setDano(antigo.getDano());
        copia.setArma(antigo.getArma());
        return copia;
    }
}

public class Inimigo {
    private String tipo;
    private Double vida;
    private Double dano;
    private Arma arma; // Arma é um objeto mutável com nome e bônus de dano

    // getters e setters...
}
```

## Perguntas

**1.** Por que essa forma de copiar campo a campo é um problema de design?

*Resposta:*
Porque quem for utilizar a copia precisaria antes saber toda a estrutura interna da classe, e utilizar diretamente todos os setters e getters, além disso, qualquer campo que eu adicionar novo em inimigo, eu teria que alterar também manualmente a cópia.
---

**2.** Que tipo de bugs ou comportamentos estranhos podem acontecer se um novo campo for adicionado a `Inimigo` e o `criarCopia` não for atualizado?

*Resposta:*
Uma variavel da classe inimigo pode virar null, false, ou ficar com o valor padrão, podendo gerar um null pointer exception, ou compilando normal até a hora que o inimigo vá utilizar a variavel realmente.


---

**3.** Observe `copia.setArma(antigo.getArma())`. O que acontece se o clone compartilhar a mesma instância de `Arma` do original e o jogo modificar a arma de um deles? Qual conceito visto em aula isso ilustra (cópia rasa × profunda)?

*Resposta:*
Os dois teriam que utilizar a exata mesma arma, o que é possível, mas pode gerar situações onde caso a arma de um inimigo quebre ou seja buffada, a do com a arma clonada também é sem que tenha sido feito nada para ele.