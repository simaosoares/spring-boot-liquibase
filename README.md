# Spring Boot Liquibase

This sample demonstrates the liquibase auto-configuration support.
The application is based on the official spring boot liquibase sample [spring-boot-sample-liquibase].   

Table of contents:
* [Run the application](#run-the-application)
* [Run production profile](#run-production-profile)
* [Simulate a production hotfix](#simulate-a-production-hotfix)
* [References](#references)

## Run the application

```
mvn spring-boot:run
```

You can look at `http://localhost:8080/actuator/liquibase` to review the list of
scripts.

This sample also enables the H2 console (at `http://localhost:8080/h2-console`)
so that you can review the state of the database (the default jdbc url is
`jdbc:h2:mem:testdb`).

## Run production profile

The application is also configured with a `production` profile to simulate the migrations against to a MySQL database.

```
mvn spring-boot:run -Dspring-boot.run.profiles=prod
```

## Simulate a production hotfix

A branch `hotfix` was created to simulate a production hotfix with databases changes involving database versioning tools like `liquibase`.
In this case a new changeset (the hotfix) will be executed by `liquibase` even if the migrations run "out of order".    

```
git checkout hotfix
```
Run 
```
mvn spring-boot:run -Dspring-boot.run.profiles=prod
```

## References

* https://www.liquibase.org
* https://www.liquibase.org/documentation/maven/
* [spring-boot-sample-liquibase]
* https://spring.io/guides/gs/accessing-data-mysql/

[spring-boot-sample-liquibase]: https://github.com/spring-projects/spring-boot/tree/2.1.x/spring-boot-samples/spring-boot-sample-liquibase
