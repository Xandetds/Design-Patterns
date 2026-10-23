# Exercício 1 – Aplicações

Para cada cenário abaixo, indique se o padrão Command é apropriado ou não e justifique em 2–3 frases.

Para cada item, responda:
- "Faz sentido usar Command" ou "Não faz sentido usar Command".
- Explique rapidamente o porquê (requisição como objeto, fila/agendamento, undo/redo, parâmetros variáveis, operação única e estável, overengineering, etc.).

## Perguntas

**1.** Uma barra de ferramentas de um editor em que cada botão dispara uma ação e o usuário precisa de desfazer/refazer, sem que a barra conheça os detalhes das operações.

*Resposta:*
Faz sentido. Cada botão aciona um Comando, uma requisição encapsulada como objeto, a barra não precisa saber a lógica de cada operação, só chamar executar e desfazer.

---

**2.** Um agendador de tarefas que precisa enfileirar jobs, executá-los depois e, às vezes, cancelá-los antes da execução.

*Resposta:*
Faz sentido. Cada job vira um Comando guardado numa fila, o agendador só manipula objetos Comando, podendo executá-los ou removê-los antes de rodar, sem acoplar ao código de cada tarefa.

---

**3.** Um sistema de macros em que o usuário grava uma sequência de ações e a repete como se fosse um único comando.

*Resposta:*
Faz sentido. É o caso clássico de comando composto: uma lista de comandos executados em sequência se comporta como um único comando macro.

---

**4.** Uma classe `Relatorio` que sempre gera o mesmo PDF, com um fluxo único e fixo, sem fila, parametrização nem necessidade de desfazer.

*Resposta:*
Não faz sentido. Sem variação de parâmetros, fila ou necessidade de desfazer, encapsular como Comando é overengineering, um método direto resolve.

---

**5.** Uma classe `Ponto` com apenas `x` e `y`, que só soma coordenadas por um método simples e nunca precisa reverter a operação.

*Resposta:*
Não faz sentido. Operação simples e estável, sem necessidade de desfazer ou enfileirar, não justifica a estrutura do Command.
