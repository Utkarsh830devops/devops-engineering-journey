# 🚀 Maven Day 6 - Dependency Management & Plugin Management

## Objective

Learn:

- dependencyManagement
- pluginManagement
- Centralized Version Control
- Maven Compiler Plugin
- Enterprise Maven Best Practices

---

# Problem Statement

Consider a Portfolio Management Platform with:

```text
portfolio-service
trade-service
client-service
risk-engine
```

Each service uses:

```text
Spring Boot
JUnit
Maven Compiler Plugin
```

Without centralized management:

```text
portfolio-service     → Spring 3.5.0
trade-service         → Spring 3.5.0
client-service        → Spring 3.5.0
risk-engine           → Spring 3.5.0
```

Updating versions becomes difficult.

---

# Solution

Use Parent POM with:

```xml
<dependencyManagement>
</dependencyManagement>
```

and

```xml
<pluginManagement>
</pluginManagement>
```

---



# What is dependencyManagement?

dependencyManagement is used to centrally manage dependency versions.

Example:

```xml
<dependencyManagement>

    <dependencies>

        <dependency>

            <groupId>org.springframework.boot</groupId>

            <artifactId>spring-boot-starter-web</artifactId>

            <version>3.5.0</version>

        </dependency>

    </dependencies>

</dependencyManagement>
```

---

# Child POM Example

Without Dependency Management:

```xml
<dependency>

    <groupId>org.springframework.boot</groupId>

    <artifactId>spring-boot-starter-web</artifactId>

    <version>3.5.0</version>

</dependency>
```

With Dependency Management:

```xml
<dependency>

    <groupId>org.springframework.boot</groupId>

    <artifactId>spring-boot-starter-web</artifactId>

</dependency>
```

Version is inherited from Parent POM.

---

# Enterprise Benefit

Change version once:

```xml
<spring.boot.version>3.6.0</spring.boot.version>
```

All services automatically inherit.

---

# Properties Section

Parent POM:

```xml
<properties>

    <java.version>17</java.version>

    <spring.boot.version>3.5.0</spring.boot.version>

    <junit.version>5.13.0</junit.version>

</properties>
```

Usage:

```xml
<version>${spring.boot.version}</version>
```

---

# What is pluginManagement?

pluginManagement is used to centrally manage Maven plugins.

Example:

```xml
<pluginManagement>

    <plugins>

        <plugin>

            <groupId>org.apache.maven.plugins</groupId>

            <artifactId>maven-compiler-plugin</artifactId>

            <version>3.14.0</version>

        </plugin>

    </plugins>

</pluginManagement>
```

---

# Why Plugin Management?

Without pluginManagement:

Every service defines:

```xml
maven-compiler-plugin
```

Multiple times.

With pluginManagement:

```text
Parent POM controls everything
```

---

# Maven Compiler Plugin

Purpose:

```text
Compile Java Source Code
```

Converts:

```text
.java
```

into:

```text
.class
```

Example:

```xml
<plugin>

    <groupId>org.apache.maven.plugins</groupId>

    <artifactId>maven-compiler-plugin</artifactId>

    <version>3.14.0</version>

</plugin>
```

---

# Important Maven Plugins

## Maven Compiler Plugin

Used for:

```text
Java Compilation
```

---

## Maven Surefire Plugin

Used for:

```text
JUnit Execution
Unit Testing
```

Runs:

```bash
mvn test
```

---

## Maven JAR Plugin

Used for:

```text
JAR Generation
```

---

## Spring Boot Maven Plugin

Used for:

```text
Spring Boot Packaging
```

Produces:

```text
portfolio-service.jar
```

---

# Enterprise Parent POM Example

```xml
<properties>

    <java.version>17</java.version>

    <spring.boot.version>3.5.0</spring.boot.version>

    <junit.version>5.13.0</junit.version>

</properties>

<dependencyManagement>

    <dependencies>

        <dependency>

            <groupId>org.springframework.boot</groupId>

            <artifactId>spring-boot-starter-web</artifactId>

            <version>${spring.boot.version}</version>

        </dependency>

    </dependencies>

</dependencyManagement>

<build>

    <pluginManagement>

        <plugins>

            <plugin>

                <artifactId>maven-compiler-plugin</artifactId>

                <version>3.14.0</version>

            </plugin>

        </plugins>

    </pluginManagement>

</build>
```

---

# Portfolio Management Platform Structure

```text
portfolio-management-platform

│
├── pom.xml
│
├── services
│   ├── portfolio-service
│   ├── trade-service
│   ├── client-service
│   └── risk-engine
```

Parent POM controls:

```text
Java Version
Dependency Versions
Plugin Versions
Build Standards
```

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

Flow:

```text
Parent POM
      ↓
Dependencies
      ↓
Plugins
      ↓
Build
```

---

# Difference: dependencies vs dependencyManagement

| dependencies | dependencyManagement |
|-------------|---------------------|
| Adds dependency | Manages dependency versions |
| Downloads dependency | Does not automatically add dependency |
| Used directly in child | Supports child inheritance |

---

# Difference: plugins vs pluginManagement

| plugins | pluginManagement |
|----------|------------------|
| Plugin executes directly | Only defines configuration |
| Used in project build | Used for inheritance |
| Immediate effect | Child projects reuse settings |

---

# Interview Questions

## What is dependencyManagement?

A Maven section used to centrally manage dependency versions for child projects.

---

## What is pluginManagement?

A Maven section used to centrally manage plugin versions and configurations.

---

## Why use dependencyManagement?

To maintain consistent dependency versions across multiple services.

---

## Why use pluginManagement?

To maintain consistent plugin versions and build configurations.

---

## What is Maven Compiler Plugin?

A Maven plugin used to compile Java source files into bytecode.

---

## Why use a Parent POM?

- Centralized configuration
- Consistent versions
- Shared plugins
- Easier maintenance

---

# Real DevOps Workflow

GitHub
↓
Jenkins
↓
Parent POM
↓
Dependencies
↓
Plugins
↓
Build
↓
JAR
↓
Docker
↓
Kubernetes

---

# Key Learnings

✅ dependencyManagement manages dependency versions

✅ pluginManagement manages plugin versions

✅ Parent POM centralizes project configuration

✅ Maven Compiler Plugin handles Java compilation

✅ Enterprises manage all services through a Parent POM

✅ Jenkins automatically uses Parent POM during Maven builds

---

## Commands Practiced

```bash
mvn validate

mvn dependency:tree

mvn clean package

mvn clean install
```

---

## Status

✅ Completed
