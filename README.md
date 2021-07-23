# Atalhos/Comandos genéricos ainda sem organização no git


## Maven

- Para build sem testes:
 
```
mvn clean install -DskipTests=true
```

- Para ver a arvore de dependencias:

```
mvn dependecy:tree // So mostrar
mvn dependency:tree --log-file log.txt // Criar um arquivo
mvn dependency:tree -Dincludes=*:hibernate-core // filtrar por
```

- Artifact upload jar:

```
mvn deploy:deploy-file -DgroupId=<group-id> \
  -DartifactId=<artifact-id> \
  -Dversion=<version> \
  -Dpackaging=<type-of-packaging> \
  -Dfile=<path-to-file> \
  -DrepositoryId=<id-to-map-on-server-section-of-settings.xml> \
  -Durl=<url-of-the-repository-to-deploy>
```
Ex:
```
-mvn deploy:deploy-file 
	-DgroupId=pepper.com.exception
	-DartifactId=exception 
	-Dversion=0.0.1
	-Dpackaging=jar 
	-Dfile={caminho_arquivo}\exception-0.0.1.jar 
	-DrepositoryId=repo-aws-code-artifcat
	-Durl=https://pepper-repo-111111111.d.codeartifact.us-east-1.amazonaws.com/maven/internal-legacy/
```

Obs: entrar no artifact e ver se tem o pom dentro da versao da lib.
