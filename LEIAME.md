# uniteste.0 — Guia rápido

Um micro-framework de testes para a linguagem .0. Permite agrupar suítes de testes, fazer asserções básicas e imprimir um resumo dos resultados.

## Principais funções

*   `uniteste.descrever({título testes})`: Agrupa testes sob um nome. Retorna um objeto que pode ser exibido ou aninhado.
*   `uniteste.iguais({valor_obtido valor_esperado})`: Compara dois valores (igualdade simples) e gera mensagem de sucesso ou falha.
*   `uniteste.listas_iguais({lista1 lista2})`: Compara listas elemento a elemento e gera mensagem apropriada.

## Exemplo mínimo

```(.0)
uniteste # ./código/0

uniteste.descrever({"Aritmética" {
  uniteste.iguais({(1 + 1) 2})
  uniteste.iguais({(2 + 3) 5})
}})(0)
```

## Executando os testes

*   É necessário o interpretador 0 (repositório Nuffem/0).
*   Execução local (assumindo que o diretório `0` contém o interpretador):

    ```sh
    node 0/0_node.js testes/0
    ```

## Saída

*   O runner imprime mensagens por teste e retorna código de saída `0` se todos passaram, ou `1` caso contrário.
*   Mensagens de falha descrevem o valor obtido e o esperado.