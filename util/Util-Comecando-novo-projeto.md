# Começando novo projeto

!!! warning "Scrum Master"
    1. O grupo deve escolher um novo mediador
    1. ==Aconselhável no primeiro projeto o facilitador ser aquele que tem mais facilidade git.==
    1. Até que todos tenham sido mediadores, não pode repetir.

Você deve fazer a secção do seu papel: Mediador/ Desenvolvedor

## Antes de começar - Mediador

!!! note "Mediador"
    ==Somente mediador==, mas todos devem acompanhar (uma hora será sua vez).

Antes de começar será necessário atualizar o ==repositório de vocês== com os novos arquivos no repositório oficial da disciplina, e também configurar o Travis para executar os testes nesse novo projeto. 

### upstream

!!! tip "Abrindo terminal no Linux"
    <kbd>ctrl</kbd>+<kbd>alt</kbd>+<kbd>t</kbd>

No terminal:

1. Referenciando repositório original da disciplina

=== "Elementos"
    ``` bash
    $ git remote add upstream https://github.com/insper/Z01.1
    ```
    
=== "Bits e Proc"
    ``` bash
    $ git remote add upstream git@github.com:Insper/bits-e-proc-proj.git
    ```

2. Atualizando repositório do grupo com alterações feitas no repositório da disciplina:

``` bash
$ git fetch upstream
$ git checkout main
$ git merge upstream/main
```

Novos arquivos devem ter aparecido no repositório, para saber quais:

``` bash
$ git diff HEAD~ --name-only
```


### Actions

!!! tip "Arquivos ocultos"
    No linux os arquivos que começam com `.` são ocultos, ou seja, eles não
    aparecem normalmente no gerenciador de arquivos ou no comando `ls`, para ver os arquivos ocultos:
    
    - No gerenciador de arquivos aperte <kbd>crtl</kbd>+<kbd>h</kbd> (*h de hide*)
    - `ls -a` (*onde -a indica all*)

Edite o arquivo `actions.yml` localizado na pasta `.github/workflows/` modificando o final do arquivo para ficar como:

=== "Elementos"
    ``` yml
    python3 Projetos/B-LogicaCombinacional/testeLogicaCombinacional.py
    python3 Projetos/C-UnidadeLogicaAritmetica/testeULA.py
    python3 Projetos/D-LogicaSequencial/testeLogicaSequencial.py
    ```
    
=== "Bits e Proc"
    Cada entrega terá um arquivo de configuracão, no caso do primeiro projeto ele já está 
    configurado, mas de uma olhada no arquivo: `.github/workflows/componentes.yml`.
    
    ``` yml
      - name: Combinacional
        run: |
        pytest hw/test_components.py
    ```


Agora vamos realizar um commit e submeter aos demais colegas do grupo as alterações:

```bash
$ git add .github/
$ git commit -m "configurando repo para novo projeto"
```

## Atualizando infra

!!! warning
    Todos devem realizar essa etapa: Mediadores e Desenvolvedores

Atualizar a infra da disciplina executando o comando a seguir na pasta raiz ro repositório:

=== "Elementos"

    ```bash
    $ ./updateZ01tools.sh
    ```

    Isso irá baixar as dependências phython (via pip) e também clonar um repositório chamado `Z01-Tools` na raiz do usuário: `$HOME/Z01-Tools/`.

=== "Bits e Proc"
    Install:
    
    ```
    pip install -r requirements.txt
    pip install pip-upgrader
    ```
    
    E execute:
    
    ```
    pip-upgrade requirements.txt
    ```
    
    Irá instalar / atualizar a lib python que possui a infra de testes da disciplina.


## Antes de começar - Desenvolvedores

!!! note "Desenvolvedores"
    1. Todos desenvolvedores devem fazer essa etapa.
    1. ==Fazer isso somente depois que o mediador fez a parte dele!==

Volte para a branch main:

```
$ git checkout main
```

Agora todos os integrantes do grupo devem atualizar o repositório local:

```
$ git pull origin main
```
