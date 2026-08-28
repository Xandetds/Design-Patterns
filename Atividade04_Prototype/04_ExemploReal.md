# Exercício 4 – Exemplo real

Acesse os seguintes arquivos no projeto open source do JDK:

- **Projeto:** OpenJDK
- **Arquivos:**
  - [`Object.java`](https://github.com/openjdk/jdk/blob/master/src/java.base/share/classes/java/lang/Object.java) (método nativo `clone()`)
  - [`Cloneable.java`](https://github.com/openjdk/jdk/blob/master/src/java.base/share/classes/java/lang/Cloneable.java)

O Java traz suporte a clonagem nativa: `Object.clone()` cria uma cópia do objeto, mas só funciona se a classe implementar a interface marcadora `Cloneable`. Diferente do padrão visto em aula, aqui a própria máquina virtual é quem faz a cópia.

## Perguntas

**1.** Observe as exigências do `clone()` nativo: retorna `Object` (exigindo cast), pode lançar `CloneNotSupportedException` e depende de `super.clone()`. Compare esse mecanismo com o contrato de clonagem visto em aula (interface com método `clonar()` + construtor de cópia). Qual é mais próximo da ideia do GoF de Prototype e por quê?

*Resposta:*
O visto em aula é mais proximo do GoF pois ele realmente utiliza um metodo que copia a si mesmo, enquanto o do JDL tenta fazer isso mas usando um método de fora da interface.

---

**2.** Vimos que a cópia rasa faz o clone compartilhar os objetos internos com o original. No `clone()` nativo do Java, o comportamento padrão é a cópia rasa ou cópia profunda?

*Resposta:*
Cópia rasa,. O arquivo fala isso em um dos comentários, e os campos são copiados todos em uma atribuição, eles ficam compartilhados entre o original e o clone. A cópia profunda so acontece se for sobrescrito clone() e clonar na mão os campos mutáveis.
