# Comandos Docker

### Comandos relacionados à informações

`docker version`   exibe a versão do docker que está instalada.  
`docker inspect ID_CONTAINER`    retorna diversas informações sobre o container.  
`docker ps`   exibe todos os containers em execução no momento.  
`docker ps -a`   exibe todos os containers, independente de estarem em execução ou não.   
`docker ps -q`   exibe todos os ID's dos containers em execução.  
`docker images`   exibe todas as imagens.   
`docker images -q`   exibe todos os ID's das imagens.  



### Comandos relacionados à execução

`docker run NOME_DA_IMAGEM`   cria um container com a respectiva imagem passada como parâmetro.  
`docker run --rm NOME_DA_IMAGEM`   criar um container que será removido automaticamente quando sair.  
`docker run -it NOME_DA_IMAGEM`   conecta o terminal que estamos utilizando com o do container.  
`docker run -d -P --name NOME dockersamples/static-site`   ao executar, dá um nome ao container.  
`docker run -d -p 12345:80 dockersamples/static-site`   define uma porta específica para ser atribuída à porta 80 do container, neste caso 12345.  
`docker run -v "CAMINHO_VOLUME" NOME_DA_IMAGEM`   cria um volume no respectivo caminho do container.  
`docker run -it --name NOME_CONTAINER --network NOME_DA_REDE NOME_IMAGEM`   cria um container especificando seu nome e qual rede deverá ser usada.  

*O parâmetro `-d` utilizado juntamente com `run` significa que irá rodar em background e não vai travar o terminal até que o container morra.*  

### Comandos relacionados à inicialização/interrupção

`docker start ID_CONTAINER`   inicia o container com id em questão.  
`docker start -a -i ID_CONTAINER`   inicia o container com id em questão e integra os terminais, além de permitir interação entre ambos.  
`docker stop ID_CONTAINER`   interrompe o container com id em questão.  
`docker stop $(docker ps -a -q)`   interrompe a execução de todos os containers. 

### Comandos relacionados à remoção

`docker rm ID_CONTAINER`   remove o container com id em questão.  
`docker container prune`   remove todos os containers que estão parados.  
`docker rmi NOME_DA_IMAGEM`   remove a imagem passada como parâmetro.  
`docker rm $(docker ps -a -q)`   remove todos os containers. 
`docker rmi $(docker images -q)`   remove todas as imagens. 
### Comandos relacionados à construção de Dockerfile

`docker build -f Dockerfile`   cria uma imagem a partir de um Dockerfile.  
`docker build -f Dockerfile -t NOME_USUARIO/NOME_IMAGEM`   constrói e nomeia uma imagem não-oficial.  
`docker build -f Dockerfile -t NOME_USUARIO/NOME_IMAGEM CAMINHO_DOCKERFILE`   constrói e nomeia uma imagem não-oficial informando o caminho para o Dockerfile.  

### Comandos relacionados ao Docker Hub

`docker login`   inicia o processo de login no Docker Hub.  
`docker push NOME_USUARIO/NOME_IMAGEM`   envia a imagem criada para o Docker Hub.  
`docker pull NOME_USUARIO/NOME_IMAGEM`   baixa a imagem desejada do Docker Hub.  


### Comandos relacionados à rede

`hostname -i`   mostra o ip atribuído ao container pelo docker (funciona apenas dentro do container).  
`docker network create --driver bridge NOME_DA_REDE`   cria uma rede especificando o driver desejado

### Comandos relacionados à docker-compose

`docker-compose build -d`   Cria as imagens de acordo com o arquivo docker-compose.yaml  
`docker-compose up -d`   Cria os serviços configurados no docker-compose.yaml  
`docker-compose ps`   Mostras os serviços que estão rodando  
`docker-compose down`   Para todos os serviços e removem os containers  
`docker-compose restart` Reinicia os containers, é como se tivesse executado os comandos `docker-compose down` e `docker-compose up`  

### Imagens

#### Postgres

`docker run --name postgres-db -p 5432:5432 \
-e POSTGRES_PASSWORD=1234 \
-e POSTGRES_USER=postgres-user \
-e POSTGRES_DB=postgres_db \
-d postgres:latest`  

Cria um container do Postgres com o nome `postgres-db`, usuário `postgres-user`, senha `1234`, banco de dados `postgres_db` e expõe a porta `5432` para conexão externa.  

#### MySQL

`docker run --name mysql-db -p 3306:3306 \
-e MYSQL_PASSWORD=1234 \
-e MYSQL_USER=mysql-user \
-e MYSQL_DATABASE=mysql_db \
-d mysql/mysql-server:latest` 

Cria um container do MySQL com o nome `mysql-db`, usuário `mysql-user`, senha `1234`, banco de dados `mysql_db` e expõe a porta `3306` para conexão externa.  

#### SQL Server 2017

`docker run --name mssql-server-db -p 1433:1433 -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=!Q@W#E$R%t' -d microsoft/mssql-server-linux:2017-latest`  

Cria um container do SQL Server 2017 com o nome `mssql-server-db`, senha `!Q@W#E$R%t` e expõe a porta `1433` para conexão externa.
A variável de ambiente `ACCEPT_EULA=Y` significa que aceita o contrato de licença do SQL Server, e a variável `SA_PASSWORD` define uma senha para acesso ao banco de dados. Não existe variável de ambiente para definir o nome do banco de dados e usuário na criação do container. Ao executar `run` na imagem do SQL Server, é criado automaticamente o banco de dados `master` e o usuário `sa`.  
