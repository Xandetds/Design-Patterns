# Exercício 4 – Exemplo real

Acesse o seguinte arquivo em um projeto open source:

- **Projeto:** OpenJDK
- **Arquivo:** [`InputStreamReader.java`](https://github.com/openjdk/jdk/blob/master/src/java.base/share/classes/java/io/InputStreamReader.java)

Em Java, um `InputStream` trabalha com bytes, enquanto um `Reader` trabalha com caracteres. Para ler texto de uma fonte que só fornece bytes (arquivo, socket, etc.), o JDK oferece o `InputStreamReader`: uma classe que estende `Reader` (a interface que o cliente usa) e encapsula um `InputStream` (recebido no construtor, junto com um charset), convertendo os bytes em caracteres. É exatamente a estrutura do adaptador de objeto vista em aula.

## Perguntas

**1.** Quais são as duas "interfaces" incompatíveis que o `InputStreamReader` liga? O que a classe estende (qual o tipo dela) e o que ela recebe no construtor?

*Resposta:*
InputStreamReader estende Reader, que é a abstração que o cliente usa e trabalha com char. No construtor ele recebe um InputStream, que trabalha com byte, junto com um charset. As duas interfaces incompatíveis são Reader, baseado em caractere, e InputStream, baseado em byte.



---

**2.** Observe os métodos `read()`, `ready()` e `close()`: para onde eles delegam? Por que o código cliente que lê texto enxerga apenas um `Reader` e nunca precisa conhecer o `InputStream` por baixo?

*Resposta:*
Esses métodos delegam para o StreamDecoder interno, que é quem de fato lê os bytes do InputStream e decodifica em caracteres usando o charset. O cliente só enxerga a interface Reader porque todo acesso ao InputStream fica encapsulado dentro do InputStreamReader e do StreamDecoder. O código cliente nunca chama métodos do InputStream diretamente.



---

**3.** Onde acontece a conversão de bytes → caracteres (dica: observe o campo `StreamDecoder sd`)? Que variação do padrão Adapter essa classe representa e por que ela funciona com qualquer `InputStream` (arquivo, socket, memória)?

*Resposta:*
A conversão acontece dentro do StreamDecoder, que usa um decodificador de charset para transformar os bytes lidos em caracteres. É uma variação do adaptador de objeto, que usa composição, guardando uma referência ao InputStream, em vez de herança. Funciona com qualquer InputStream porque InputStream é um tipo abstrato, arquivo, socket ou memória são apenas implementações diferentes, e o InputStreamReader só depende do tipo abstrato, nunca da implementação concreta.


