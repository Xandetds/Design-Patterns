# Exercício 1 – Aplicações

Para cada cenário abaixo, indique se o padrão Composite é apropriado ou não e justifique em 2–3 frases.

Para cada item, responda:
- "Faz sentido usar Composite" ou "Não faz sentido usar Composite".
- Explique rapidamente o porquê (estrutura recursiva parte-todo, tratamento uniforme, lista plana, overengineering, etc.).

## Perguntas


**1.** Um explorador de arquivos que precisa listar e calcular o tamanho de pastas, que podem conter arquivos ou outras pastas (estrutura recursiva).

*Resposta:*
Faz sentido, pq pasta pode ter arquivo ou outra pasta dentro, entao é uma estrutura recursiva parte-todo, e da pra tratar os dois da mesma forma na hora de calcular o tamanho.

---

**2.** Um cardápio digital de um restaurante em que seções podem conter itens de cardápio ou outras subseções, e o total de calorias de uma seção deve somar todos os itens abaixo dela.

*Resposta:*
Faz sentido, secao pode ter item ou outra subsecao, entao é a mesma logica de arvore, cada nivel soma o que tem embaixo dele.

---

**3.** Um motor de interface gráfica em que um painel pode conter controles simples (botões, rótulos) ou outros painéis aninhados, e o sistema precisa desenhar/ocultar qualquer elemento da mesma forma.

*Resposta:*

Faz sentido, painel pode ter controle ou outro painel dentro, e o sistema desenha ou esconde botao e painel do mesmo jeito, sem precisar saber qual é qual.
---

**4.** Um cadastro de produtos com uma lista simples e plana (nome, preço, estoque) que nunca terá itens compostos ou hierarquia.

*Resposta:*
Nao faz sentido. É uma lista plana, sem hierarquia nem item composto, usar composite ali seria overengineering.

---

**5.** Um sistema de uma rede de lojas em que cada loja pertence a uma região, cada região a um estado e cada estado ao país, e é preciso, a partir de qualquer nível, somar o faturamento de tudo abaixo daquele nó.

*Resposta:*
Faz sentido, loja/regiao/estado/pais é hierarquia recursiva e cada nivel precisa somar o faturamento de tudo que ta embaixo, exatamente o caso que o composite resolve.