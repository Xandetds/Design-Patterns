# Exercício 2 – Analogia

Crie uma analogia própria para explicar o padrão Bridge para alguém que não é da área de TI.

Na aula, usamos o carro e o motor: dirigir um carro não depende do motor (combustão ou elétrico), o carro delega a força ao motor, e carros e motores evoluem independentes. Agora crie uma outra analogia.

## Perguntas

**1.** Descreva uma situação do mundo real em que:
- existam duas "famílias" que precisam ser combinadas de muitas formas,
- combinar tudo de uma vez por "duplicação" seja inviável,
- e cada família possa evoluir separadamente, com as combinações feitas na hora (composição).

*Resposta:*
Um restaurante tem pratos, peixe, frango, carne, e métodos de preparo, grelhado, frito, assado, no vapor. Sem Bridge, seria preciso uma receita fixa para cada combinação, PeixeGrelhado, FrangoFrito, CarneAssada, o que explode rápido. Em vez disso, o prato, a abstração, simplesmente delega o preparo ao método escolhido, a implementação, e o cozinheiro combina os dois na hora. Adicionar um prato novo, camarão, não mexe nos métodos de preparo, e um método novo, defumado, não mexe nos pratos: as duas famílias evoluem soltas, e a combinação é montada por composição, não por uma classe nova.

Limitação: na vida real nem toda combinação faz sentido, peixe cru não é bem um método de preparo, enquanto no código, tecnicamente, qualquer combinação de abstração e implementação compila.


