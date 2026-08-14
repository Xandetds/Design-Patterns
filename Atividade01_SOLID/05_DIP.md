# Exercício 5 – Dependency Inversion Principle (DIP)

Um módulo de alto nível `ProcessadorDePagamento` instancia diretamente uma classe concreta `PagInseguro` usando `new` e chama seus métodos em todos os métodos (ex.: `processarPagamento()`, `verificarPagamento()`, `cancelarPagamento()`).

## Perguntas

**1.** Explique por que isso fere o DIP.

*Resposta:*
Porque o ProcessadorDePagamento (alto nível) depende da implementação concreta PagInseguro ( baixo nível), em vez de depender de uma abstração. O DIP diz que ambos deveriam depender de uma interface, e não que o de alto nível dependa dos detalhes do de baixo nível.

---

**2.** Quais seriam as consequências de manter essa dependência direta em termos de manutenção e evolução do sistema?

*Resposta:*
Fica difícil trocar de gateway de pagamento sem alterar o ProcessadorDePagamento; fica difícil testar, já que não dá pra mockar o PagInseguro em um teste, qualquer mudança na classe concreta pode quebrar o módulo de alto nível e o código fica mais caro de evoluir.

---

**3.** Descreva brevemente por quais maneiras o desenvolvedor poderia injetar a implementação concreta.

*Resposta:*
Criando uma interface IGatewayPagamento que PagInseguro implementa, e passando a instância pronta de fora, em vez do ProcessadorDePagamento fazer new PagInseguro() internamente. Isso pode ser feito por injeção via construtor, injeção via setter, algo tipo um setGateway(...) define a dependência depois de criado o objeto, injeção via parâmetro de método, ou usando um framework de injeção de dependência tipo o spring.
