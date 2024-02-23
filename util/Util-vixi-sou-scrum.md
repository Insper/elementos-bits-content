# Vixi! Sou desenvolvedor 

![](https://imgs.xkcd.com/comics/compiling.png)

Você é desenvolvedor do projeto e não sabe por onde começar? A seguir os passos que devem ser realizados!

1. ==Aguardar mediador criar o projeto==
1. Acessar o repositório usando o link do classroom 
2. Ler documentação do projeto
3. Junto com o scrum defina as tarefas que você quer fazer, elas vão virar issues no github.
4. Para cada tarefa sua você deve:
    - Criar uma branch
    - Configurar o github actions para executar teste do projeto 
    - Implemente e teste o módulo
    - Enviar branch para github
    - Criar pull-request
5. Acompanhe o desenvolvimento do projeto pelo seus colegas, não faca apenas a sua parte!
6. Na data da entrega preencha o formulário que vai estar na página do projeto.
    
## Comandos

Criando uma branch:

```
git checkout -B NAME main
```

- NAME: escolha um nome que faca sentido.
- Lembre de criar o branch sempre do main, por isso que temos um `main` no final do comando

----------------------

Enviando uma branch para o github:

```bash
git push origin NAME
```

----------------------

Adicionado teste no CI:

``` yml title=".github/workflows/componentes.yml"
    - name: Test MODULO
      run: |
        pytest hw/test_components.py -k MODULO
```

- MODULO: Nome do modulo que está implementando.

----------------------

Criando PR:
