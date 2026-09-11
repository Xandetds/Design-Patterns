# Exercício 1 – Aplicações

Para cada cenário abaixo, indique se o padrão Bridge é apropriado ou não e justifique em 2–3 frases.

Para cada item, responda:
- "Faz sentido usar Bridge" ou "Não faz sentido usar Bridge".
- Explique rapidamente o porquê (duas dimensões ortogonais, explosão de subclasses, plataforma, overengineering, etc.).

## Perguntas

**1.** Um sistema de notificações que precisa variar em duas dimensões: o tipo de conteúdo (informativo, alerta, promoção) e o canal de envio (SMS, e-mail, push). Sem o padrão, cada combinação viraria uma classe nova.

*Resposta:*
Faz sentido. Sem Bridge, cada combinação de tipo de conteúdo e canal viraria uma classe, como AlertaSMS, AlertaEmail, PromocaoPush, exatamente o crescimento multiplicativo que o Bridge evita. O tipo de conteúdo, a abstração, delega o envio ao canal, a implementação, e cada lado evolui separado.



---

**2.** Uma aplicação multiplataforma que precisa rodar a mesma lógica sobre APIs de sistema operacional diferentes (Windows, Linux, macOS), sem multiplicar as classes da interface.

*Resposta:*
Faz sentido. É o caso clássico de Bridge: a lógica da aplicação, a abstração, não deveria mudar por causa de qual sistema operacional está por baixo, a implementação. Sem isso, cada tela ou funcionalidade precisaria de uma versão por sistema operacional.



---

**3.** Um módulo de persistência em que a mesma lógica de repositório precisa funcionar com MySQL ou PostgreSQL, podendo até trocar de banco em tempo de execução.

*Resposta:*
Faz sentido, e é ainda mais forte por causa da troca em tempo de execução. Isso só é possível porque o repositório guarda uma referência ao driver do banco, a implementação, não uma relação fixa de herança. Trocar o banco não muda a lógica de repositório.



---

**4.** Um framework de testes que precisa executar testes em diferentes ambientes com diferentes configurações de hardware.

*Resposta:*

Faz sentido, desde que existam de fato duas hierarquias que evoluem separado: a lógica dos testes, a abstração, e os drivers ou execução por ambiente, a implementação. É basicamente a ideia por trás do Selenium WebDriver, onde o mesmo teste roda em Chrome, Firefox etc. Se fosse só parametrizar configuração, sem duas famílias de classes crescendo juntas, não precisaria de Bridge.

