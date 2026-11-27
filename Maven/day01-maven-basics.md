# Maven Day 1 - Basics

## What is Maven?

Maven is a build automation and dependency management tool.

## Important File

pom.xml

## Maven Coordinates

### groupId

Organization or Team Name

### artifactId

Application Name

### version

Application Version

### packaging

Artifact Type

## Maven Lifecycle

validate
compile
test
package
verify
install
deploy

## Commands

### Validate

```bash
mvn validate
```

### Compile

```bash
mvn compile
```

### Test

```bash
mvn test
```

### Package

```bash
mvn package
```

### Install

```bash
mvn install
```

## Local Repository

Windows:

```text
C:\Users\<user>\.m2\repository
```

## DevOps Build Flow

GitHub
↓
Jenkins
↓
Maven
↓
JAR
↓
Docker
↓
Kubernetes
