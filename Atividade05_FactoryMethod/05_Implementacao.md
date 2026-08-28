# Exercício 5 – Implementação

Imagine que você foi contratado para criar o Sistema de Notificações de um portal acadêmico.

O sistema precisa notificar os alunos por diferentes canais (email, SMS e push) sempre seguindo o mesmo fluxo:
- montar a mensagem,
- escolher o canal,
- enviar,
- registrar no log.

Como o fluxo é sempre o mesmo e só muda qual canal é criado, repetir o envio com `new` para cada canal deixaria o código acoplado às classes concretas.

## Sua missão

Implemente, em Java, um sistema que centralize a criação do notificador em um método fábrica, usando o padrão Factory Method.

**1.** Crie a interface `Notificador`:
- Contrato: `void enviar(String destinatario, String mensagem)`.

**2.** Crie pelo menos três produtos concretos:
- `EmailNotificador`, `SmsNotificador` e `PushNotificador`, cada um implementando `Notificador` e imprimindo (ou registrando) uma mensagem que identifique o canal usado.

**3.** Crie a classe abstrata `NotificacaoService` (o Creator):
- Um método público `notificar(String destinatario, String mensagem)` que representa o fluxo comum (montar mensagem, chamar o método fábrica, enviar, registrar log).
- Um método fábrica abstrato `protected abstract Notificador criarNotificador();`.

**4.** Crie os criadores concretos:
- `EmailService`, `SmsService` e `PushService`, que estendem `NotificacaoService` e sobrescrevem `criarNotificador()` devolvendo o notificador correspondente.

**5.** Crie uma classe de teste, por exemplo `Main`, que:
- Instancie `EmailService`, `SmsService` e `PushService`.
- Envie a mesma mensagem pelos três canais usando o método `notificar(...)`.
- Mostre que o fluxo é o mesmo e apenas o canal criado muda (ex.: a saída identifica o canal).
- Explique, em um comentário ou README, como adicionar um novo canal (ex.: `WhatsApp`) exigiria apenas uma nova subclasse de `Notificador` e uma nova subclasse de `NotificacaoService`, sem alterar o fluxo existente.

---

## Anotações / código

*(cole aqui o código ou o link do repositório com a implementação)*
