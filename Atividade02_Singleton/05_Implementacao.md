# Exercício 5 – Implementação

Imagine que você foi contratado para criar um Sistema Central de Alertas de Emergência para diferentes órgãos de segurança:

- Polícia
- Bombeiros
- SAMU

Cada órgão possui seu próprio módulo no sistema, mas todos precisam acessar o mesmo centro de controle para:

- enviar alertas (por exemplo: acidente, incêndio, assalto),
- receber mensagens já registradas no sistema (histórico de alertas).

## Sua missão

Implemente, em Java, um sistema em que exista apenas um "central de alertas" na aplicação inteira, usando o padrão Singleton.

**1.** Crie uma classe `CentralDeAlertas` que seja um Singleton:
- Uma estrutura interna (por exemplo, `List<String> mensagens`) para armazenar os alertas enviados.
- Métodos, por exemplo:
  - `public void enviarAlerta(String orgao, String mensagem)` que adiciona uma nova mensagem ao sistema, incluindo o nome do órgão que enviou.
  - `public List<String> getAlertas()` – retorna a lista de mensagens registradas.

**2.** Implemente três classes representando os órgãos:
- `Policia`
- `Bombeiros`
- `Samu`

**3.** Cada órgão deve:
- Obter a instância da `CentralDeAlertas` sem usar `new`;
- Ter um método, por exemplo, `enviarAlerta(String mensagem)` que encaminha a mensagem para a `CentralDeAlertas`.
- Ter um método para listar todos alertas registrados na central.

**4.** Crie uma classe de teste, por exemplo `Main`, que:
- Crie objetos de `Policia`, `Bombeiros` e `Samu`.
- Faça cada órgão enviar pelo menos um alerta (mensagens diferentes).
- Liste os alertas a partir de pelo menos dois órgãos diferentes e mostre que todos veem o mesmo histórico (com as mensagens de todos).
- Comprove, se quiser, imprimindo o `hashCode()` da instância de `CentralDeAlertas` em partes diferentes do código para mostrar que é sempre o mesmo objeto.

**5.** Adicione um `README.md` ao projeto explicando:
- Por que faz sentido que a `CentralDeAlertas` seja um Singleton nesse contexto?
- Que problemas poderiam acontecer se cada órgão tivesse sua própria instância de central?
- Sua implementação é thread-safe? Se sim, demonstre como funciona no código. Se não, o que poderia ser feito para torná-la segura em um cenário com múltiplas threads (por exemplo, vários módulos disparando alertas ao mesmo tempo)?

---

## Anotações / código

*(cole aqui o código ou o link do repositório com a implementação)*
