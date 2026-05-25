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

# Ações de Arquivos e Diretórios
## Adicionar
### *Adicionar Arquivo Específico*
Adiciona somente um arquivo de todo o repositório:

    git add nome_arquivo.extensao

### *Adicionar Diretório*
Adiciona um diretório completo:

    git add nome_diretório

### *Adicionar Tudo*
Adiciona todos os arquivos (novos, modificados e removidos) e pastas do diretório em que o comando é digitado:

    git add .

Adiciona todos os arquivos (novos, modificados e removidos) de todo o repositório:

    git add --all

Adiciona arquivos modificados ou removidos:

    git add -u
    git add -update

### *Adicionar arquivo listado no .gitignore*
Pode adicionar o arquivo geral ou do repositório:

    git add -f arquivo_gitignore.extensão
<hr>

## Remover
### *Remover Arquivo / Diretório*

    git rm nome_arquivo.extensão
    git rm -r diretorio
<hr>

## Histórico
Mostra algumas opções disponíveis para ajudar:

    git log --help

### *Exibir*
Exibe o histórico:

    git log

Exibe histórico de um arquivo específico:

    git log -- <caminho_arquivo>

Exibe histórico de um arquivo específico que contêm determinada palavra:

    git log --sumary -S<palavra> [<caminho_arquivo>]

Exibe histórico de um autor:

    git log --author=usuario

### *Histórico em Linha*
Exibe o histórico em linha:

    git log --oneline

Exibe informações resumidas (hash e comentário):

    git log --pretty=oneline

### *Histórico Detalhado*
Exibe os detalhes, mostrando o que aconteceu no projeto:

    git log -p

Exibe histórico das duas últimas alterações:

    git log -p -2

Resumo histórico (hash completa, autor, data, comentário e quantidade de alterações):

    git log --stat

Exibe histórico com formatação específica:

    git log --pretty=format:"%h - %an, %ar : %s"

* %h: Abreviação do hash;
* %an: Nome do autor;
* %ar: Data;
* %s: Comentário.

Exibe todo os logs bem detalhados:

    git log --graph --oneline --all

### *Gráfico*
Visualizador de histórico gráfico:

    gitk
<hr>

## Desfazer
### *Desfazer Alteração Local (Working Directory)*
Descarta alterações do arquivo, quando não foi adicionado na **staged area**:

    git checkout -- nome_arquivo.extensão
    git restore nome_arquivo.extensão

### *Desfazer Tudo*
Descarta alterações de todos os arquivos:

    git checkout .
    git restore .

### *Desfazer Alteração Local (Stating Area)*
Desmarca o arquivo para ser commitado, não foi adicionado na **staged area**:

    git reset HEAD nome_arquivo.extensão

### *Desfazer Commit*
Desfaz o último commit, mantendo todas as alterações dods arquivos intactas para um novo commit, na **staged area**:

    git reset --soft HEAD^	

### *Apagar Commit*
Apaga permanentemente o último commit e descarta todas as alterações não salvas feitas nos arquivos desde então. Retorna o repositório para o estado que estava no penúltimo commit:

    git reset --hard HEAD^	

### *Desfazer Alteração Commit*
Remove as alterações no código do commit, criando um novo commit. Não apaga o commit original do histórico:

    git revert nome-hash

<br>

# Comitar
Comitar é ação de salvar os arquivos e os diretórios e prepará-los para enviar ao repositório
### *Tipos*
Realiza o commit de um arquivo:

    git commit nome_arquivo.extensão

Realiza o commit de vários arquivos:

    git commit nome_arquivo.extensão nome_arquivo.extensão nome_arquivo.extensão

Realiza um commit com título:

    git commit -m "Título"

Realiza um commit com título e Descrição:

    git commit -m "Título" -m "Descrição"

Adiciona todos os arquivos e realiza o commit:

    git commit -a -m "Mensagem"

Realiza o commit de um arquivo informando uma mensagem:

    git commit nome_arquivo.extensão -m "Mensagem"

<br>

# Repositório 
Podem ser criadas localmente ou de forma remota
## Local
### *Novo Repositório*
Cria um novo repositório de forma local:

    git init

Cria um repositório que não terá working tree, ou seja, não terá cópia dos arquivos, servindo como servidor:

    git init --bare

### *Status*
Analisa o estado do repositório:

    git status
<hr>

## Remoto
É possível abrir um código em um editor online do `GitHub`, sem precisar clonar ou baixar o repositório:
1) Copie a `URL` do repositório
2) Adicione `1s` depois de **github**
* https://github.com/nome_usuario/nome_repositório
* https://github1s.com/nome_usuario/nome_repositório

### *Exibir Repositório*
Lista os repositórios remotos:

    git remote

Lista os nomes e endereços:

    git remote -v

Exibi informações dos repositórios remotos:

    git remote show origin

### *Adicionar*
Adiciona um repositório remoto:

    git remote add origin url_repositorio
    git remote set-url origin url_repositorio

### *Renomear*
Renomeia um repositório remoto:

    git remote rename origin novo-nome
    git remote rename nome-atual novo-nome

### *Desvincular*
Desvincula um repositório remoto:

    git remote remove nome-repositório
    git remote rm nome-repositório

### *Clone*
Clona um repositório remoto já existente:

    git clone url_repositório

Baixa o repositório remoto em uma branch específica:

    git clone --branch nome-branch url_repositório
    git clone -b nome-branch url_repositório

### *Enviar Arquivos*
Envia arquivos e diretórios para o repositório remoto. Ao usar a primeira opção, ficará salvo e os demais envios não irão precisar colocar a branch:

    git push -u origin master
    git push nome-remote nome-branch

Envia os arquivos e diretórios após o primeiro push:

    git push

Envia os dados de todas as branches para o repositório remoto:

    git push --all
<hr>

## Atualizar Repositório
Atualiza o repositório local de acordo com as atualizações do repositório remoto
### *Atualiza os arquivos na branch atual*
Pega as atualizações do repositório remoto e aplica no local

    git pull

### *Vizualizar Alterações*
Busca informações sobre um repositório remoto, mas não altera nenhuma branch

    git fetch

<br>

# Branches / Ramificação
Ao criar um repositório com conteúdo, o GitHub cria o repositório com um só branch (Ramificação), sendo o branch-padrão, que tem o nome de `Main` ou `Master`. Esse branch principal será o que o Github exibe quando alguém visita o repositório e quando alguém deseja clonar o repositório, a menos que o usuário especifique um branch diferente.

A criação de um novo `branch / ramificação`, diverge a linha principal de desenvolvimento. Essas novas ramificações, permitem adicionar novas funcionalidades, corrigir bugs ou experimentar novas ideias com segurança, sem alterar e interferir no desenvolvimento da linha principal.

A criação de diversas `branches` é utilizada principalmente em projetos que possuem vários colaboradores, pois:
* Isolamento: Alterações feitas em uma branch não afetam o código principal até que você decida juntá-las.
* Organização: Permite o desenvolvimento de múltiplos recursos (features) em paralelo.
* Trabalho em equipe: Diferentes pessoas podem trabalhar em branches separadas ao mesmo tempo, sem que o trabalho de uma interfira no da outra

Ao final do projeto, quando todas as branches estão funcionando, elas são mescladas para a linha principal;
<hr>

## Ações
### *Branch Principal*
Volta para o branch principal / master:

    git checkout master

Volta para a branch anterior sem escrever o nome:

    git checkout -
<hr>

## Criar Branch
### *Criar uma Branch*

    git branch nome-branch

### *Criar e Trocar*
Cria um novo branch e troca:

    git checkout -b nome-branch
    git switch -c nome-branch

### *Trocar Existente*
Troca para um branch existente:

    git checkout nome-branch
    git switch nome-branch

### *Branch no Repositório Remoto*
Cria um branch no repositório remoto com mesmo nome:

    git push origin nome-branch

Cria um branch no repositório remoto com nome diferente:

    git push origin nome-branch:new-branch

Cria um branch já existente localmente no repositório remoto:

    git push --set-upstream origin <nome-branch>

Baixa um branch remoto para edição:

    git checkout -b nome-branch origin/nome-branch
<hr>

## Listar Branches
### *Tipos de Listagem*
Lista as branches locais:

    git branch

Lista as branches locais e remotas:

    git branch -a

Lista branches com informações dos últimos commits:

    git branch -v

### *Listagem de Merged*
Lista branches que já foram fundidos (merged) com o `master`:

    git branch --merged

Lista branches que não foram fundidos (merged) com o `master`:

    git branch --no-merged
<hr>

## Apagar Branch
### *Tipos de Delete*
Deleta a branch somente sem conflitos:

    git branch -d nome-branch

Deleta a branch com ou sem conflitos:

    git branch -D nome-branch

Apaga um branch remoto:

    git push origin:nome-branch
<hr>

## Renomear Branch
### *Tipos de Rename*
Renomeia a branch, se estiver dentro dela:

    git branch -m novo-nome

Renomeia a branch, dentro de outra branch:

    git branch -m nome-atual novo-nome

<br>

# Merge
Merge refere-se a *mesclar* ou *unir* as alterações das branches selecionadas e as implementa no branch main/master.

As vezes, o Git não consegue unir os arquivos de forma automática se duas pessoas alteraram a mesma linha de um código de maneiras diferentes. Quando isso acontece, ele gera um conflito e você precisará abrir o arquivo manualmente, escolher qual parte do código manter e depois concluir a junção.

Para realizar o `merge`, é necessário estar no branch que deverá receber as alterações. O `merge` pode ser automático ou manual. O merge automático será feito em arquivos textos que não sofreram alterações nas mesmas linhas, já o merge manual será feito em arquivos textos que sofreram alterações nas mesmas linhas.

A mensagem indicando um `merge` manual será:

	Automerging meu_arquivo.txt
	CONFLICT (content): Merge conflict in meu_arquivo.txt
	Automatic merge failed; fix conflicts and then commit the result

### *Fazer Merge*
Faz Merge do branch atual com uma selecionada:
    git merge nome-branch

Faz Merge para o branch main/master:

    git merge main/master

Faz Merge trocando para o branch que deseja:

    git checkout nome-branch
    git merge nome-branch

### *Cancelar Merge*
Cancela o merge e volta ao estado anterior:
    git merge --abort

### *Squash Merge*
Combina todas as alterações de um branch em um único commit, em vez de cada commit ser individual:

    git merge --squash nome-branch
<hr>

## Merge Non Fast Forward

### *NON-FAST-FORWARD*
O comando `git merge --no-ff` serve para forçar a criação de um commit de merge, mesmo quando o Git conseguiria juntar as alterações automaticamente usando `fast-forward`.

    git merge --no-ff nome-branch
`Fast-Forward:` Quando no histórico, não existe um commit de merge, deixando o histórico linear.

### **Sem Usar --no-f**
Você criou um branch feature, fez commits nela ``(C e D)``, e a main não mudou desde então:

    main
    A---B

    feature
    \---C---D

Depois de efetuar o merge, o Git simplesmente move a main para frente:

    git merge feature
    main A---B---C---D

### **Usando --no-f**
A vantagem é mostrar claramente que houve um merge, de onde ele veio, quais commits pertencem a ele e quando foi integrada, deixando o histórico mais organizado com as informações:

    git merge --no-ff feature
O Git cria um commit especial de merge:

    A---B-------M

        \     /
        C---D

``M = commit de merge``

**Quando usar?**
* Use --no-ff quando:
* trabalha em equipe
* usa Git Flow
* quer histórico organizado
* quer separar funcionalidades
* quer facilitar rollback

**Talvez não precise quando:**
* projeto pequeno
* commits simples
* você prefere histórico totalmente linear