# Exercício 4 – Interface Segregation Principle (ISP)

Suponha uma interface `ITrabalhador` com os métodos: `trabalhar()`, `comer()`, `dormir()`. Ela é implementada por `Robo` e `Funcionario`.

## Perguntas

**1.** Explique por que essa interface pode violar o ISP.

*Resposta:*
Porque por mais que um trabalhador trabalhe, se ele for um robo, ele nao precisa comer ou dormir.

---

**2.** Proponha um conjunto de interfaces menores que segregue melhor as responsabilidades.

*Resposta:*
Uma interface humano que come e dorme, e uma interface trabalhador que trabalha.

O funcionario implementaria as duas e o robo so a de funcionario.


---

**3.** Escreva a nova definição dessas interfaces em pseudocódigo (ou sintaxe de alguma linguagem OO) e indique quais seriam implementadas por `Robo` e por `Funcionario`.

*Resposta:*
Public Interface ITrabalhador {
    void trabalhar();
}

Public Interface ISerVivo {
    void comer();
    void dormir();
}

Public class Robo implements ITrabalhador {
        void trabalhar(){};
}

Public class Funcionario implements ITrabalhador, ISerVivo {
    void comer(){};
    void dormir(){};
    void trabalhar(){};
}

