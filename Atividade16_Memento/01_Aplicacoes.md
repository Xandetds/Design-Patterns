# Exercício 1 – Aplicações

Para cada cenário abaixo, indique se o padrão Memento é apropriado ou não e justifique em 2–3 frases.

Para cada item, responda:
- "Faz sentido usar Memento" ou "Não faz sentido usar Memento".
- Explique rapidamente o porquê (guardar/restaurar estado, encapsulamento, undo/redo, estado único e imutável, overengineering, etc.).

## Perguntas

**1.** Um jogo em que o jogador salva checkpoints do progresso e pode voltar ao ponto salvo após perder, sem que o sistema de save conheça os atributos internos do jogo.

*Resposta:*
Faz sentido. É o caso central do Memento: o Jogo, o originator, gera e restaura o próprio estado, e o sistema de save, o caretaker, guarda os checkpoints sem enxergar os campos internos.

---

**2.** Um editor de texto que precisa oferecer desfazer/refazer, restaurando o estado anterior do documento a cada passo.

*Resposta:*
Faz sentido. Cada estado do documento vira um memento guardado numa pilha de histórico, e desfazer é só restaurar o memento anterior.

---

**3.** Um formulário em várias etapas (wizard) em que o usuário pode voltar a um passo anterior e retomar exatamente os dados de então.

*Resposta:*
Faz sentido. Cada etapa pode gerar um memento do formulário até aquele ponto, e voltar é restaurar o memento daquele passo, sem o wizard conhecer a estrutura interna de cada etapa.

---

**4.** Uma classe `Configuracao` lida uma única vez por um único consumidor fixo, sem histórico e sem necessidade de voltar a estados anteriores.

*Resposta:*
Não faz sentido. Sem necessidade de voltar a um estado anterior, Memento seria overengineering, um objeto imutável simples já resolve.

---

**5.** Uma classe `Ponto`, com apenas `x` e `y`, que só guarda coordenadas e nunca precisa restaurar um estado passado.

*Resposta:*
Não faz sentido. Não há histórico nem necessidade de desfazer, guardar mementos seria overhead sem benefício.
