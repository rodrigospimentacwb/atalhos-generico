# Atalhos genéricos ainda sem organização no git


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
