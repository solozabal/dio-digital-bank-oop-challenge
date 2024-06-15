# dio-digital-bank-oop-challenge
Strengthen knowledge in Object-Oriented Programming (OOP) in Java, through the implementation of a digital bank.

## Diagrama de Classes

```mermaid
classDiagram
    class Cliente {
        <<abstract>>
        - String nome
        - String email
    }
    class Conta {
        <<abstract>>
        - String numero
        - double saldo
        - String senha
        + sacar(valor: double, senha: String): boolean
        + depositar(valor: double): boolean
        + validarSenha(senha: String): boolean
        + consultarExtrato(dias: int): List<String>
    }
    class ContaCorrente {
        - String cpf
        - String profissao
        - double rendaMensal
    }
    class ContaPoupanca {
        - double depositoInicial
    }

    Cliente <|-- Conta
    Conta <|-- ContaCorrente
    Conta <|-- ContaPoupanca

    class BancoDigital {
        - Map<String, ContaCorrente> contasCorrente
        - Map<String, ContaPoupanca> contasPoupanca
        + cadastrarCliente(nome: String, email: String): Cliente
        + abrirContaCorrente(nome: String, cpf: String, profissao: String, rendaMensal: double): String
        + abrirContaPoupanca(nome: String, cpf: String, depositoInicial: double): String
        + sacarDinheiroContaCorrente(numeroConta: String, senha: String, valor: double): void
        + sacarDinheiroContaPoupanca(numeroConta: String, senha: String, valor: double): void
        + transferirParaContaCorrente(numeroContaOrigem: String, senha: String, numeroContaDestino: String, valor: double): void
        + transferirParaContaPoupanca(numeroContaOrigem: String, senha: String, numeroContaDestino: String, valor: double): void
        + depositarContaCorrente(numeroConta: String, valor: double): void
        + depositarContaPoupanca(numeroConta: String, valor: double): void
        + consultarSaldoContaCorrente(numeroConta: String, senha: String): void
        + consultarSaldoContaPoupanca(numeroConta: String, senha: String): void
        + consultarExtratoContaCorrente(numeroConta: String, senha: String, dias: int): void
        + consultarExtratoContaPoupanca(numeroConta: String, senha: String, dias: int): void
        + pagarBoleto(numeroConta: String, senha: String, codigoDeBarras: String, valor: double): void
        + solicitarEmprestimo(numeroConta: String, rendaMensal: double, profissao: String, possuiBem: String, tipoBem: String, modeloAno: String, valorBem: double): void
        + solicitarCartaoCredito(numeroConta: String, rendaMensal: double, profissao: String): void
        + colocarCreditoCelular(numeroConta: String, senha: String, valor: double, numeroCelular: String): void
    }
