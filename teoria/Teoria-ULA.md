# ULA

Unidade Lógica Aritmética (ULA) é a parte da Unidade de Processamento (CPU) responsável por realizar operações binárias. 

!!! info "Leitura necessária"
    - [The Elements of Computing Systems (Livro texto do curso), cap 2.](https://b1391bd6-da3d-477d-8c01-38cdf774495a.filesusr.com/ugd/44046b_f0eaab042ba042dcb58f3e08b46bb4d7.pdf) 
    
    <div style="text-align: center;" class="no-print"><embed src="https://b1391bd6-da3d-477d-8c01-38cdf774495a.filesusr.com/ugd/44046b_f0eaab042ba042dcb58f3e08b46bb4d7.pdf" width="600" height="500"></div>

!!! warning
    Estudar pelo livro, o restante dessa teoria é apenas um resumo e algumas notas.

!!! video
    ![](https://www.youtube.com/embed/zRX3sOtjS10?start=403)

!!! tip
    No coursera temos os autores do livro dando uma aula sobre esse tópico.
    
    - https://www.coursera.org/lecture/build-a-computer/unit-2-4-arithmetic-logic-unit-6ZS46

## Arquitetura

A ULA utilizada no curso tem a seguinte arquitetura interna:

![](../figs/ula/ula.png)

Os sinais do diagrama são:

- `X` e `Y`: Entradas de 16 bits
- `OUT`: Saída da ULA
- `zx, nx, zy, ny, f, no`: Sinais de controle da ULA
- `zr` e `ng`: Saída de flags da ULA e que a operação realizada na ULA:
    - `zr`: resultou em zero
    - `ng`: resultou em um número negativo

## Operações

As operações suportadas pela ULA são (OUT):

- `0`: Gera o valor 0 (`000000000000000`) 
- `1`: Gera o número 1 (`000000000000001`)
- `-1`: Gera o número -1 (`111111111111111`)
- `X`: Replica a entrada X 
- `Y`: Replica a entrada Y 
- `!X`: Inverte bit a bit a entrada X
- `!Y`: Inverte bit a bit a entrada Y
- `-X`: Nega (complemento de dois) a entrada X
- `-Y`: Nega (complemento de dois) a entrada Y
- `X+1`: Soma um a entrada X
- `Y+1`: Soma um a entrada Y
- `X-1`: Subtrai um da entrada X
- `Y-1`: Subtrai um da entrada Y
- `X+Y`: Soma as entradas X e Y
- `X-Y`: Subtrai Y de X
- `Y-X`: Subtrai X de Y
- `Y&X`: Realiza a opera AND bit a bit de X com Y
- `Y|X`: Realiza a opera or bit a bit de X com Y

### Controle

Para realizar as operações é necessário controlar o sinais de controle da ULA, a tabela a seguir indica o que deve ser feito para cada umas das operações suportadas:

| zx | nx | zy | ny | f | no | out |
|----|----|----|----|---|----|--------|
|  1 |  0 |  1 |  0 | 1 |  0 | 0      |
|  1 |  1 |  1 |  1 | 1 |  1 | 1      |
|  1 |  1 |  1 |  0 | 1 |  0 | -1     |
|  0 |  0 |  1 |  1 | 0 |  0 | x      |
|  1 |  1 |  0 |  0 | 0 |  0 | y      |
|  0 |  0 |  1 |  1 | 0 |  1 | !x     |
|  1 |  1 |  0 |  0 | 0 |  1 | !y     |
|  0 |  0 |  1 |  1 | 1 |  1 | -x     |
|  1 |  1 |  0 |  0 | 1 |  1 | -y     |
|  0 |  1 |  1 |  1 | 1 |  1 | x+1    |
|  1 |  1 |  0 |  1 | 1 |  1 | y+1    |
|  0 |  0 |  1 |  1 | 1 |  0 | x-1    |
|  1 |  1 |  0 |  0 | 1 |  0 | y-1    |
|  0 |  0 |  0 |  0 | 1 |  0 | x+y    |
|  0 |  1 |  0 |  0 | 1 |  1 | x-y    |
|  0 |  0 |  0 |  1 | 1 |  1 | y-x    |
|  0 |  0 |  0 |  0 | 0 |  0 | x&y    |
|  0 |  1 |  0 |  1 | 0 |  1 | x`|` y |

### Operação não trivial

A maioria das operações da nossa ULA são imediatas, a menos imediata de entender é a operação `y-x`, nesse caso, se olharmos a operação que é realizada na ULA para executar isso notamos que:

1. $y-x=\overline{x+\bar{y}}$
    - esse `+` é de operação de soma, não OR!
1. Precisamos fazer um truque, note que: $\bar{y}=-y-1$
1. Substituindo: $\overline{x+ (-y -1)}$
1. Podemos chamar: $x+ (-y -1) = z$
1. $\overline{z}$, aplicando a mesma substituição que 2.
1. $\overline{z}=-z-1$, recuperando `z`
1. $-y-x=-(x -y -1)-1$
1. $y-x=-x+y$
