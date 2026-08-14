# Exercício 3 – Liskov Substitution Principle (LSP)

Considere uma hierarquia de classes onde `Conta` é a classe base e `ContaCorrente`, `ContaPoupanca` e `ContaSalario` são subclasses.

A classe `Conta` possui os seguintes métodos:

- `sacar(Double valor)`: permite sacar o valor informado da conta, desde que haja saldo suficiente.
- `depositar(Double valor)`: permite depositar dinheiro na conta.
- `transferir(Double valor, Conta conta)`: permite transferir o valor informado para outra conta.

No entanto, devido a uma regra específica do sistema, a classe `ContaSalario` sobrescreve os métodos `sacar` e `transferir`. Nessa classe, essas operações não realizam a operação solicitada diretamente: o valor movimentado é automaticamente direcionado para uma conta específica vinculada ao empregador.

## Perguntas

**1.** Explique, com suas palavras, quando uma subclasse viola o Princípio da Substituição de Liskov (LSP).

*Resposta:*
Quando uma classe filha de outra não esta ou nao pode implementar uma funcao que a classe pai dela implementa

---

**2.** Descreva um cenário de uso em que `ContaSalario` poderia causar um comportamento inesperado ou incorreto ao ser utilizada onde o sistema esperava receber uma `Conta` genérica.

*Resposta:*
Supondo que eu tentei sacar um valor da conta salario, mas nao consigo pq de acordo com as regras do sistema, essas sao realiadas de forma diferente.

---

**3.** Explique por que o problema apresentado está relacionado ao comportamento esperado da classe, e não simplesmente à existência dos mesmos métodos na classe filha.

*Resposta:*
O problema se encontra na questao de que quando eu quero sacar dinheiro, eu espero que o valor fique disponivel para mim, e nao que ele va automaticamente para uma conta separada vinculada a ela.