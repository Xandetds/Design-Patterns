# Exercício 5 – Implementação

Imagine que você foi contratado para criar o sistema de veículos de uma concessionária.

O sistema precisa montar veículos combinando dois conceitos que evoluem de forma independente:
- o tipo de veículo (por exemplo, `Sedan` e `SUV`), e
- o tipo de motor (por exemplo, `MotorGasolina` e `MotorEletrico`).

Sem o padrão, cada combinação viraria uma classe nova (`SedanGasolina`, `SedanEletrico`, `SuvGasolina`…).

## Sua missão

Implemente, em Java, um sistema que separe as duas hierarquias, usando o padrão Bridge.

**1.** Crie a interface de implementação `Motor`:
- Métodos: `void ligar()` e `void acelerar()`.

**2.** Crie as implementações concretas:
- `MotorGasolina` e `MotorEletrico`, cada um imprimindo mensagens que identificam o motor.

**3.** Crie a classe abstrata `Veiculo` (a abstração):
- Um campo `protected Motor motor` (recebido no construtor).
- Métodos `void dirigir()` (liga o motor) e `void acelerar()` (delega ao motor).

**4.** Crie as abstrações refinadas:
- `Sedan` e `Suv`, que estendem `Veiculo` (cada uma pode imprimir o próprio tipo ao dirigir).

**5.** Crie uma classe de teste, por exemplo `Main`, que:
- Monte as quatro combinações (`Sedan` com `MotorGasolina`, `Sedan` com `MotorEletrico`, `Suv` com `MotorGasolina`, `Suv` com `MotorEletrico`) e as execute.
- Mostre que o mesmo veículo funciona com motores diferentes e que o mesmo motor funciona em veículos diferentes.
- Explique, em um comentário ou README, como adicionar um novo motor (ex.: `MotorHibrido`) ou um novo veículo (ex.: `Picape`) exigiria apenas uma nova classe, sem alterar o outro lado.

---

## Anotações / código

*(cole aqui o código ou o link do repositório com a implementação)*
