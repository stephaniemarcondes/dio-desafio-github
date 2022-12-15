# GIT CONTROLE DE VERSAO

:
## Configuração ao mexer pela primeira vez no git

Acesse o gitbash e faça a configuração inicial com os seguintes comandos:

- git config --local user.name "Seu nome aqui"
- git config --local user.email "seu@email.aqui"


## Comandos comunente usados 


- iniciar repositorio: git init
- ver quais arquivos foram alterados, entre outras coisas :  git status
-  adicionar todos os arquivos: git add . 
- fazer commit: git commit -m "mensagem"  
- enviando os arquivos para o github: git push -u branchescolhida  

## Alguns conceitos do git status

- HEAD: Estado atual do nosso código, ou seja, onde o Git os colocou
- Working tree: Local onde os arquivos realmente estão sendo armazenados e editados
- Index: Local onde o Git armazena o que será commitado, ou seja, o local entre a working tree e o repositório Git em si.

## Ver o historico do git

- ver informações: git log
- informações resumidas em uma linha git log --oneline
- git log -p 

> alem do git log normal vê as alterações que foram realizadas, Você deve ter reparado que ao executar git log -p, o git nos mostrou uma tela onde é possível rolar para baixo e para cima através das setas. Quando finalizarmos a visualização do log, basta apertar a tecla q para voltar "ao normal" em nossa linha de comando. :-D

 lista de comandos git log : [devHints](http://devhints.io/git-log)

## Significado de algumas coisinhas

- Rest do commit : id unica do commit.

## Mudar configurações

- modificar repositorio: git config --local 
-  modificar maquina como um todo: git config --global 

exemplo:

> Mudar o nome: git config --local user.name "Nome Qualquer"
> Mudar email: git config --local user.email "userqualquer@mail.com" 

## Arquivo .gitignore 

>Existe um arquivo especial do Git, chamado .gitignore, e todas as linhas que estiverem nele serão lidos e ignorados pelo Git. Se temos um arquivo denominado ide-config que queremos que seja ignorado, por exemplo, basta o incluirmos em .gitignore, digitando ide-config simplesmente. Da mesma forma, se tivéssemos uma pasta ide, incluiríamos ide/, em uma nova linha.

## Repositórios remotos 

- código : git init --bare
> Uma forma de fazer init de uma pasta quando você quer que ela seja o repositório central, cujo parâmetro indica que este repositório é puro, que contém apenas as alterações dos arquivos, e não uma cópia física de cada um dos arquivos.

- comando que lista os repositórios remotos: git remote 
- comando que adiciona um repositório remoto: git remote add nomedorepositorio caminhodorepositorio
- comando que mostra o endereço fetch e push do arquivo remoto : git remote -v 

> Exemplo de querer criar e clonar uma pasta para alguem no repositorio: 
git clone enderecodapasta nomequequerdarapasta , exemplo: /c/users/nomedapasta

> Dando push:
> git push nomedorep nomedabranch

> Caso você queira renomear o repositório: git remote rename nomeorginal novonome 

> Caso você queira puxa os dados da branch do repositorio pra esse repositorio: git pull nomedorepositorio nomedabranch 

## Comandos mais usados de branch

- Criar nova branch: git branch nomedabranch 
- Mostrar todas as branchs: git branch 
- Mudar para a branch escolhida:  git checkout nomedabranch 
- Cria uma branch e muda para a branch digitada: it checkout -b nomedabranch

## Dar merge

> 1- ir para a branch que vai sofrer o merge, por exemplo a master 
> 2 - digitar o comando: git merge nomedabranchquevaifazeromerge

se aparecer uma tela de confirmação, digitar : 
:x

O merge junta os trabalhos e gera um merge commit. O rebase aplica os commits de outra branch na branch atual.

como atualizar a master com os commits da outra branch usando rebase:

- git rebase nomedabranch 
gera todos os commits da branch selecionada + commit da branch atual

- recomendado também usar o comando git log --graph , que mostra as linhas de desenvolvimento

## "Ctrl z" no git:

para desfazer antes de iniciar o processo de add e commit:
> 1- git status
> 2- git checkout -- nomedoarquivo 

para desafazer após dar add :
> 1 - git status
> 2 - git reset HEAD nomedoarquivo 
Obs: as modificações continuam lá mas sem ser marcadas pra commit, pra desfazer mesmo é só usar o git checkout -- nomedoarquivo . 

desfazer commit:
> 1- git log 
> 2- pegar o id do commit, e fazer o comando : git revert iddocommit

## Git stash

- salva temporariamente: git stash  
- mostra os arquivos em stash: git stash list 
- pega o arquivo e exclui ele da stash git stash pop 

## Git diff

- Mostra o que foi alterado no codigo, porém tem que ser antes de commitar : git diff 
- Mostra a diferença entre commits> git diff codigox. .. codigoy

## TAG e Releases

- Criar tag : git tag -a nomedatag -m "mensagem"
- Mostrar a tag: git tag 
- Enviar pro github: git push nomedorep nomedatag