# 🚀 Maven Day 8 - Maven Plugins Deep Dive

## Objective

Learn:

- Maven Plugins
- Maven Compiler Plugin
- Maven Surefire Plugin
- Maven JAR Plugin
- Spring Boot Maven Plugin
- Plugin Lifecycle
- Jenkins Integration
- Build Troubleshooting

---

# What is a Maven Plugin?

A Maven Plugin performs actual build tasks.

Maven itself does not compile code, run tests, or create JARs.

Instead:

```text
Maven
  ↓
Plugin
  ↓
Task Execution
```

Examples:

- Compile Code
- Run Tests
- Create JAR
- Deploy Artifacts

---

# Maven Build Architecture

```text
pom.xml
    ↓
Maven
    ↓
Plugins
    ↓
Build Tasks
```
---

# Most Important Maven Plugins

## Maven Compiler Plugin

Used for:

```text
Java Compilation
```

Converts:

```text
.java files
```

into:

```text
.class files
```

Example:

```xml
<plugin>

    <groupId>org.apache.maven.plugins</groupId>

    <artifactId>maven-compiler-plugin</artifactId>

    <version>3.14.0</version>

    <configuration>

        <source>17</source>

        <target>17</target>

    </configuration>

</plugin>
```

---

# What Does Compiler Plugin Do?

Input:

```text
PortfolioService.java
```

Output:

```text
PortfolioService.class

Generated in:

```text
target/classes/
```

---

# Maven Surefire Plugin

Used for:

```text
Unit Testing
```

Test Frameworks:

- JUnit
- Mockito

Plugin Example:

```xml
<plugin>

    <groupId>org.apache.maven.plugins</groupId>

    <artifactId>maven-surefire-plugin</artifactId>

    <version>3.5.4</version>

</plugin>
```

Command:

```bash
mvn test
```

---

# What Does Surefire Plugin Do?

Runs:

```text
PortfolioServiceTest.java
```

```

Plugin:

```xml
<plugin>

    <groupId>org.apache.maven.plugins</groupId>

    <artifactId>maven-jar-plugin</artifactId>

</plugin>
```

Command:

```bash
mvn package
```

Output:

```text
target/

portfolio-service-1.0.0.jar
```

---

# Spring Boot Maven Plugin

Most important plugin in enterprise projects.

Plugin:

```xml
<plugin>

    <groupId>org.springframework.boot</groupId>

    <artifactId>spring-boot-maven-plugin</artifactId>

</plugin>
```

Purpose:

```text
Create Executable Spring Boot JAR
```

Without Spring Boot Plugin:

```text
Simple JAR
```

With Spring Boot Plugin:

```text
Executable JAR
```

Run:

```bash
java -jar app.jar
```

---

# Maven Lifecycle and Plugins

When:

```bash
mvn package
```

runs, Maven internally executes:

```text
Compile Phase
      ↓
Compiler Plugin

Test Phase
      ↓
Surefire Plugin

Package Phase
      ↓
JAR Plugin
```

---

# Build Flow

```text
mvn package

      ↓

Compiler Plugin

      ↓

Surefire Plugin

      ↓

JAR Plugin

      ↓

Artifact Generated
```

---

# Plugin Management

Parent POM:

```xml
<pluginManagement>

    <plugins>

        <plugin>

            <groupId>org.apache.maven.plugins</groupId>

            <artifactId>maven-compiler-plugin</artifactId>

            <version>3.14.0</version>

            Surefire Plugin
Spring Boot Plugin
```

Child projects inherit configuration.

---

# Jenkins Integration

Pipeline:

```groovy
pipeline {

    agent any

    stages {

        stage('Build') {

            steps {

                sh 'mvn clean package'

            }

        }

    }

}
```

Behind the scenes:

```text
Compiler Plugin
      ↓
Surefire Plugin
      ↓
Jar Plugin
      ↓
Artifact
```

---

# Common Maven Plugin Commands

## Show Effective POM

```bash
mvn help:effective-pom
```

Purpose:

```text
Show Final POM
After Parent + Child + Inheritance
```

---

## Plugin Description

Compiler Plugin:

```bash
mvn help:describe \
-Dplugin=org.apache.maven.plugins:maven-compiler-plugin
```

mvn help:describe \
-Dplugin=org.apache.maven.plugins:maven-surefire-plugin
```

---

# Common Build Errors

## Java Version Mismatch

Error:

```text
invalid target release
```

Check:

```bash
java -version
```

Verify:

```xml
<source>17</source>

<target>17</target>
```

---

## Test Failure

Command:

```bash
mvn test
```

Failure:

```text
Test Failed
```

Debug:

```bash
mvn test -X
```

---

## Plugin Resolution Failure

Error:

```text
Plugin not found
```

Fix:

```bash
mvn clean install -U
```

---
## Corrupted Local Repository

Fix:

```bash
rm -rf ~/.m2/repository
```

Rebuild:

```bash
mvn clean install
```

---

# Portfolio Service Build Flow

```text
GitHub
   ↓
Jenkins
   ↓
Maven
   ↓
Compiler Plugin
   ↓
Surefire Plugin
   ↓
Jar Plugin
   ↓
portfolio-service.jar
   ↓
Docker Build
   ↓
Kubernetes
```

---

# Interview Questions

## What is a Maven Plugin?

A Maven Plugin performs build-related tasks such as compiling code, running tests, and generating artifacts.

---

## What does Maven Compiler Plugin do?

Compiles Java source files into bytecode (.class files).

---

## Which plugin runs test cases?

```text
Maven Surefire Plugin
```

---

## Which plugin creates JAR files?

```text
Maven JAR Plugin
```

---

## Why use Spring Boot Maven Plugin?

To create executable Spring Boot JARs.

---

## What is pluginManagement?

A Parent POM section used to centrally manage Maven plugin versions and configurations.

---

## What happens during mvn package?

```text
Compiler Plugin
       ↓
Surefire Plugin
       ↓
Jar Plugin
```

---

# Commands Practiced

```bash
mvn help:effective-pom

mvn help:describe \
-Dplugin=org.apache.maven.plugins:maven-compiler-plugin

mvn help:describe \
-Dplugin=org.apache.maven.plugins:maven-surefire-plugin

mvn test

mvn package

mvn clean package
```

---

# Key Learnings

✅ Maven uses Plugins to perform build tasks

✅ Compiler Plugin compiles Java code

✅ Surefire Plugin executes tests

✅ JAR Plugin creates artifacts

✅ Spring Boot Plugin creates executable JARs

✅ pluginManagement centralizes plugin configuration

✅ Jenkins executes Maven plugins during builds

---

## Status

✅ Completed
