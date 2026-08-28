# Exercício 1 – Aplicações

Para cada cenário abaixo, indique se o padrão Prototype é apropriado ou não e justifique em 2–3 frases.

Para cada item, responda:
- "Faz sentido usar Prototype" ou "Não faz sentido usar Prototype".
- Explique rapidamente o porquê (custo de criação, repetição de configuração, variações sobre uma base, acoplamento, overengineering, etc.).

## Perguntas

**1.** Um sistema de relatórios financeiros em que os relatórios mensais nascem de um template base com cabeçalho, rodapé e seções padrão, mudando apenas os valores de cada mês.

*Resposta:*
Faz sentido. Com o uso de copia para as informações repetidas desse template, podemos reaproveitar varios objetos de um modelo base.

---

**2.** Uma classe simples `Ponto` com apenas dois campos obrigatórios (`x`, `y`), utilizada em um sistema de CAD e instanciada dezenas de vezes por segundo.

*Resposta:*
Não faz sentido, para uma classe simples como essa o copy seria overengineering

---

**3.** Um sistema de jogos em que os inimigos possuem muita configuração (estatísticas, equipamentos, habilidades) e várias fases criam variações de um mesmo guerreiro repetindo o mesmo código de construção.

*Resposta:*
Faz sentido, reaproveita os objetos já utilizados com uma base de guerreiro para as variaveis que se repetem.

---

**4.** Um módulo em que o cliente não deve conhecer as classes concretas dos objetos que precisa, podendo apenas pedir uma cópia pelo nome do modelo (por exemplo, "guerreiro", "mago") através de um registro.

*Resposta:*
Faz sentido, daria para utilizar o regisro de protótipos, fazendo como se fosse um de/para da string que queremos utilizar para o nome da classe com um hash map, assim o cliente não saberia o nome real da classe.

---

**5.** Uma classe `Produto` com três campos obrigatórios (`nome`, `preco`, `quantidadeEstoque`), criada em um único ponto do sistema através do construtor tradicional e sem variações.

*Resposta:*
Não faz sentido, seria overengineering, pois ele é criado em um único ponto do sistema, sendo assim, não precisamos fazer a cópia dele.
