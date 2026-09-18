# Exercício 1 – Aplicações

Para cada cenário abaixo, indique se o padrão Decorator é apropriado ou não e justifique em 2–3 frases.

Para cada item, responda:
- "Faz sentido usar Decorator" ou "Não faz sentido usar Decorator".
- Explique rapidamente o porquê (combinação dinâmica de responsabilidades, explosão de subclasses, interface estável, overengineering, etc.).

## Perguntas

**1.** Um serviço de envio de e-mails que, em alguns fluxos, precisa registrar log, em outros comprimir os anexos e em outros fazer os dois, sem criar uma classe para cada combinação.

*Resposta:*
Faz sentido usar Decorator, pq log e compressao sao responsabilidades que podem aparecer sozinhas ou juntas, e se fosse fazer uma classe pra cada combinacao ia explodir o numero de classes. Com decorator da pra empilhar log e compressao em qualquer combinacao sem duplicar codigo.

---

**2.** Um editor de imagens que permite aplicar filtros em cadeia (brilho, contraste, sépia) em qualquer ordem e quantidade sobre uma foto.

*Resposta:*
Faz sentido, cada filtro (brilho, contraste, sepia) vira um decorator que embrulha a imagem e adiciona um efeito, e da pra empilhar quantos filtro quiser em qualquer ordem, exatamente o caso que decorator resolve.

---

**3.** Um repositório de produtos usado pelo sistema todo; para um único caso de uso de alta leitura, é preciso adicionar cache em memória, sem mudar a interface que os demais consumidores já usam.

*Resposta:*
Faz sentido, da pra criar um decorator de cache que implementa a mesma interface do repositorio e so intercepta a leitura pra guardar em memoria, sem mexer na interface nem nos outros lugares que ja usam o repositorio normal.

---

**4.** Um catálogo de livros em que cada `Livro` tem apenas título, autor e preço com estrutura simples e estável que nunca ganha variações de comportamento.

*Resposta:*
Nao faz sentido. É uma classe simples e estavel sem nenhuma variacao de comportamento, usar decorator ali seria overengineering sem necessidade.

---

**5.** Uma concessionária em que todo carro vendido sai exatamente igual, sempre com o mesmo pacote opcional embutido na classe `Carro`.

*Resposta:*
Nao faz sentido, como o pacote é sempre o mesmo pra todo carro nao tem combinacao dinamica nem variacao, entao pode ficar tudo direto na classe Carro mesmo, nao precisa de decorator.
