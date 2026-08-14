# Exercício 2 – Open/Closed Principle (OCP)

Imagine um sistema de cálculo de frete onde existe uma classe `CalculadoraFrete` com um `switch`/`if-else` interno que decide o valor com base no tipo de entrega: Normal, Rápida, Expressa.

**CalculadoraFrete.java**

```java
public class CalculadoraFrete {

    public double calcularFrete(String tipoEntrega, double peso) {
        switch (tipoEntrega) {
            case "Normal":
                return peso * 5.0;
            case "Rápida":
                return peso * 10.0;
            case "Expressa":
                return peso * 20.0;
            default:
                throw new IllegalArgumentException("Tipo de entrega desconhecido: " + tipoEntrega);
        }
    }
}
```

A empresa deseja adicionar novos tipos de entrega (por exemplo, Entrega Noturna, Entrega Internacional) sem precisar modificar o código existente.

## Perguntas

**1.** Explique quais problemas o código atual apresenta em relação ao OCP.

*Resposta:*
Para adicionar esses novos tipos de entrega, teriamos que mexer no switch case da classe. Caso ele esteja sendo usado em mais de um lugar, teriamos que mexer tambem em todas essas implementações, e poderia dar problema por deixar uma delas pra tras.

---

**2.** Proponha uma implementação criando uma interface chamada `TipoEntrega` e classes concretas para cada tipo de entrega, de forma que cada tipo de entrega tenha um método `calcularFrete(double peso)`.

*Resposta:*
public interface TipoEntrega {
    double calcularFrete(double peso);
}

public class EntregaNormal implements TipoEntrega {
    @Override
    public double calcularFrete(double peso) {
        return peso * 5.0;
    }
}

public class EntregaRapida implements TipoEntrega {
    @Override
    public double calcularFrete(double peso) {
        return peso * 10.0;
    }
}

public class EntregaExpressa implements TipoEntrega {
    @Override
    public double calcularFrete(double peso) {
        return peso * 20.0;
    }
}

public class CalculadoraFrete {
    public double calcularFrete(TipoEntrega tipoEntrega, double peso) {
        return tipoEntrega.calcularFrete(peso);
    }
}