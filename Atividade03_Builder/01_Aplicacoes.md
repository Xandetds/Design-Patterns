# Exercício 1 – Aplicações

Para cada cenário abaixo, indique se o padrão Builder é apropriado ou não e justifique em 2–3 frases.

Para cada item, responda:
- "Faz sentido usar Builder" ou "Não faz sentido usar Builder".
- Explique rapidamente o porquê (quantidade de campos, opcionais, legibilidade, risco de overengineering, etc.).

## Perguntas

**1.** Uma classe `ConfiguracaoServidor` que representa as configurações de conexão de um serviço, com campos como `host`, `porta`, `timeout`, `quantidadeDeTentativas`, `usarSSL` e `proxy`, onde a maioria dos campos é opcional e varia entre ambiente de desenvolvimento e produção.

*Resposta:*
Faz sentido, pois eu nao quero ter que ficar criando construtores para cada situacao possivel, muito menos com esse tanto de variaveis.

---

**2.** Um componente responsável por montar requisições HTTP para chamadas a APIs externas, onde o código encadeia URL, método, cabeçalhos e corpo de forma legível (`Request.Builder` do OkHttp).

*Resposta:*
Faz sentido, pois ele envolve a url, o metodo os cabecalhos e o corpo, que sao varias partes configuraveis, podendo ser opcionais, e gerando varios possiveis construtores.
---

**3.** Uma classe simples `Ponto` com apenas dois campos obrigatórios (`x`, `y`), utilizada em um sistema de CAD e instanciada dezenas de vezes por segundo.

*Resposta:*
Não faz sentido, pois são poucas as cobinações possiveis a se fazer em um construtor, removendo a necessidade de fazer um builder.

---

**4.** Um `RelatorioFinanceiro` com muitas opções de configuração: título, período, filtros, ordenação, formato de saída (PDF, CSV), marca d'água e rodapé, sendo que diferentes módulos geram combinações diferentes sem alterar o código de montagem.

*Resposta:*
Faz sentido, pois se eu tiver que fazer um construtor para cada situacao, eu teria que fazer varios construtores, ou construtores enormes para cada situacao possivel.

---

**5.** Uma classe `Produto` com três campos obrigatórios (`nome`, `preco`, `quantidadeEstoque`), criada em um único ponto do sistema através do construtor tradicional.

*Resposta:*
Não faz sentido. Ela e usada em um unico ponto do sistema sempre da mesma forma. O construtor ja atenderia à necessidade da classe