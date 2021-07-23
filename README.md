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

## Analisar Heap Dump e Thread Dump

### Verificar consumo de memoria Heap Dump

 * Dentro de uma pod:

	```$ apt update && apt install openjdk-8-jdk openjdk-8-dbg```

	```$ jmap -dump:live,format=b,file=/tmp/dump.hprof PID_PROCESSO_JAVA```

* Copiar o heap dump para maquina local

	```$ kubectl cp <namespace>/<Pod name>:/tmp/dump.hprof ./dump.hprof```


* Usar o VisualVm para visualizar

	https://visualvm.github.io/

### Para thread dump:

 * Dentro de uma pod:
 
	```$ jstack -l 1  > /tmp/dump.hprof```

 * Para analisar usar: 
 
 	https://fastthread.io/

Referência: https://www.zup.com.br/blog/ferramentas-de-troubleshooting-em-aplicacoes-jvm
