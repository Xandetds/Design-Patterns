# Exercício 1 – Aplicações

Para cada cenário abaixo, indique se o padrão Singleton é apropriado ou não e justifique em 2–3 frases.

Para cada item, responda:
- "Faz sentido usar Singleton" ou "Não faz sentido usar Singleton".
- Explique rapidamente o porquê (unicidade, escopo, concorrência, testes, etc.).

## Perguntas

**1.** Um serviço de configurações da aplicação que carrega propriedades de um arquivo (`application.properties`) e é lido por vários módulos de um sistema web.

*Resposta:*

Faz sentido, porque ele é lido por varios modulos da mesma forma, e ter varias instancias seria repetitivo

---

**2.** Um componente responsável por gerenciar conexões HTTP para chamadas a APIs externas, onde diferentes partes do sistema podem precisar de configurações de timeout e autenticação distintas.

*Resposta:*

Nao faria sentido, porque para configurar o timeout e a autenticacao de formas diferentes, precisariamos de estancias diferentes.


---

**3.** Um logger central que registra eventos da aplicação em arquivo/console, usado por dezenas de classes diferentes.

*Resposta:*
Faria sentido, pois todos esses eventos iriam para um so lugar, sem um monte de estancias tentando escrever ao mesmo tempo


---

**4.** Uma classe que representa o usuário autenticado atual em um sistema web com múltiplos usuários acessando simultaneamente.

*Resposta:*
Nao faria sentido. Cada usuario deveria ter a sua propria instancia, e nao centraliar em uma so.


---

**5.** Um cache em memória compartilhado entre vários serviços do back-end, que armazena dados frequentemente lidos do banco.

*Resposta:*
Faria sentido. Se cada servico tivesse sua estancia, os dados do cache de cada uma delas seria diferente, perdendo o sentido

