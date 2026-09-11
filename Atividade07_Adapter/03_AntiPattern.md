# Exercício 3 – Anti-pattern

Considere o código Java abaixo, usado por um módulo de clima da aplicação:

```java
public class PainelClima {

    public void exibirTemperatura(String cidade, String fornecedor) {
        if (fornecedor.equals("accuweather")) {
            AccuWeatherApi api = new AccuWeatherApi();
            int f = api.getTemperature(cidade);            // retorna °F
            int c = (f - 32) * 5 / 9;                       // conversão manual
            System.out.println("Temperatura: " + c + "°C");
        } else if (fornecedor.equals("openweather")) {
            OpenWeatherApi api = new OpenWeatherApi();
            double c = api.getTempCelsius(cidade);          // outra assinatura
            System.out.println("Temperatura: " + c + "°C");
        }
    }
}
```

Além desse painel, outros dois módulos da aplicação fazem a mesma consulta repetindo o mesmo código de conversão.

## Perguntas

**1.** Por que essa forma de chamar os fornecedores diretamente é um problema de design?

*Resposta:*
O PainelClima conhece e depende diretamente das classes concretas de cada fornecedor, AccuWeatherApi e OpenWeatherApi, cada uma com uma assinatura e um formato de retorno diferente. A lógica de conversão fica misturada com a lógica de exibição, dentro de um if/else baseado em string. Como outros dois módulos fazem a mesma consulta, esse código de conversão está duplicado em vários lugares, e qualquer mudança precisa ser replicada manualmente em todos.



---

**2.** Que tipo de bugs ou dificuldades aparecem quando um SDK de terceiros muda (por exemplo, passa a retornar °F) ou quando um novo fornecedor precisa ser adicionado?

*Resposta:*
Se o AccuWeather passar a retornar Celsius sem avisar, o código continua aplicando a fórmula de Fahrenheit para Celsius e mostra uma temperatura errada, sem nenhum erro de compilação. O bug só aparece quando alguém notar o valor estranho. Adicionar um fornecedor novo exige um novo else if em cada um dos três módulos que repetem esse código, com risco de esquecer de atualizar algum deles.



---

**3.** Proponha uma solução usando o padrão Adapter, explicando em linhas gerais: a interface do cliente, o(s) adaptador(es) por fornecedor e como o `PainelClima` passaria a depender apenas da interface.

*Resposta:*
Criar uma interface PrevisaoService com um método obterTemperatura, sempre em graus Celsius. Cada fornecedor ganha um adaptador, AccuWeatherAdapter e OpenWeatherAdapter, que encapsula o SDK correspondente e faz a conversão internamente, implementando essa interface. O PainelClima passa a receber um PrevisaoService pelo construtor e só chama obterTemperatura, sem saber qual fornecedor está por trás nem fazer conversão nenhuma. Os outros dois módulos reaproveitam os mesmos adaptadores, então a lógica de conversão passa a existir em um único lugar.

