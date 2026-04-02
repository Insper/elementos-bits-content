# ASM - Assembly

Assembly é a linguagem de programação mais próxima do hardware, nela cada linha de código é traduzida diretamente para uma linha do executável (código binário).

Para mais informações sobre o assembly utilizado no curso acesse a página: [Z01 :arrow_right: Resumo Assembly](../z01/z01-Resumo-Assembly.md)


Exemplo:

```nasm
INICIO:
	  leaw $0, %A				; Carrega 0 em A
	  movw %A, %D               ; Carrega 0 em D

ADD:                            ; Label para saltar
	  incw %D                   ; Incrementa D
	  leaw $ADD, %A             ; Carrega endereço do label ADD
	                            ; (3 no caso em A)
	  jmp                       ; Salto incondicional
	  nop                       ; No-Operation
	                            ; (necessário após jump)
```

## Hardware

A seguir uma animacão de como nosso hardware acessa memória:

![](./figs/Z0-nasm-ram/1.gif)
