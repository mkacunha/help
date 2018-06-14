# Comandos Maven

### Comandos relacionados a versão
`mvn --version` exibe a versão corrente do maven.  

### Comandos relacionados à instalação
`mvn clean` limpa artefatos criados pelas builds do maven.  
`mvn install` instala pacotes especifidados no pom.xml no repositório local, e realiza os testes unitários.  
`mvn install -DskipTests` realiza instalação sem execução dos testes unitários.  

### Comandos relacionados à testes 
`mvn test` executa os testes unitários do projeto corrente.  
`mvn -Dtest=<NomeDoArquivo.java> test` executa o testes unitários do arquivo NomeDoArquivo.java.  
`mvn -Dtest=<Pattern*> test` executa os testes unitários de todos os arquivos que iniciam com o nome Pattern.  

### Comandos relacionados à compilação
`mvn compile` compila o código-fonte do projeto atual.  
`mvn package` empacota o código compilado em algum formato de distribuição, ex: JAR.
