# Exercício 4 – Exemplo real

Acesse o seguinte arquivo em um projeto open source:

- **Projeto:** OkHttp (biblioteca HTTP para Java/Kotlin)
- **Arquivo:** [`Request.kt`](https://github.com/lysine-dev/okhttp/blob/main/okhttp/src/commonJvmAndroid/kotlin/okhttp3/Request.kt)

O OkHttp é uma das bibliotecas mais utilizadas para requisições HTTP em Java/Kotlin. A classe `Request` representa uma requisição HTTP imutável a partir do momento em que é criada.

## Perguntas

**1.** Procure explicar, em linhas gerais, por que a classe `Request` é imutável e qual o papel do seu `Builder` nessa garantia.

*Resposta:*
Os campos de Request são val e o construtor é internal, só acessível pelo próprio Builder. O Builder guarda os campos var durante a montagem; só quando build() é chamado os valores são copiados pra dentro do Request, que depois disso não muda mais.

---

**2.** Observe os métodos de configuração da classe `Builder` (por exemplo, `url(...)`, `header(...)`, `method(...)`, `get()`, `post(body)`). O que esses métodos têm em comum no tipo de retorno e por que isso permite o encadeamento fluente visto em aula?

*Resposta:*
Todos retornam Builder via applu. Como cada método devolve o Builder, dá pra encadear várias chamadas seguidas, tipo Builder().url(...).header(...).get().build().

---

**3.** Analise o método `build()` e as verificações feitas nesse exemplo (por exemplo, `checkNotNull(builder.url)`). Relacione esse comportamento com a validação de campos obrigatórios do `build()` visto em aula.

*Resposta:*
build() chama Request(this), e dentro do construtor de Request, checkNotNull(builder.url) lança exceção se a URL não foi definida. build() valida os campos obrigatórios antes de criar o objeto final, garantindo que ele nunca exista em estado inválido.

---

**4.** O `Builder` desse exemplo é uma classe interna. Compare com o que foi apresentado na aula sobre Builder interno `static` e comente se a relação entre o `Builder` e o produto final é a mesma que você aprendeu.

*Resposta:*
Sim, é a mesma relação. Builder é uma classe aninhada dentro de Request (equivalente a uma nested/static class do Java, já que em Kotlin classes aninhadas não são inner por padrão), com acesso aos campos internos de Request e responsável por construí-lo, igual ao padrão construtor privado + Builder interno estático visto em aula.
