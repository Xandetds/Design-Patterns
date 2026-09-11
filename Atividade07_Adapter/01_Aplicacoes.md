# Exercício 1 – Aplicações

Para cada cenário abaixo, indique se o padrão Adapter é apropriado ou não e justifique em 2–3 frases.

Para cada item, responda:
- "Faz sentido usar Adapter" ou "Não faz sentido usar Adapter".
- Explique rapidamente o porquê (interface incompatível, código de terceiros, acoplamento, overengineering, etc.).

## Perguntas

**1.** Um módulo de previsão do tempo que precisa consultar dois fornecedores externos (SDKs de terceiros) com APIs diferentes e não modificáveis, enquanto o restante da aplicação deve usar uma única interface de consulta.

*Resposta:*
Faz sentido, pois cada uma das consultas traz informações em formatos diferentes, mas que devem ser lidas pelo sistema da mesma forma, para que não tenhamos que adicionar duas lógicas de leitura diferentes.

---

**2.** Uma aplicação que hoje usa uma biblioteca legada de envio de e-mail e pretende trocá-la por outra, sem alterar os serviços que já fazem os envios.

*Resposta:*
Faz sentido, precisariamos de um adapter que implementa a interface anterior mas por dentro chama a nova.

---

**3.** Um time que decide "preparar o terreno" e já cria adaptadores para todas as classes do sistema, mesmo sem existir hoje nenhuma interface incompatível real.

*Resposta:*
Não faz sentido. Sem ter a necessidade real de existir um adapter, ele vira overengineering

---

**4.** Um `Checkout` que precisa integrar um SDK de pagamento de terceiros para processar os pedidos.

*Resposta:*
Faz sentido. Cada SDK pode ter interfaces e retornos diferentes, e eles deverão dpender de só uma interface de pagamento.
