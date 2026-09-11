# Exercício 2 – Analogia

Crie uma analogia própria para explicar o padrão Composite para alguém que não é da área de TI.

Na aula, usamos o organograma de uma empresa: um departamento contém funcionários ou sub-departamentos, e "quantas pessoas há abaixo de X" soma a árvore recursivamente. Agora crie uma outra analogia.

## Perguntas

Descreva uma situação do mundo real em que:
- exista uma hierarquia recursiva (uma "coisa" que pode conter outras, inclusive do mesmo tipo),
- seja natural tratar o todo e as partes da mesma forma (ex.: perguntar algo para o nó raiz resolve a estrutura inteira),
- e esse tratamento uniforme simplifique quem usa a estrutura.

*Resposta:*
Uma pasta de computador seria uma boa analogia. Uma pasta pode ter arquivo dentro ou outra pasta, que tambem pode ter mais pastas dentro dela. Quando eu pergunto pro sistema quantos MB tem uma pasta, ele soma tudo que tem la dentro recursivamente, sem eu precisar saber se é um arquivo direto ou uma pasta cheia de coisa. Isso facilita pq quem usa so pergunta pro nivel de cima e o resto se resolve sozinho.
