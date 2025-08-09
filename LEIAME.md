# Guia de Uso: `uniteste.0`

Este documento descreve como usar o framework de testes `uniteste.0`.

## Visão Geral

`uniteste.0` é um framework simples para escrever e executar testes unitários. Ele fornece funcionalidades básicas para organizar seus testes em grupos, fazer asserções e visualizar um resumo dos resultados.

## Funções Principais

O framework `uniteste.0` oferece algumas funções chave para a criação de testes:

### `principal(testes)`

Esta é a função principal que executa os testes.

*   **Parâmetro**:
    *   `testes`: Uma lista de suítes de testes (geralmente criadas com `descrever`).
*   **Retorno**: Uma lista contendo:
    1.  O número total de testes que falharam.
    2.  Uma string formatada com os resultados detalhados de cada teste.
    3.  O número total de testes executados.

    A string de resultados detalhados inclui mensagens de erro para testes que falharam e um resumo final com o total de testes e o número de falhas.

### `descrever(título, testes)`

Agrupa um conjunto de testes relacionados sob um `título` comum.

*   **Parâmetros**:
    *   `título`: Uma string que descreve o grupo de testes.
    *   `testes`: Uma lista de testes individuais (geralmente asserções feitas com `iguais`) ou outros grupos `descrever`.
*   **Retorno**: Uma lista estruturada que representa a suíte de testes, contendo:
    1.  O número de falhas dentro deste grupo.
    2.  Uma lista de mensagens de resultado para os testes dentro deste grupo, prefixadas pelo `título` do grupo.

### `iguais(valor1, valor2)`

Verifica se `valor1` é igual a `valor2`. Esta é a principal função de asserção.

*   **Parâmetros**:
    *   `valor1`: O valor obtido (resultado da operação que está sendo testada).
    *   `valor2`: O valor esperado.
*   **Retorno**: Uma lista contendo:
    1.  `0` se os valores forem iguais (sucesso), ou `1` se forem diferentes (falha).
    2.  Uma lista com uma mensagem: `"ok"` em caso de sucesso, ou uma mensagem de erro detalhada como `"Esperava que [valor1] fosse igual a [valor2]."` em caso de falha.

## Exemplo de Uso

Abaixo está um exemplo de como usar o `uniteste.0` para testar algumas operações aritméticas.

### Importando via CDN

Você pode importar o `uniteste.0` diretamente de um CDN em ambientes que suportam importações de URL. Adicione a seguinte linha no início do seu arquivo de script `.0`:

```(.0)
uniteste # "https://cdn.jsdelivr.net/gh/nuffem/uniteste.0@main/uniteste.0"
```

### Importando Localmente

Primeiro, você precisa importar o `uniteste.0`. Assumindo que `uniteste.0` está no mesmo diretório ou em um caminho acessível:

```(.0)
uniteste # ./uniteste.0 // Importa o framework
```

Depois, você pode definir e executar seus testes:

```(.0)
// Define uma suíte de testes para "Testes de Aritmética"
meus_testes = uniteste.descrever("Testes de Aritmética" [
  // Um subgrupo para "Adição"
  uniteste.descrever("Adição" [
    uniteste.iguais((1 + 1) 2) // Testa se 1 + 1 = 2
    uniteste.iguais((2 + 3) 5) // Testa se 2 + 3 = 5
  ])
  // Um subgrupo para "Subtração"
  uniteste.descrever("Subtração" [
    uniteste.iguais((5 - 3) 2) // Testa se 5 - 3 = 2
    uniteste.iguais((10 - 4) 6) // Testa se 10 - 4 = 6
  ])
])

// Executa os testes. O resultado de uniteste.principal será o valor retornado por este script.
uniteste.principal([meus_testes])
```

Neste exemplo:
*   Importamos `uniteste.0` (localmente ou via CDN).
*   Usamos `uniteste.descrever` para criar uma suíte de testes principal chamada "Testes de Aritmética".
*   Dentro desta suíte, criamos subgrupos para "Adição" e "Subtração".
*   Usamos `uniteste.iguais` para realizar as asserções.
*   Finalmente, `uniteste.principal` é chamado com a lista de testes. Na linguagem .0, o último valor avaliado em um módulo (arquivo) é seu valor de retorno. Portanto, o resultado da execução dos testes (a lista retornada por `uniteste.principal`) será o valor de retorno deste script de teste. Este resultado pode ser capturado e processado pelo ambiente de execução.

## Executando os Testes

Para executar os testes, é necessário ter o interpretador da linguagem 0, que está disponível no repositório [github.com/Nuffem/0](https://github.com/Nuffem/0). O arquivo do interpretador é o `0_node.js`.

Assumindo que o repositório foi clonado no diretório `./0`, você pode executar os testes da seguinte forma:

### Executar todos os testes

Para executar todos os arquivos de teste localizados no diretório `testes/`, utilize o seguinte comando:

```sh
node 0/0_node.js testes/0
```

### Executar um teste específico

Para executar um único arquivo de teste, forneça o caminho para o arquivo de teste específico. Por exemplo, para executar `testes/iguais.0`:

```sh
node 0/0_node.js testes/iguais.0
```

O interpretador executará o script de teste e exibirá os resultados, incluindo o número de falhas, detalhes dos testes e o total de testes executados.
