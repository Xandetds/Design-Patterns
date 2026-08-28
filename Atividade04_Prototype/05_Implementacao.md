# Exercício 5 – Implementação

Imagine que você foi contratado para criar o sistema de inimigos de um jogo.

O jogo possui vários tipos de inimigo (guerreiro, mago, arqueiro, chefe), cada um com muita configuração (`tipo`, `vida`, `dano` e uma `Arma`). Como os inimigos nascem de uma base parecida e cada fase precisa de várias variações, recriar cada um com `new` repetiria muito código de construção.

## Sua missão

Implemente, em Java, um sistema que crie inimigos por cópia de protótipos, usando o padrão Prototype.

**1.** Crie a classe `Arma`:
- Campos, por exemplo, `nome` e `bonusDano`, com getters e setters (objeto mutável).
- Um método `clonar()` que retorna uma nova `Arma` independente (para a cópia profunda).

**2.** Crie a interface `InimigoPrototype`:
- Contrato de clonagem: `InimigoPrototype clonar()`.

**3.** Crie a classe `Inimigo implements InimigoPrototype`:
- Campos: `tipo`, `vida`, `dano` e `Arma arma`.
- Um construtor de cópia (`Inimigo(Inimigo base)`) que copia os atributos simples e faz a cópia profunda da `Arma` (usando `arma.clonar()`).
- Um método `clonar()` que retorna `new Inimigo(this)`.
- Getters e setters para ajustar variações após a cópia.

**4.** Crie a classe `RegistroDePrototipos`:
- Um `Map<String, InimigoPrototype>` que guarda os protótipos prontos (`"guerreiro"`, `"mago"`, `"arqueiro"`, `"chefe"`).
- Um método, por exemplo, `getPrototipo(String nome)`, que retorna o clone do protótipo (nunca o próprio protótipo).
- O cliente pede a cópia pelo nome, sem conhecer a classe concreta `Inimigo`.

**5.** Crie uma classe de teste, por exemplo `Main`, que:
- Obtenha inimigos via `RegistroDePrototipos` pelos nomes.
- Crie um inimigo elite a partir do `"guerreiro"` (por exemplo, `setVida(...)` e `setDano(...)` maiores) e mostre que o protótipo original não muda.
- Prove que os clones são objetos distintos (por exemplo, comparando referências ou `hashCode()`).
- Demonstre a cópia profunda: modifique a `Arma` de um clone e mostre que a `Arma` de outro clone (e do protótipo) permanece intacta.
- Se quiser, mostre também o que aconteceria se a cópia da `Arma` fosse rasa (compartilhando a mesma instância).

---

## Anotações / código

*(cole aqui o código ou o link do repositório com a implementação)*
