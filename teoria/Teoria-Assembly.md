# ASM - Assembly

Assembly é a linguagem de programação mais próxima do hardware, nela cada linha de código é traduzida diretamente para um linha do executável (código binário).

Para mais informações sobre o assembly utilizado no curso acesse a página: [Z01 :arrow_right: Resumo Assembly](https://insper.github.io/Z01.1/Util-Resumo-Assembly/).

Exemplo:

```nasm
INICIO:
	  leaw $0, %A
	  movw %A, %D                   ; Carrega 0 em S

ADD:                                  ; Label para saltar
	  incw %D                       ; Incrementa S
	  leaw $ADD, %A                 ; Carrega endereço do label ADD
	                                ; (3 no caso)
	  jmp                           ; Salto incondicional
	  nop                           ; No-Operation
	                                ; (necessário após jump)
```

## Hardware

A seguir uma animacão de como nosso hardware acessa memória:

![](./figs/Z0-nasm-ram/1.gif)
