# autodiff

This is a utility Gradle script for generating Liquibase changelogs for your Hibernate JPA projects. It will

- Spin up a database Docker container
- Apply your current database schema
- Generate a diff changelog using your current JPA entity classes
- Clean up the database container

Currently supported databases:

- PostgreSQL

## Prerequisites

- [Liquibase Gradle Plugin](https://github.com/liquibase/liquibase-gradle-plugin)
- [Docker](https://www.docker.com/)

## Usage

For latest version see https://github.com/erikhofer/autodiff/releases

build.gradle

```
apply from: 'https://raw.githubusercontent.com/erikhofer/autodiff/<version>/autodiff.gradle'
project.autodiff.basePackage = 'com.example.entity'
```

To generate the diff, run

```
gradle autodiff
```

Default changelog locations are based on Spring Boot, you may want to set `project.autodiff.changeLogMaster` and `project.autodiff.changeLogDiff`.

If something goes wrong, the database container is probably still running. You can clean it up with

```
gradle autodiffStopDatabase
```
