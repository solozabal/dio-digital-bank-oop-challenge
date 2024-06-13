# dio-digital-bank-oop-challenge
Strengthen knowledge in Object-Oriented Programming (OOP) in Java, through the implementation of a digital bank.

## Diagrama de Classes

```mermaid
classDiagram
    class Banco {
        - clientes: List<Cliente>
        + adicionarCliente(cliente: Cliente): void
        + buscarCliente(cpf: String): Cliente
        + registrarTransacao(descricao: String, objeto: Object): void
    }

    class Cliente {
        - nome: String
        - cpf: String
        - contas: List<Conta>
        + getNome(): String
        + getCpf(): String
        + getContas(): List<Conta>
    }

    class Conta {
        - numero: int
        - saldo: double
        + depositar(valor: double): void
        + sacar(valor: double): boolean
        + transferir(outraConta: Conta, valor: double): boolean
        + solicitarEmprestimo(rendaMensal: double, possuiGarantia: boolean, tipoBem: String, valorBem: double): boolean
        + solicitarCartaoCredito(tipoRenda: String, rendaMensal: double, possuiBemGarantia: boolean, tipoBem: String, valorBem: double): void
        + realizarPagamentoBoleto(valor: double): void
        + solicitarExtrato(): void
        + realizarRecargaCelular(numero: String, valor: double): void
    }

    class Main {
        - banco: Banco
        + main(args: String[]): void
    }

    class Emprestimo {
        - valor: double
        - aprovado: boolean
        - tipoBem: String
        - valorBem: double
        + avaliarGarantiaVeiculo(veiculo: Veiculo): boolean
    }

    class CartaoCredito {
        - tipoRenda: String
        - rendaMensal: double
        - possuiBemGarantia: boolean
        - tipoBem: String
        - valorBem: double
        + enviarSolicitacao(): void
    }

    class Veiculo {
        - tipo: String
        - modelo: String
        - anoFabricacao: int
        - valorFipe: double
    }

    Banco "1" *-- "*" Cliente
    Cliente "1" *-- "*" Conta
    Conta "1" o-- "1" Emprestimo
    Conta "1" o-- "1" CartaoCredito
    Conta -- Veiculo
    Main "1" o-- "1" Banco
