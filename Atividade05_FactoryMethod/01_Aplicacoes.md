# Exercício 1 – Aplicações

Para cada cenário abaixo, indique se o padrão Factory Method é apropriado ou não e justifique em 2–3 frases.

Para cada item, responda:
- "Faz sentido usar Factory Method" ou "Não faz sentido usar Factory Method".
- Explique rapidamente o porquê (acoplamento com classes concretas, variação de criação, extensibilidade, overengineering, etc.).

## Perguntas

**1.** Um serviço de notificações que precisa enviar mensagens por email, SMS e push. O fluxo de envio é sempre o mesmo (montar a mensagem, enviar, registrar log), mas cada canal entrega de um jeito diferente, e novos canais entram frequentemente.

*Resposta:*
Faz sentido usar, para que possamos seguir a teoria do open closed e não termos que sempre estar adicionando novos canais no código. Dessa forma, poderiamos utilizar uma factory, e manter só o fluxo de envio na classe principal.

---

**2.** Uma classe simples `Ponto` com apenas dois campos obrigatórios (`x`, `y`), utilizada em um sistema de CAD e instanciada dezenas de vezes por segundo através do construtor tradicional.

*Resposta:*
Não faz sentido. Ela não terá novos metodos adicionados e não é confusa de entender sem o uso de uma factory. Seria overengineering.

---

**3.** Um framework de exportação de relatórios (PDF, CSV, Excel). O módulo principal não deve conhecer as classes concretas de exportação, e novas exportações devem entrar apenas com novas subclasses, sem alterar o fluxo de geração.

*Resposta:*
Faz sentido, podemos fazer uma classe creator para exportacoes, e subclasses dele para cada tipo de exportacao.

---

**4.** Uma aplicação que precisa criar um cliente HTTP diferente conforme o ambiente: uma implementação mock nos testes e uma real (OkHttp) em produção, sem que o restante do código mude.

*Resposta:*
Faz sentido. Um metodo de fatory decidiria sozinho com base na sua logica, qual implementação usar, sem que o cliente saiba o que está por trás.
---

**5.** Uma classe `Produto` com três campos obrigatórios (`nome`, `preco`, `quantidadeEstoque`), criada em um único ponto do sistema através do construtor tradicional e sem variações.

*Resposta:*
Não faz sentido. Como não tem variações e é usado em um unico ponto do codigo, seria over utilizarmos uma factory para a implementação
