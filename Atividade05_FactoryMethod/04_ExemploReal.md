# Exercício 4 – Exemplo real

Acesse os seguintes arquivos em um projeto open source:

- **Projeto:** [`iluwatar/java-design-patterns`](https://github.com/iluwatar/java-design-patterns) (um dos repositórios de padrões de projeto mais populares do GitHub)
- **Arquivos:**
  - [`Blacksmith.java`](https://github.com/iluwatar/java-design-patterns/blob/master/factory-method/src/main/java/com/iluwatar/factory/method/Blacksmith.java)
  - [`ElfBlacksmith.java`](https://github.com/iluwatar/java-design-patterns/blob/master/factory-method/src/main/java/com/iluwatar/factory/method/ElfBlacksmith.java)

Esse exemplo implementa o Factory Method com ferreiros (blacksmiths): a interface `Blacksmith` declara o método fábrica `manufactureWeapon(...)`, e cada ferreiro concreto (como o `ElfBlacksmith`, ou o `OrcBlacksmith` do mesmo pacote) decide qual arma criar. É a mesma estrutura vista em aula com a `Logistica` e o método `criarTransporte()`.

## Perguntas

**1.** Que papel a interface `Blacksmith` exerce no padrão? Qual é o método fábrica declarado nela e qual o seu tipo de retorno?

*Resposta:*
Declarar que todas as classes que implementam ela devem ter o metodo manufactureWeapon. É um metodo que sempre irá retornar uma Weapon que o blacksmith criou.

---

**2.** No `ElfBlacksmith`, o que o método `manufactureWeapon(...)` retorna? Por que o tipo de retorno é a interface `Weapon` e não a classe concreta (`ElfWeapon`)?

*Resposta:*
Vai retornar ElfWeapon, pois foi mapeado em cima do codigo que o tipo de arma para ELFARSENAL é ElfWeapon. Ele tem o tipo de retorno Weapon pois é o tipo de retorno que a classe pai (Blacksmith) retorna, fazendo com que a classe main não precise conhecer todos os tipos de arma.

---

**3.** O cliente do exemplo (a classe `App` do mesmo pacote) trabalha com `Blacksmith` e `Weapon` — abstrações — e troca de ferreiro (elfo ou orc). O que seria necessário para adicionar um novo ferreiro (por exemplo, um anão) sem alterar o código que usa as armas? Relacione com o princípio OCP.

*Resposta:*
Criarmos uma nova classe que implementa blacksmith e segue a mesma logica das outras, retorna uma arma do tipo da raça do ferreiro, utilizando o metodo manufactureWeapon, isso se relaciona com o OCP pois não estamos alterando nenhuma classe já criada, apenas fazendo uma nova.