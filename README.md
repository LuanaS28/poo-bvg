# Projeto 3 - Módulo de Contatos B2B (C++)

Ticket #612 - Módulo de Contatos B2B do CRM Enterprise.

O programa cadastra clientes corporativos em um `std::vector<Contato>` e exibe nome e telefone de cada um. Cada `Contato` possui um destrutor que imprime um log quando o objeto é liberado da memória.

## Estrutura

```
Projeto_3/
├── docs/
│   ├── Contato_UML.drawio
│   └── Contato_UML.png
├── src/
│   ├── Contato.h
│   ├── Contato.cpp
│   └── main.cpp
└── README.md
```

| Arquivo | Descrição |
|---|---|
| `src/Contato.h` | Declaração da classe `Contato` (atributos privados `nome` e `telefone`) com guarda de inclusão |
| `src/Contato.cpp` | Construtor parametrizado (com `this->`), destrutor com log, `imprimirNome()` e `imprimirTelefone()` |
| `src/main.cpp` | Cria o `std::vector<Contato>`, adiciona 3 contatos com `push_back()` e percorre o vector com `for` |
| `docs/Contato_UML.png` | Diagrama de Classes UML (editável em `Contato_UML.drawio`) |

## Como compilar

A partir da pasta `Projeto_3`:

```bash
g++ -Wall -Wextra src/main.cpp src/Contato.cpp -o crm_app
```

## Como executar

```bash
./crm_app
```

No Windows (PowerShell ou CMD), use `crm_app.exe` ou `.\crm_app`.

## Exemplo de saída

```
LOG: Registro do contato Sertão Digital Ltda liberado.
LOG: Registro do contato Nordeste Logística S.A. liberado.
LOG: Registro do contato Boa Viagem Soluções B2B liberado.


*-*-*-*-Lista de contatos B2B*-*-*-*-

Cliente 1:
Nome: Sertão Digital Ltda
Telefone: (88) 3421-1020
-----------------------

Cliente 2:
Nome: Nordeste Logística S.A.
Telefone: (85) 3200-4455
-----------------------

Cliente 3:
Nome: Boa Viagem Soluções B2B
Telefone: (88) 3421-9080
-----------------------

*-*-*-*-Fim da lista*-*-*-*-

LOG: Registro do contato Sertão Digital Ltda liberado.
LOG: Registro do contato Nordeste Logística S.A. liberado.
LOG: Registro do contato Boa Viagem Soluções B2B liberado.
```

## Observação sobre os logs do destrutor

As três primeiras linhas de `LOG` aparecem antes da lista porque `Contato("...")` cria um objeto temporário no `push_back()`. O vector guarda uma cópia e o temporário é destruído logo em seguida. As três últimas linhas aparecem ao final do programa, quando o vector sai de escopo e libera os contatos. O `reserve(3)` evita realocações do vector, que gerariam logs adicionais.
