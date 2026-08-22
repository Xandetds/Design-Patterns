# Exercício 4 – Exemplo real

Acesse o seguinte arquivo em um projeto open source:

- **Projeto:** Apache Spark
- **Arquivo:** [`JavaRecoverableNetworkWordCount`](https://github.com/apache/spark/blob/2572d806923a9cb5f2094a822d4fba9df979685b/examples/src/main/java/org/apache/spark/examples/streaming/JavaRecoverableNetworkWordCount.java)

O Apache Spark é um framework de processamento distribuído de dados em larga escala. No arquivo indicado, há uma classe que implementa um contador de palavras que pode ser recuperado após falhas.

## Perguntas

**1.** Procure explicar, em linhas gerais, quais funcionalidades estão implementadas nesse exemplo.

*Resposta:*

contador de palavra via streaming, recebendo texto por socket. quer recuperar o StreamingContext após falha, usando checkpoint. Broadcast e Accumulator são Singleton pra serem re-registrados na recuperação.

---

**2.** Quais as classes presentes nesse arquivo que podem ser consideradas Singletons, como vimos em aula? Justifique sua resposta.

*Resposta:*
JavaWordExcludeList e JavaDroppedWordsCounter. Elas sao as singleton pq sao as que tem um getINstance implementado, usando um lazy initialization

---

**3.** As soluções apresentadas no código são thread-safe? Explique o porquê.

*Resposta:*

Sim, por conta do synchronized, as threads todas terão a mesma estancia sincronizada, sem ter chance de duplicar sem querer. o volatile evita a reordenacao de instrucoes

---

**4.** Por que há duas verificações de `if (instance == null)` no método `getInstance()`? Podemos considerar essa estratégia desperdício de recursos? Justifique sua resposta.

*Resposta:*

Não é um desperdicio. Primeira checagem evita synchronized desnecessário depois que a instância já existe. Segunda evita duas threads criando a instância ao mesmo tempo.