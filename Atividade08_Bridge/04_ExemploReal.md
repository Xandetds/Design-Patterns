# Exercício 4 – Exemplo real

Acesse os seguintes arquivos em um projeto open source:

- **Projeto:** OpenJFX (a biblioteca JavaFX, da família OpenJDK)
- **Arquivos:**
  - [`Skin.java`](https://github.com/openjdk/jfx/blob/master/modules/javafx.controls/src/main/java/javafx/scene/control/Skin.java)
  - [`Button.java`](https://github.com/openjdk/jfx/blob/master/modules/javafx.controls/src/main/java/javafx/scene/control/Button.java)

O JavaFX separa a lógica de um controle da sua aparência usando o padrão Bridge: o `Control` (a abstração) guarda uma referência a uma `Skin` (a implementação) e delega a ela a renderização. Cada controle tem a sua própria skin (por exemplo, o `Button` usa um `ButtonSkin`). Quando o `Control` precisa da skin e ela ainda não existe, ele chama `createDefaultSkin()`. É a mesma estrutura do `ControleRemoto` que delega a um `Dispositivo` vista em aula.

## Perguntas

**1.** Quais são as duas hierarquias do padrão nesse exemplo? Onde está a abstração e onde está a implementação?

*Resposta:*
A abstração é Control e Button, o que o usuário interage, estado, comportamento, eventos. A implementação é Skin e ButtonSkin, responsável pela aparência ou renderização de fato. Control guarda uma referência a Skin e delega a ela o desenho.



---

**2.** Em `Button.java`, localize o método `createDefaultSkin()`. O que ele retorna? Por que o `Button` delega a própria aparência a um `ButtonSkin` em vez de embutir todo o desenho no próprio controle?

*Resposta:*
Retorna uma nova instância de ButtonSkin, associada ao próprio botão. O Button delega a aparência a um ButtonSkin em vez de embutir o desenho nele mesmo porque assim a lógica do controle, estado e comportamento, fica separada da lógica visual. Isso permite trocar a skin, temas diferentes, sem tocar no Button, e vice-versa.

