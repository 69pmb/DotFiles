## Maven
- Execute specific test:  
`mvn -Dtest= test`
- Skip test:  
`mvn install -q -Dmaven.test.skip=true`
- Run Spring boot local:  
`mvn spring-boot:run -Dspring-boot.run.profiles=local`  
`mvn spring-boot:run -Drun.jvmArguments="-Dspring.profiles.active=local -Djava.net.useSystemProxies=true" `
- Run liquibase scripts:  
`mvn liquibase:update`

```xml
<plugin>
  <groupId>org.liquibase</groupId>
  <artifactId>liquibase-maven-plugin</artifactId>
  <configuration>
    <propertyFile>src/main/resources/config/application-local.yml</propertyFile>
    <changeLogFile>src/main/resources/db/liquibase/master.xml</changeLogFile>
  </configuration>
</plugin>
```