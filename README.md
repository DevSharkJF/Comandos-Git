# Git
Link para fazer o download do git e sua documentação:

    https://git-scm.com

<br>

# Ajuda
> ## Geral
Mostra os comandos do git, abreviações e suas devidas explicações:

    git help

> ## Comando Específico:
Abre uma janela no navegador padrão, mostrando sinopse, descrição, comandos, opções, exemplos e configurações, relacionados ao comando que deseja obter ajuda:

    git help add
    git help commit

<br>

# Estados
* Modificado (Modified): Arquivo foi alterado no diretório de trabalho, mas as mudanças não foram salvas no Github.
* Preparado (staged): Marca a versão atual de um arquivo modificado para que ele seja incluído no próximo commit.
* Consolidado (Commited): Os dados foram salvos no banco de dados local.
* Não Rastreado (Untracked): Arquivos novos no projeto que o Git ainda não monitora (precisar **git add** para adicioná-los).
* Não Modificado (Unmodified):  Arquivos cujos conteúdos são exatamente iguais aos da última versão salva.

<br>

# Configurações
As configurações do GIT são armazenadas no arquivo ``.gitconfig`` localizado dentro do diretório do usuário do Sistema Operacinal.

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
Arquivos, diretórios ou extensões listados no ``.gitignore`` não serão adicionados no repositório do Github, ficando apenas na máquina do usuário. Esse método é importante para senhas, chaves, nomes de BD entre outros. Existem dois tipos de arquivos .gitignore, são eles:

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
### **Legendas**
* rm abreviação de *remove*
* -r é necessário porque é um diretório.
* -f força a remoção do índice.
* --cached garante que os arquivos continuem no disco.
<hr>

### *Remover Arquivo / Diretório*

    git rm nome_arquivo.extensão
    git rm -r diretorio
    git clean -df

### *Listar Removidos*
Lista arquivos a serem removidos:

    git clean -n
Lista arquivos e diretórios a serem removidos:

    git clean -df

### *Remover do Controle do Git (Diretório)*
Remover um diretório do controle de versão do Git sem apagar os arquivos do computador:

    git rm -rf --cached nome-diretorio
Além de remover, mantém todos os arquivos fisicamente no computador. Útil quando adiciona uma pasta por engano e deseja ignorá-la com ``.gitignore``. O ``-r`` é necessário **sempre** que desejar remover um **diretório**.

### Exemplo:
Imagine que um usuário tenha esses diretórios:

logs/
├── app.log
├── error.log
└── access.log

imagens/
├── foto1.png
├── foto2.png

O usuário queria subir somente o diretório de imagens, mas por engano ele sobe o diretório de logs com:
* git add .
* git commit -m "Adionado fotos"
Agora o diretório ``logs`` está sendo rastreado pelo Git.

Para resolver essa situação o usuário pode:
1) Adicionar o diretório no .gitignore
2) Remover do índice: git rm -rf --cached logs
3) Fazer um novo commit: git commit -m "removendo node_modules do repositório"

**Resultado:** O diretório continua existindo no computador, o git para de monitorar.

### *Remover do Controle do Git (Arquivo)*
Remover um arquivo do controle de versão do Git sem apagar do computador:

    git rm --cache
Por ser somente arquivo, e não diretório não é necessário usar ``-r``, porém se usar o git ignora, sendo redundante.
### Exemplo:
Imagine o mesmo cenário anterior, porém dessa vez o usário subiu o arquivo .env, contendo:

DB_HOST=localhost
DB_USER=admin
DB_PASSWORD=123456

1) Adicionar o arquivo .env no .gitignore
2) Remover do índice: git rm --cached .env
3) Fazer novo commit: git commit -m "removendo .env do controle de versão".

**Resultado:** O arquivo continua existindo no computador e não é rastreado pelo git

### *Remover do Git e PC*
Remove diretórios ou arquivos do controle de versão do git, do repositório, índice e também do computador:

    git rm -rf nome-diretório_ou_arquivo
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

### *Histórico de Modificação*
Exibe histórico de modificação de um arquivo

    git log --diff-filter=M -- <caminho_arquivo>
* O **M** pode ser substituido por: Adicionado (A), Copiado (C), Apagado (D), Modificado (M), Renomeado (R)

Exibe revisão e autor da última modificação de um bloco de linhas:

    git blame -L 12,22 nome_arquivo.extensão

### *Remover Histórico*
Remove todo o histórico de um arquivo:

    git filter-branch --tree-filter 'rm -f nome_arquivo.extensão' HEAD
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

# Commit
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

Altera as mensagens de um commit:

    git commit --amend -m "Nova Mensagem"
    git commit -am "Nova Mensagem"

Altera e adiciona as novas modificações no último commit sem alterar a mensagem:

    git comiit -amend --no-edit

<br>

# Repositório 
Podem ser criados localmente ou de forma remota.

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
É possível abrir um código em um editor online do ``GitHub``, sem precisar clonar ou baixar o repositório:
1) Copie a ``URL`` do repositório
2) Adicione ``1s`` depois de **github**
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
Atualiza o repositório local de acordo com as atualizações do repositório remoto.
### *Atualiza os arquivos na branch atual*
Pega as atualizações do repositório remoto e aplica no local:

    git pull

### *Vizualizar Alterações*
Busca informações sobre um repositório remoto, mas não altera nenhuma branch:

    git fetch

<br>

# Branches / Ramificação
Ao criar um repositório com conteúdo, o GitHub cria o repositório com um só ``branch (Ramificação)``, sendo o branch-padrão, que tem o nome de `Main` ou `Master`. Esse branch principal será o que o Github exibe quando alguém visita o repositório e quando alguém deseja clonar o repositório, a menos que o usuário especifique um branch diferente.

A criação de um novo `branch / ramificação`, diverge a linha principal de desenvolvimento. Essas novas ramificações, permitem adicionar novas funcionalidades, corrigir bugs ou experimentar novas ideias com segurança, sem alterar e interferir no desenvolvimento da linha principal.

A criação de diversas `branches` é utilizada principalmente em projetos que possuem vários colaboradores, pois:
* Isolamento: Alterações feitas em uma branch não afetam o código principal até que você decida juntá-las.
* Organização: Permite o desenvolvimento de múltiplos recursos (features) em paralelo.
* Trabalho em equipe: Diferentes pessoas podem trabalhar em branches separadas ao mesmo tempo, sem que o trabalho de uma interfira no da outra.

Ao final do projeto, quando todas as branches estão funcionando, elas são mescladas para a linha principal.
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

<br>

# Rebasing
O ``rebasing`` serve para reorganizar ou reescrever o histórico de commits de um projeto. Ele é usado principalmente para atualizar a sua branch atual com as últimas alterações de outra branch (como a main ou develop), colocando os seus commits no topo e deixando o histórico linear, sem gerar commits de merge. Isso pode ser útil se a branch que você tá precisar ser revisada por outra pessoa, ou se você só quiser manter o histórico limpo pra ter uma visão melhor do que aconteceu.

Imagine que você criou uma branch feature para trabalhar em uma funcionalidade e fez alguns commits nela. Enquanto isso, alguém alterou a branch main.

Se você usar o git merge, o Git criará um commit extra apenas para juntar as duas linhas. Com o git rebase, acontece o seguinte:
* O Git "desconecta" temporariamente os seus commits da feature.
* Ele atualiza a sua branch com os commits mais recentes da main.
* Ele reaplica os seus commits da feature um por um, bem no final dessa nova linha da main.

O resultado é um histórico limpo e contínuo, como se você tivesse começado a trabalhar na feature já a partir da versão mais recente da main.

``Obs:`` O Git só executa o rebase depois que o editor é **salvo e fechado**. Enquanto o editor estiver aberto, o Git entende que o usuário ainda está editando as instruções do rebase.

## Rebase
Faz o `rebase` entre uma branch e a branch main.

    git checkout nome-branch
    git rebase master
<hr>

## Organização
O comando ``git rebase -i`` (onde o -i significa interativo) serve para editar, limpar e organizar o histórico de commits locais antes de você enviá-los para o servidor compartilhado.Diferente do rebase comum, que apenas move os commits em bloco, o modo interativo abre um painel no seu editor de texto que permite alterar o passado linha por linha.

    git rebase -i

### *Como Usar?*
Ao usar o ``git rebase -i``, geralmente precisamos informar ao git a partir de qual ponto queremos usar. O mais comum é olhar os últimos commits, deixando o comando da seguinte forma:

    git rebase -i HEAD~n°_de_commits

Para olhar os últimos 5 commits: ``git rebase -i HEAD~5``

### *Alterar Commit*
Para alterar os últimos 3 commits:

    git rebase -i HEAD~3

O editor será aberto com as linhas representando os commits:

    pick f7f3f6d alteração no read.me
    pick 310154e adicionado arquivo script
    pick a5f4a0d indentação de código

Alterar de ``pick`` para ``edit`` no commit que deseja modificar:

    edit f7f3f6d alteração no read.me
    pick 310154e adicionado arquivo script
    pick a5f4a0d indentação de código

**Salvar e fechar editor.**

O Git irá pausar no commit marcado como ``edit``.
Alterar a mensagem do commit:

    git commit --amend -m "Mensagem"

Aplicar alteração:

    git rebase --continue

### *Juntar Commits*
Para juntar vários commits, basta seguir os mesmos passos acima, porém marcar os commits que devem ser juntados com ``squash``.
<hr>

## Organização Desde o Inicial
O comando ``git rebase -i --root`` serve para abrir o rebase interativo desde o primeiríssimo commit da história do seu repositório.Por padrão, quando você faz um git rebase -i, você precisa passar um ponto de partida (como HEAD~3 para ver os últimos 3 commits). No entanto, o Git normalmente não permite que você altere o primeiro commit da história (o commit inicial) usando essa sintaxe. O modificador --root resolve isso, permitindo que você reescreva absolutamente todo o histórico da branch atual, do início ao fim:

    git rebase -i --root

* Limpar o início do projeto: Se os seus primeiros commits foram bagunçados (ex: "initial commit", "ajuste", "teste"), você pode usar o squash para juntar tudo em um único commit inicial limpo.
* Corrigir mensagens antigas: Mudar o texto do primeiríssimo commit do projeto que foi escrito com erros de digitação.
* Remover arquivos pesados do passado: Se você colocou uma senha, chave de API ou um arquivo de 1GB no primeiro commit e depois deletou, ele continua ocupando espaço no histórico. Com o --root, você pode editar o primeiro commit e removê-lo definitivamente
<hr>

## Comandos
Ao usar o rebase o Git irá exibir no editor de código alguns comandos:
* p, pick <commit> = usar o commit
* r, reword <commit> = usar o commit, mas editar a mensagem
* s, squash <commit> = usar o commit, mas mesclar no commit anterior

<br>

# Stash
O Git tem uma área chamada ``stash`` (esconderijo), onde é armazenado temporariamente alterações na cópia do trabalho, sem fazer commit delas para o repositório, para que o usuário possa trabalhar em outra coisa e depois voltar e fazer a reaplicação mais tarde. Ele é separado do diretório de trabalho, da área de staging e do próprio repositório. O stashing é útil quando você precisa alternar com rapidez o contexto e trabalhar em outra coisa, mas está no meio da alteração de código e não está pronto para fazer commit.

``Obs:`` salva as alterações sem commit (tanto as preparadas quanto as não preparadas) para uso posterior e as reverte da cópia de trabalho

## Iniciando Stash
O Git stash arquiva alterações não commitadas do seu local de trabalho, ou seja, ele volta para o estado do seu último commit guardando as alterações adicionais que você tinha feito; stashes não são transferidos para o servidor quando você envia por push.

É como se fizesse um backup das modificações dos seus arquivos.

Comando Moderno:

    git stash
    git stath -m "Mensagem"

Comando Moderno e Completo:

    git stash push
    git stash push -m "Mensagem"

Comando Legado:

    git stash save

Nesse ponto, você está livre para fazer alterações, criar novos commits, alternar ramificações e executar quaisquer outras operações do Git. Quando estiver terminado, volte e aplique mais uma vez seu stash quando estiver pronto.

### *Exemplo:*
* Estou a trabalhar numa branch e quero mudar para outra branch para fazer alguma coisa, e depois voltar. Não consigo mudar de branch porque tenho alterações não commitadas que iriam dar conflito. Então faço stash das minhas alterações, mudo de branch, faço o que tenho a fazer, volto para trás, e depois unstash.
<hr>

## Listar
Lista todos os stashes salvos:

    git stash list

Mostra resumo das alterações do stash:
    git stash show

Mostra o conteúdo completo do stash:

    git stash show -p

Mostra diff completo de stash específico:

    git stash show -p stash@{n}

Mostra stash específico:

    git stash show stash@{n}
<hr>

## Recuperar
Recupera o stash sem apagar ele da lista:

    git stash apply

Aplicar stash específico:

    git stash apply stash@{1}

Recupera e remove o stash automaticamente:

    git stash pop  

Recupera stash mantendo estado do index:

    git stash apply --index
    git stash pop --index
<hr>

## Apagar
Remove um stash específico:

    git stash drop stash@{0}

Apaga TODOS os stashes:

    git stash clear
<hr>

## Guardar
Guarda arquivos não rastreados (untracked)

    git stash push -u
    git stash -u
    git stash --include-untracked

Guarda tudo:

    git stash -a
    git stash --all
* Arquivos rastreados
* Não rastreados
* Ignorados pelo .gitignore

Guarda apenas arquivos específicos:

    it stash push nome_arquivo.ext

Múltiplos Arquivos:

    git stash push index.js style.css

Escolhe trecho por trecho:

    git stash push -p
Modo interativo (patch).

Guarda apenas arquivos NÃO staged:

    git stash --keep-index
Mantém os arquivos já adicionados com ``git add.``

Guarda SOMENTE arquivos staged:

    git stash push --staged
<hr>

## Stash e Branch
### *Criar branch*
Cria uma branch a partir do stash:

    git stash branch nova-branch

O que ele faz?
* Cria branch
* Aplica stash
* Remove stash automaticamente
<hr>

## Stash Manual
### *Criar*
É possível criar stashes que não ficam salvas na pilha (``stash list``) automaticamente.

Cria um stash sem registrar oficialmente, apenas gerando um identificador (hash) do commit temporário:

    git stash create
--> **Identificador (HASH)** = a1b2c3d4e5f6

### *Armazenar*
Serve para pegar um stash criado manualmente e armazená-lo oficialmente na lista de stashes.

Armazena um stash criado manualmente:

    git stash store n°_hash
Após armazenar, o stash irá aparecer salvo na lista (``stash list``).

# Diferenças
Mostra o que foi alterado e o que ainda não foi adicionado para ser commitado:

    git diff

Mostra as diferenças entre dois commits:

    git diff nome-commit..nome-commit

<br>

# Tags
## Criar
### *Tag Leve*

    git tag vs-1.1

### *Tag Anotada*

    git tag -a vs-1.1 -m "Mensagem"

### *Tag Assinada*
Para criar uma tag assinada é necessário uma chave privada (GNU Privacy Guard - GPG).

    git tag -s vs-1.1 -m "Mensagem"

### *Tag Commit*
Cria uma tag a partir de um commit (hash):

    git tag -a vs-1.2 n°_hash

### *Tag de Repositório Remoto*
Cria uma tag no repositório remoto:

    git push origin vs-1.2
    git push origin main versao-0.1.0

Cria todas as tags locais no repositório remoto:

    git push origin --tags
<hr>

## Listar
### *Listar Versões*
Lista todas as versões:

    git tag
