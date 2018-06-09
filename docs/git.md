# Comandos GIT

#### Gerando chave SSH

`ssh-keygen -t rsa -C "seu_email@provedor.com`

Após rodar o comando será solicitado uma senha, caso queira deixar sem senha basta apertar enter sem informar nada. Após isso será gerado uma chave pública e uma chave privada. No terminal aparece em qual diretório foi criado. Agora é só editar o arquivo que contém a chave pública e configurar no repositório remoto em chaves públicas.

## Funcionalidades e comandos

#### Configurando nome do usuário do commit apenas do repositório atual

`git config user.name "Meu Nome"`

#### Configurando nome do usuário do commit de todos repositórios git local

`git config --global user.name "Meu Nome"`

#### Configurando o e-mail do usuário para commit apenas do repositório atual

`git config user.email "meuemail@email.com"`

#### Configurando o e-mail do usuário para commit de todos repositórios git local

`git config --global user.email "meuemail@email.com"`

#### Clonando um repositório

`git clone git://github.com/jcfonsecagit/repositorio.git` Este comando deverá ser executando dentro do repositório onde o projeto deve ficar.

#### Visualizando versões de um projeto

`git tag` O comando deve ser executado dentro do repositório git local

#### Voltando o projeto para um versão anterior (v001)

`git checkout v001`

#### Visualizando alterações de um arquivo

`git blame index.html` Esta funcionalidade permite consultar quem foi o autor de cada linha de um arquivo determinado arquivo.

#### Inicializando um repositório local para ser controlado pelo git

`git init` Bastar através do terminal entrar dentro da pasta que deseja controlar e executar o comando.

#### Verificar quais arquivos dentro do repositório já estão sendo controlados

`git ls-files` Não é necessário o arquivo estar comitado para aparecer, se estiver apenas no index já aparece listado quando executado este comando.

#### Verificando o status do repositório

`git status` Este comando mostra os arquivos que foram criado e ainda estão no Working Directory e os arquivos que estão no Index, prontos para serem comitados.

#### Preparando um arquivo para executar commit

`git add index.html` Este comando permite preparar um arquivo para ser comitado. Quando executado o arquivo passa do Working Directory para o Index, após isso é necessário apenas executar o `git commit`. Para executar este comando pode ser passado como parâmetro um arquivo (ex: index.html), um diretório (ex: meuprojeto/paginasweb/) ou adicionar todos os arquivos alterados ao Index sem passar nada por parâmetro, para isso deve ser executado da seguinte maneira `git add .` .

#### Executando commit

`git commit -m "Primeirto commit"` Para executar o commit, primeiro é necessário adicionar os arquivos a serem comitados no index, para isso basta executar o comando anterior. O parâmetro `-m` serve para passar por parâmetro uma mensagem de commit, caso não informado, será aberto automaticamene o editor de arquivos default do terminal para que seja informada a mensagem de commit.

#### Compartilhando um repositório git local em um repositório git remoto

`git remote add [alias_do_repositorio_remoto] [uri_do_repositorio]` Uma convensão adotada é a utilização do alias "origin" como nome do repositório remoto. No entanto, qualquer nome pode ser utilizado.

#### Enviando commit para repositório remoto

`git push origin master` __Origin__ é o alias do repositório remoto, e __master__ é o nome da branch que queremos enviar as alterações. Qualquer branch existente localmente pode ser enviada para o repositório remoto, basta especificar qual. Porém, toda vez que atualizarmos o nosso projeto local, precisaremos indicar qual o repositório e o nome da branch que a nossa branch local se refere no remoto, isto é, precisaremos digitar `git push [alias_repositorio_remoto] [alias_da_branch_remota]`. Para não precisar-mos fazer isso e digitar apenas o comando `git push` para atualizar a branch corrente, basta executar o comando `git push -u [alias_repositorio_remoto] [alias_da_branch_remota]`. Com isso, a nossa branch local sabe qual a branch remota que ela se referencia.

#### Recebendo alterações do repositório remoto para o local

`git pull origin master` __Origin__ é o alias do repositório remoto, e __master__ é o nome da branch que estamos recebendo arquivos ou alterações. Qualquer uma branch existente remotamente pode ser baixada para um repositório local, basta especificar o nome. Porém, toda vez que atualizarmos o nosso projeto local, precisaremos indicar qual o repositório e o nome da branch que a nossa branch local se refere no remoto, isto é, precisaremos digitar `git pull [alias_repositorio_remoto] [alias_da_branch_remota]`. Para não precisar-mos fazer isso e digitar apenas o comando `git pull` e atualizar a branch corrente, basta executar o comando `git pull -u [alias_repositorio_remoto] [alias_da_branch_remota]`. Com isso, a nossa branch local sabe qual a branch remota que ela se referencia.

#### Fazendo download das alterações no repositório remoto

`git fetch [alias_repositorio_remoto]` Este comando faz o download das alterações mas não faz merge automático, apenas o pull realiza merge automático.

#### Visualizando logs de commit

`git log` Esse comando mostrará informações como o autor, a data e hora e a mensagem de commit utilizada.

#### Visualizando logs de commit e linhas modificadas

`git whatchanged -r`

#### Criando uma nova branch

`git branch [alias_para_branch]` Podemos criar uma outra branch para podermos fazer alterações e testes em um branch diferente da principal, sendo assim uma boa prática não trabalhar na branch principal.

#### Criando uma nova branch e em seguida passa para branch criada automaticamente

`git checkout -b [alias_para_branch]` Cria uma branch e troca automaticamente para a branch criada

#### Deletando uma branch

`git branch -d [alias_da_branch]` Não é possível remover a branch se ela for a atual, antes de remover tem que alterar a branch atual para outra através do comando `git checkout`. Também não é possível remover uma branch que existe commit e não foi realizado o merge.

#### Deletando uma branch remota

`git push [alias_repositorio_remoto] :[alias_da_branch]` Ao executar este comando a branch remota é deletada.

#### Visualizando todas as branch que existe no projeto

`git branch` Este comando retorna uma lista com todas as branchs que existem no projeto. Quando antes do nome da branch aparecer um "*", significa que esta é a branch atual, ou seja, se realizarmos alguma alteração de arquivo, é nesta branch que será aplicadas as alterações.

#### Alterando a branch de trabalho

`git checkout [alias_da_branch_desejada]`

#### Listando branches que existem no repositório remoto

`git branch -r`

#### Listando branches locais e remotas

`git branch -a`

#### Copiando uma branch remota para repositório local

`git branch -t [alias_branch_a_ser_criada_local] [alias_repositorio_remoto]/[alias_branch_remota]`

#### Atualizando uma branch local com os commits existentes na branch principal MASTER (REBASE)

`git rebase [alias_branch_base]` Para executar este comando, deve estar seleiconado como branch atual a branch que deverá receber os commits. Por exemplo, atualizei a branch __master__ com commits que estavão no repositório remoto, e agora quero atualizar a branch local __desenvolimento__ com os commits que veio do repositório remoto para a __master__. Primeito peciso verificar se estou na __desenvolvimento__ com o comando `git branch`, caso não esteja, utiliza-se o comando `git checkout desenvolvimento`, e em seguida executa o comando `git rebase master`. Nesse instante, os commits feitos em __desenvolvimento__ são movidos para uma branch temporária e o git atualiza com os commits da __master__. Após essa atualização, o próprio git traz de volta os commits que que foram levados para a branch temporária e os aplica sobre a __desenvolvimento__, um de cada vez. Caso existir conflito temos três opções: podemos anular o rebase através
comando `git rebase --abort`, ou descartar o seu commit que gerou conflito através do comando `git rebase --skip`, ou ainda resolver o confilto manualmente direto no arquivo, pois quando ocorre conflitos que o git não consegue fazer merge automaticamente durante um rebase, o git coloca os arquivos em uma branch temporária, nesta branch pode-se utilizar do comando `git status` para descobrir quais arquivos ocorreram os conflitos e utilizar o comando `git add [nome_arquivo]` para adicionar o arquivos ao index e continuar com processo de rebase através do comando `git rebase continue`.

#### Atualizando branch MASTER com commits existente em uma branch local de desenvolvimento (MERGE)

`git merge [alias_branch_base]` Para executar este comando, deve estar seleiconado como branch atual a branch principal, a __master__. Por exemplo, vou levar os commits existentes na branch __desenvolimento__ para a branch __master__. Primeito peciso verificar se estou na __master__ com o comando `git branch`, caso não esteja utiliza-se o comando `git checkout master`, e em seguida executa o comando `git merge desenvolvimento`. Nesse instante, tem-se todos os novos commits na branch master, prontos para serem enviados para o repositório remoto através do comando `git push`.

#### Descartando alterações de um arvuivo que está no "Working Directory"

`git checkout [nome_do_arquivo]` Com este comando é possível descartar todas as alterações realizadas desde do último commit, ou seja, voltar para o estado em que se encontra no __head__.

#### Descartando alterações de um arvuivo que está no "Working Directory" utilizando uma versão que está em uma branch diferente da atual

`git checkout [alias_branch] [nome_do_arquivo]` Com este comando é possível realizar a mesma ação do comando anterior mas voltando para uma versão do arquivo que está em uma branch diferente da atual.

#### Descartando alterações do INDEX

`git reset HEAD [nome_do_arquivo]` Com este comando um arquivo que já foi adicionado no __index__ volta para o estado __Working Directory__, podendo ser
descartado através do comando `git checkout [nome_do_arquivo]`

#### Salvando alterações do Working Directory em uma stach para voltar na versão do HEAD

`git stach` Ao executar este comando todas as alterações do __Working Dorectory__ e __Index__ são salvas em uma área distinta, e o repositório é restaurado de acordo
com o __head__. Após isso pode realizar novas alterações e realizar commits normalmente.

#### Recuperando alterações salvas em um stach

`git stach pop` Com este comando as alterações salvas no __stach__ voltam para o __Working Dorectory__, mas apenas as alterações contidasno último stach salvo.

#### Verificando se existe alguma alteração salva no stach

`git stach list`

#### Recuperando um stach específico

`git stash pop stash@{[numero_do_stash_especifico]}` A executar o comando para listar as stashs existentes, o git retorna uma lista contendo o número da stash entre {}, para voltar para uma stash especifica basta executar o comando específicando qual deverá voltar para o __Working Directory__.

#### Deletando um stach

`git stash drop` Com este comando o último stash realizado será descartado.Também podemos utilizar o nome do stash como argumento para remover um stash específico que não seja o último.

#### Removendo todos os stash existentes

`git stash clear`

#### Descartando commits indesejados para um outro commit específico

`git reset [hash_do_commit_especifico]` Com esse comando conseguimos voltar um arquivo para uma commit anterior, mas todos os commits que aconteceram no intervalo serão descartados. Podemos descobrir qual o hash do commit através do comando `git log`.

#### Revertendo apenas uma commit específico sem descartar os commits posteriores

`git revert [hash_commit]` Ao digitar o comando, um novo commit revertendo as alterações do commit escolhido será realizado e o editor de texto padrão se abrirá para que se possa digitar a mensagem do commit. Para que o comando seja utilizado, é necessário que o __Working Directory__ e o __Index__ estejam "limpos", ou as alterações atuais serão descartadas. Uma boa alternativa para maior flexibilidade é a opção `-n`, para que as alterações sejam revertidas e adicionadas ao nosso __Working Directory__ e __Index__. Assim podemos fazer alterações adicionais
antes de criar um novo commit de reversão, exemplo `git revert -n [hash_do_commit]`

#### Aplicando alterações de um repositório remoto em outro repositório remoto

`git merge [alias_repositorio_remoto]/[alias_branch_base]`

#### Trazendo um commit específico de uma outra branch para a master

`git cherry-pick [hash_do_commit]`
