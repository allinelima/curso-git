#local

-- Iniciar o repositorio
git init

-- Criar arquivo na pasta
echo "#local" >> README.txt     

-- Gravar todas as alterações
git add .

-- Gravar alteração no arquivo
git add README
    
--Armazena o conteúdo atual em um novo commit
git commit -m "Bug da funcao corrigido 2"

--Armazena o conteúdo atual em um novo commit e adiciona as alterações
 git commit -a -m "Bug da funcao corrigido 3"   

--Refazendo commit quando esquecer de adicionar um arquivo
git commit -m "Bug da funcao corrigido 3 (editado)" --amend

--Para voltar ao último commit
git reset --hard HEAD~1

--Visualizando o Histórico de Commits
git log

--Histórico de um ou mais arquivos
git log -p meus-arquivos

--Para voltar ao último commit e mantém os últimos arquivos
git reset --soft HEAD~1

--Remover o arquivo do seu diretório
git rm -f {arquivo}

-- Verificar status Listando Arquivos Modificados
git status

--Verificar Mudanças
git diff

--renomear um arquivo
git mv arquivo_origem arquivo_destino

-- Criar uma novo branch
git branch teste

-- Para mudar para uma branch existente
git checkout teste

-- Para mudar de branch e criar 9 (adicionar -b, uma nova branch será criada.)
git checkout -b {nome_da_branch}

--Indo para outra branch
git checkout minha-branch

--Listando Branches
git branch

--Renomeando branches (Se você estiver em uma branch e quiser renomear outra, você deve passar primeiro o nome atual da branch que quer renomear)

git branch -m novo-nome-da-branch

git branch -m teste teste2

-- Pegar dados dos projetos remotos
git fetch origin

--Removendo arquivos do Stage
git reset

--Desfazer o último commit
git revert HEAD

-- Inspeção e Comparação
git show