## Maven
- Execute specific test:  
`mvn -Dtest=my.package.myClassTest test`  
`mvn -Dtest=my.package.myClassTest#myTestCase test`
- Skip test:  
`mvn clean install -DskipTests`  
`mvn install -q -Dmaven.test.skip=true`
- Run Spring boot local:  
`mvn spring-boot:run -Dspring-boot.run.profiles=local`  
`mvn spring-boot:run -Drun.jvmArguments="-Dspring.profiles.active=local`  
- Release:  
Clean workdir, scm tags completed in `pom.xml` and no SNAPSHOT dependencies  
`mvn release:prepare release:perform -Dgoals=deploy -Dtag=<release_version> -DdevelopmentVersion=<next_version>-SNAPSHOT -DreleaseVersion=<release_version> -Darguments=-DskipTests -DskipTests -Dmaven.javadoc.skip=true -DpushChanges=false`
- Run flyway migration:  
`mvn flyway:migrate`  
```xml
<plugin>
  <groupId>org.flywaydb</groupId>
  <artifactId>flyway-maven-plugin</artifactId>
  <configuration>
    <user>usr</user>
    <password>pwd</password>
    <url>jdbc:postgresql://localhost:6002/db</url>
    <locations>
      <location>filesystem:src/main/resources/migration-scripts</location>
    </locations>
  </configuration>
</plugin>
```
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
- Run jacoco coverage unit test:  
`mvn test`  
Reporting can be found in `target/site/jacoco/index.html`

```xml
<plugin>
  <groupId>org.jacoco</groupId>
  <artifactId>jacoco-maven-plugin</artifactId>
  <executions>
    <execution>
      <goals>
        <goal>prepare-agent</goal>
      </goals>
    </execution>
    <execution>
      <id>report</id>
      <phase>test</phase>
      <goals>
        <goal>report</goal>
      </goals>
    </execution>
  </executions>
</plugin>
```
