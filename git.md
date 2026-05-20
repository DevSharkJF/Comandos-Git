# Estados
* Modificado (Modified)
* Preparado (staged)
* Consolidado (Commited)

<br>

# Configurações
As configurações do GIT são armazenadas no arquivo `.gitconfig` localizado dentro do diretório do usuário do Sistema Operacinal

### *Listar Configurações*
    git config --list
<hr>

## Local
### *Setar Nome*
Define seu nome local:

    git config --local user.name "Seu Nome"

### *Setar Email*
Define o email local:

    git config --local user.email "seu@email.com"
<hr>

## Global 
### *Setar Nome*
Define o nome globalmente:

    git config --global user.name "Seu Nome"

### *Setar Email*
Define o email globalmente:

    git config --global user.name "seu@email.com"

### *Configurações Globais*
Lista as configurações globais:

    git config --global --list

### *Editor Padrão*
Define o vim como editor padrão:

    git config --global core.editor "vim"

Define o VSCODE como editor padrão:

    git config --global core.editor "code --wait"

Volta para o editor padrão:

    git config --global --unset core.editor

### *Ignorar Arquivo*
Ignora um ou mais arquivos globais:

    git config --global core.excludesfile nome-arquivo
    git config --global core.excludesfile ~/.gitignore

<br>

# Ignorar Arquivos
Arquivos, diretórios ou extensões listados no `.gitignore` não serão adicionados no repositório do Github, ficando apenas na máquina do usuário. Esse método é importante para senhas, chaves, nomes de BD entre outros. Existem dois tipos de arquivos .gitignore, são eles:

* Geral: Normalmente armazenado no diretório do usuário do Sistema Operacional. O arquivo que possui a lista dos arquivos/diretórios a serem ignorados por **todos os repositórios** deverá ser declarado conforme citado acima. O arquivo não precisa ter o nome de **.gitignore**.

* Repositório: Deve ser armazenado no diretório do repositório e deve conter a lista dos arquivos/diretórios que devem ser ignorados apenas para o repositório específico.

<br>

# Repositório Local
### *Novo Repositório*
Cria um novo repositório de forma local:

    git init
