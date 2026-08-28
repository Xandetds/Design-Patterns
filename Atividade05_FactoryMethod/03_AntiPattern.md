# Exercício 3 – Anti-pattern

Considere o código Java abaixo, usado para enviar notificações aos usuários de um sistema:

```java
public class NotificadorService {

    public void enviar(String canal, String destinatario, String mensagem) {
        if (canal.equals("email")) {
            new EmailNotificador().enviar(destinatario, mensagem);
        } else if (canal.equals("sms")) {
            new SmsNotificador().enviar(destinatario, mensagem);
        } else if (canal.equals("push")) {
            new PushNotificador().enviar(destinatario, mensagem);
        }
    }
}

public class EmailNotificador {
    public void enviar(String destinatario, String mensagem) { /* ... */ }
}

public class SmsNotificador {
    public void enviar(String destinatario, String mensagem) { /* ... */ }
}

public class PushNotificador {
    public void enviar(String destinatario, String mensagem) { /* ... */ }
}
```

## Perguntas

**1.** Por que essa forma de escolher o canal com `if/else` é um problema de design?

*Resposta:*
Porque para cada novo tipo de notificador teriamos que editar o codigo, e porque o metodo principal tem contato direto com a logica, ferindo o open closed.

---

**2.** O que precisa ser alterado para adicionar um novo canal (por exemplo, WhatsApp)? Que riscos essa mudança traz para o código que já foi testado?

*Resposta:*
Precisa ser adicionado um novo if, e uma nova classe desse notificador, fazendo com que tenhamos que testar novamente o codigo.

---

**3.** Proponha uma solução usando o padrão Factory Method, explicando em linhas gerais: a interface do produto (`Notificador`), o criador abstrato com o método fábrica e os criadores concretos por canal.

*Resposta:*
Fazer um creator principal como NotificadorService e ele ter um metodo de criarNotificador(), e fazer esse creator ter subclasses para cada tipo de notificação. Dessa forma o metodo principal nao teria acesso à logica e utilizaria a implementação da mesma forma toda vez.