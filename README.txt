# GIT

## Estados

* Modificado (modified);
* Preparado (staged/index)
* Consolidado (comitted);


## Configuração

### Geral

As configurações do GIT são armazenadas no arquivo **.gitconfig** localizado dentro do diretório do usuário do Sistema Operacional (Ex.: Windows: C:\Users\Documents and Settings\Leonardo ou *nix /home/leonardo).

As configurações realizadas através dos comandos abaixo serão incluídas no arquivo citado acima.

##### Setar usuário
	git config --global user.name "Aline Lima"

##### Setar email
	git config --global user.email allinelima@gmail.com
	

##### Setar arquivos a serem ignorados
	git config --global DS.store ~/.gitignore

##### Listar configurações
	git config --list


## Repositório Local

### Criar novo repositório

	git init

### Verificar estado dos arquivos/diretórios

	git status

### Adicionar arquivo/diretório (staged area)

##### Adicionar um arquivo em específico

	git add meu_arquivo.txt

##### Adicionar um diretório em específico

	git add meu_diretorio

##### Adicionar todos os arquivos/diretórios
	
	git add .	
	
##### Adicionar um arquivo que esta listado no .gitignore (geral ou do repositório)
	
	git add -f arquivo_no_gitignore.txt
	
### Comitar arquivo/diretório

##### Comitar um arquivo
	
	git commit funcao.php

##### Comitar vários arquivos

	git commit meu_arquivo.txt meu_outro_arquivo.txt
	
##### Comitar informando mensagem

	git commit readme.txt -m "minha mensagem de commit"

### Remover arquivo/diretório

##### Remover arquivo

	git rm readme.txt

##### Remover diretório

	git rm -r diretorio

### Visualizar histórico

##### Exibir histórico
	
	git log
	
##### Exibir histórico com diff das duas últimas alterações

	git log -p -2
	
##### Exibir resumo do histórico (hash completa, autor, data, comentário e qtde de alterações (+/-))

	git log --stat
	
##### Exibir informações resumidas em uma linha (hash completa e comentário)

	git log --pretty=oneline
	
##### Exibir histórico com formatação específica (hash abreviada, autor, data e comentário)

	git log --pretty=format:"%h - %an, %ar : %s"
	
* %h: Abreviação do hash;
* %an: Nome do autor;
* %ar: Data;
* %s: Comentário.

Verifique as demais opções de formatação no [Git Book](http://git-scm.com/book/en/Git-Basics-Viewing-the-Commit-History)

##### Exibir histório de um arquivo específico

	git log -- <caminho_do_arquivo>


##### Exibir histórico modificação de um arquivo

	git log --diff-filter=M -- <caminho_do_arquivo>

* O <D> pode ser substituido por: Adicionado (A), Copiado (C), Apagado (D), Modificado (M), Renomeado (R), entre outros.

##### Exibir histório de um determinado autor

	git log --author=usuario


### Desfazendo operações

##### Desfazendo alteração local 

	git checkout -- funcao.txt

##### Desfazendo alteração local (staging area)

	git reset HEAD funcao.txt

Se o resultado abaixo for exibido, o comando reset *não* alterou o diretório de trabalho. 

	Unstaged changes after reset:
	M	funcao.txt

A alteração do diretório pode ser realizada através do comando abaixo:
	
	git checkout meu_arquivo.txt

## Repositório Remoto

### Exibir os repositórios remotos

	git remote
	
	git remote -v

### Vincular repositório local com um repositório remoto

	git remote add origin git@github.com:allinelima/treinamento_fundamentos.git
	git remote add origin git@github.com:allinelima/treinamento_fundamentos_colabore.git
	
### Exibir informações dos repositórios remotos

	git remote show origin
	
### Renomear um repositório remoto 

	git remote rename origin curso-git
	
### Desvincular um repositório remoto
	
	git remote rm curso-git

### Pegar dados dos projetos remotos
	git fetch origin

### Removendo arquivos do Stage
	git reset

### Desfazer o último commit
	git revert HEAD


### Enviar arquivos/diretórios para o repositório remoto

O primeiro **push** de um repositório deve conter o nome do repositório remoto e o branch.

	git push -u origin master
	
Os demais **pushes** não precisam dessa informação

	git push
	

### Atualizar repositório local de acordo com o repositório remoto

##### Atualizar os arquivos no branch atual

	git pull
	
##### Buscar as alterações, mas não aplica-las no branch atual

	git fetch
	
### Clonar um repositório remoto já existente

	git clone git@github.com:allinelima/treinamento_fundamentos.git
	git clone git@github.com:allinelima/treinamento_fundamentos_colabore.git

##### Renomeando branches (Se você estiver em uma branch e quiser renomear outra, você deve passar primeiro o nome atual da branch que quer renomear)

git branch -m novo-nome-da-branch

git branch -m teste teste2

### Tags

##### Criando uma tag leve

	git tag vs-1.1

##### Criando uma tag anotada

	git tag -a vs-1.1 -m "Versão 1.1"


##### Criando tag a partir de um commit (hash)

	git tag -a vs-1.2 9fceb02
	
##### Criando tags no repositório remoto

	git push origin vs-1.2
	
##### Criando todas as tags locais no repositório remoto

	git push origin --tags
	
### Branches

O **master** é o branch principal do GIT.

O **HEAD** é um ponteiro *especial* que indica qual é o branch atual. Por padrão, o **HEAD** aponta para o branch principal, o **master**.

##### Criando um novo branch

	git branch teste
	git branch teste1
	
##### Trocando para um branch existente

	git checkout teste1
	

##### Criar um novo branch e trocar 

	git checkout -b teste2
	
##### Voltar para o branch principal (master)

	git checkout master
	
##### Resolver merge entre os branches

	git merge teste1
	
Para realizar o *merge*, é necessário estar no branch que deverá receber as alterações. O *merge* pode automático ou manual. O merge automático será feito em arquivos textos que não sofreram alterações nas mesmas linhas, já o merge manual será feito em arquivos textos que sofreram alterações nas mesmas linhas.

##### Apagando um branch

	git branch -d teste

##### Listar branches 

###### Listar branches

	git branch

###### Listar branches com informações dos últimos commits

	git branch -v

###### Listar branches que já foram fundidos (merged) com o **master**

	git branch --merged

###### Listar branches que não foram fundidos (merged) com o **master**

	git branch --no-merged

##### Criando branches no repositório remoto

###### Criando um branch remoto com o mesmo nome

	git push origin teste

###### Criando um branch remoto com nome diferente

	git push origin teste3:new-branch

##### Baixar um branch remoto para edição

	git checkout -b teste0 origin/teste0


##### Apagar branch remoto

	git push origin:teste0

### Rebasing

Fazendo o **rebase** entre um o branch teste0 e o master.

	git checkout experiment
	
	git rebase master
	

##### Alterando mensagens de commit

	git commit --amend -m "Bug da funcao corrigido 3 (editado)"


##### Criar arquivo na pasta
echo "#local" >> README.txt  
