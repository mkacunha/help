# Comandos Linux

`~/`   é um atalho para o diretório do usuário, este comando é o mesmo que /home/nome do usuário  
`etc/init.d`   diretório onde fica scripts de programas que iniciam juntamente com o sistema operacional  
`<comando> .`   executa o comando no diretório atual (ex: cd ., ls .)  
`<comando> ..`   executa o comando no diretório anterior (ex: cd .., ls ..)  

### Ajuda
`man <comando>`  mostra todas as opções de um comando

### Informações
`pwd`   mostra pasta atual  
`ls`   lista arquivos e diretórios  
`ls -l`   lista arquivos e diretórios detalhando  
`ls -a`   lista arquivos e diretórios inclusive os que estão ocultos  
`ls *`   lista todos os aquivos do diretório e subdiretório 
`which <programa>`  mostra qual arquivo será executado para abrir um programa  
`whoami`   mostra usuário logado no bash  

### Busca de palavras e arquivos
`grep <palavra>`   busca por palavras em arquivos  

`locate <nome arquivo>`   procura por um arquivo em todo o HD, os quais ficam armazenados em um banco de dados interno tornando a procura rápida  
`updatedb`   atualiza o banco de dados interno  

`wc`   conta a quantidade de palavras
- `-w <arquivo>`   conta a quantidade de palavras em um arquivo (ex: `wc -w meuArquivo.txt`)  
- `-c <arquivo>`   conta quantidade de caracteres (ex: `wc -c meuArquivo.txt`)  
- `-l <arquivo>`   quantidade de linhas (ex: `wc -l meuArquivo.txt`)  

### Manipulação de arquivos e diretórios
`touch <nome arquivo>`   encosta no arquivo alterando a data de modificação
  
`echo "<argumento>"`   imprime no terminal o argumento  
`echo "<argumento>" > <arquivo de destino>`    grava os argumentos informados no arquivo de destino informados  
`echo "<argumento>" >> <arquivo de destino>`    adiciona os argumentos informados no arquivo de destino informados  

`mkdir <nome diretório>`   cria um diretório com o nome passado como argumento

`rmdir <nome diretório>`   remove um diretório  
`rm -r <nome diretório>`   remove o diretório de forma recursiva (diretório + todos os arquivos dentro)  
`rm <nome arquivo>`   remove um arquivo  

`mv <atual> <alvo>`   move um arquivo ou diretório. Ser escolher o mesmo diretório o arquivo ou diretório é renomeado  
`cp <atual> <para>`   copia um arquivo ou diretório  
`cp -r <atual> <para>`   copia um diretório de forma recursiva  

### Permissões
- d: é um diretório
- r: permissão de leitura
- w: permissão de escrita
- x: permissão de execução

`chmod +<permissão> <nome arquivo ou diretório>`   concede permissão ao arquivo ou diretório para todos os usuários  
`chmod -<permissão> <nome arquivo ou diretório>`   remove permissão do arquivo ou diretório para todos os usuários
 - u: executa o chmod para o usuário dono (ex: `chmod u +<permissão> <nome arquivo ou diretório>`)
 - g: executa o chmod para o o grupo (ex: `chmod g +<permissão> <nome arquivo ou diretório>`)
 - o: executa o chmod para outros usuários (ex: `chmod o +<permissão> <nome arquivo ou diretório>`)

### Compactação de arquivos

##### Zip
`zip <nome do arquivo.zip> <arquivo ou diretório a ser zipado>`   zipa um arquivo ou diretório  
`zip -r <nome do arquivo.zip> <arquivo ou diretório a ser zipado>`   zipa um diretório de forma recursiva  
`unzip -l <nome do arquivo.zip>`   lista arquivos que foram zipados  
`unzip <nome do arquivo.zip>`   descompacta o arquivo  
- `-q`   quiet -> utilizar juntamente com zip e unzip para não mostrar os logs de compactação de descompactação  
- `-v`   verbose -> mostrar logs, o contrário de `-q`  

#### Tar
`tar -czf <nome do arquivo zipado.tar.gz> <nome diretório ou arquivo>`   compacta um arquivo um diretório utilizando tar  
 - `-c`   criar  
 - `-z`   zip  
 - `-f`   nome do arquivo a ser criado  
 
`tar -xzf <nome do arquivo zipado.tar.gz>`   compacta um arquivo um diretório utilizando tar  
 - `-x`   descompactar  
 - `-z`   zip  
 - `-f`   nome do arquivo a ser descompactado
 
### Leitura e alteração de arquivos
 
`cat  <nome arquivo>`   lê o arquivo passado por parâmetro
`cat  arquivo?.txt`   lê todos os arquivos .txt chamados arquivo + carácter qualquer
`cat  *.txt`   lê todos os arquivos .txt

`head <nome do arquivo>`   mostra as 10 primeiras linhas de um arquivo
`head -n 3 <nome do arquivo>`   mostra as 3 primeiras linhas de um arquivo

`tail <nome do arquivo>`   mostra as 10 últimas linhas de um arquivo
`tail -n 3 <nome do arquivo>`   mostra as 3 últimas linhas de um arquivo

`less <nome do arquivo>`   abre o arquivo no terminal e pode ser utilizado as setas para navegação
    
##### VI
 `vi <nome do arquivo>`   abre um arquivo para edição
- tecla "i": edita o arquivo e insere na posição atual
- tecla "a": edita o arquivo e insere na posição seguinte
- tecla "A": edita o arquivo e insere no final da linha
- tecla "x": remove o carácter da posição atual
- tecla "11x": remove 11 caracteres
- tecla "dd": remove uma linha
- tecla "esc": sai do modo de edição
- tecla ":w": grava o arquivo
- tecla ":q": fecha o arquivo
- tecla ":q!": fecha o arquivo sem precisar salvar
- tecla ":wq": grava e fecha o arquivo
- tecla "G": vai para a última linha do arquivo
- tecla "1G": vai para a primeira linha
- tecla "2G": vai para a segunda linha
- tecla "0": vai para o início da linha
- tecla "$": vai para o final da linha
- tecla "yy": copia uma linha
- tecla "2yy": copia duas linhas
- tecla "3yy": copia três linhas
- tecla "p": cola
- tecla "10p": cola dez vezes o mesmo conteúdo
- `/<palavra>` pesquisa dentro do texto, pode utilizar "n" para navegar entre as ocorrências encontradas e "N" para voltar a ocorrência anterior

### Script
`sh <nome do arquivo>`   executa um script
`<diretório>/<nome do arquivo>`   executa um script

### Serviços, processos, programas
`<nome de um programa>`   abre o programa via o terminal, mas o terminal fica travado, roda em foreground (`eclipse`)  
`<nome de um programa> &`   abre o programa via o terminal em background  (ex: `eclipse &`)  
`^z`   para um processo que está rodando no terminal, fica com status parado

`ps`   mostra os processos que estão rodando no bash  
   - `-e`   mostra todos os processos da máquina (ex: `ps -e`)  
   - `-f`   mostra os processos com mais detalhes (ex: `ps -f`)  
   - `| grep <filtro>`   filtra os processos (ex: `ps -ef | grep eclipse`)  

`pstree`   mostra todos os processos em formato árvore  

`top`   mostra o consumo de processamento e memória  
`top -u <usuário>`   mostra o consumo e processamento de memória de um usuário em específico  
`top -p <id processo>`   mostra o consumo e processamento de memória de um processo em específico 

`kill <id do processo>`   mata um processo enviando um sinal de pedido de finalização
`kill -9 <id do processo>`   mata um processo sem enviar sinal
`killall <nome>`   mata um processo por nome, caso exista mais de um mata todos

`jobs`   mostra serviços  
`bg <número do serviço>`   inicia serviço parado em background  
`fg <número do processo>`   traz o serviço para executar como foreground  

`sudo service <nome do serviço> stop`   para um serviço  
`sudo service <nome do serviço> start`   inicia um serviço  
`etc/init.d`   diretório onde fica scripts de programas que iniciam juntamente com o sistema operacional  

### Usuários
`whoami`   mostra usuário logado no bash  
`passwd`   altera senha do usuário logado  
`sudo passwd`   altera senha do usuário root  
`su <usuário>`   troca de usuário  
`adduser <usuário>`   adiciona um novo usuário  

### Variáveis de ambiente
`env`   mostra todas as variáveis de ambiente  
`PATH=$PATH:<diretório>`   atribuir um novo diretório ao PATH apenas para o terminal atual  
`gedit .bashrc &`   abre o arquivo onde deve ser configurado o PATH permanente. Este arquivo está localizado dentro da pasta pessoal do usuário=/home/usuário  

### Instalação de programas apt-get

`sudo apt-get update`   busca atualizações  
`sudo apt-cache search <nome programa>`   busca um programa para ser instalado  
`sudo apt-get install <nome do programa>`   instala um programa encontrado pelo apt-cache search  
`sudo apt-get remove <nome do programa>`   desinstala um programa  

### Instalação de programas .deb
`sudo dpkg -i <pacote.deb>`   instala um pacote  
`sudo dpkg -r <nome do pacote>`   remove um pacote  
`sudo apt-get -f install`   instala dependências se existir na instalação de um .deb  

### Copilando e instalando um programa a partir do código fonte
1 - Fazer o download do arquivo e descompactar  
2 - Entrar na pasta descompactada para executar os comandos a seguir  
3 - Procurar por um arquivo chamado configure, e executar `./configure` ou `sh configure`. Esse arquivo é um script responsável por verificar se no computador tem todas as dependências necessárias para a instalação do programa  
4 - Executar o comando `make` para compilar o projeto
5 - Executar o comando `sudo make install` para instalar

### Acesso SSH
`ssh <usuário>@<IP>`   acessa o servidor de acordo com o IP informado utilizando o usuário  
   - `-X`   permite conectar utilizando recursos gráficos (ex: `ssh -X joao@localhost`)  
   
`scp <nome arquivo ou diretório> <usuário>@<IP>:<diretório>`   copia um diretório ou arquivo para o servidor remoto  
   - `-r`   para copiar de maneira recursiva para quando for um diretório  (ex: `scp -r /projeto-java joao@localhost:/projetos`)

