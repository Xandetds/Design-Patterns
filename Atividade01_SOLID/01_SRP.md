# Exercício 1 – Single Responsibility Principle (SRP)

Observe a classe `RelatorioVendas` abaixo:

```java
public class RelatorioVendas {

    private final List<Venda> vendas;
    private final LocalDate dataInicio;
    private final LocalDate dataFim;

    public RelatorioVendas(List<Venda> vendas, LocalDate dataInicio, LocalDate dataFim) {
        this.vendas = vendas;
        this.dataInicio = dataInicio;
        this.dataFim = dataFim;
    }

    public String gerarRelatorio() {
        StringBuilder sb = new StringBuilder();
        sb.append("Relatório de Vendas\n");
        sb.append("Período: ").append(dataInicio).append(" até ").append(dataFim).append("\n\n");

        double total = 0.0;
        for (Venda venda : vendas) {
            sb.append("ID: ").append(venda.getId())
              .append(" | Data: ").append(venda.getData())
              .append(" | Cliente: ").append(venda.getCliente())
              .append(" | Valor: R$ ").append(String.format("%.2f", venda.getValor()))
              .append("\n");
            total += venda.getValor();
        }

        sb.append("\nTotal de vendas: R$ ").append(String.format("%.2f", total)).append("\n");
        return sb.toString();
    }

    public void salvarRelatorio(String caminho) {
        String conteudo = gerarRelatorio();
        try (FileWriter writer = new FileWriter(caminho)) {
            writer.write(conteudo);
        } catch (IOException e) {
            throw new RuntimeException("Erro ao salvar relatório em arquivo: " + caminho, e);
        }
    }

    public void enviarRelatorioPorEmail(String email) {
        String conteudo = gerarRelatorio();
        EmailService emailService = new EmailService();
        emailService.enviarEmail(email, "Relatório de Vendas", conteudo);
    }

    public static class Venda {
        private final String id;
        private final LocalDate data;
        private final String cliente;
        private final double valor;

        public Venda(String id, LocalDate data, String cliente, double valor) {
            this.id = id;
            this.data = data;
            this.cliente = cliente;
            this.valor = valor;
        }

        public String getId() { return id; }
        public LocalDate getData() { return data; }
        public String getCliente() { return cliente; }
        public double getValor() { return valor; }
    }
}
```

## Perguntas

**1.** Explique por que essa classe viola o SRP.

*Resposta:*
Porque ela assume varias responsabilidades diferentes, atrapalhando o entendimento d codigo, e a coesão caso alguma outra classe não relacionada queira utilizar um método que está nessa classe


---

**2.** Liste pelo menos três responsabilidades diferentes que ela está assumindo.

*Resposta:*
Gerar um relatório, enviar esse relatório por email, e salvar ele no banco de dados.


---

**3.** Proponha uma nova estrutura de classes usando um diagrama de classes que distribua essas responsabilidades de forma mais adequada.

*Resposta:*

Criar uma classe RelatorioVendasRepository e colocar o metodo de salvar dentro dela, e criar uma outra chamada RelatorioVendasNotificador, e adicionar o envio por email nela