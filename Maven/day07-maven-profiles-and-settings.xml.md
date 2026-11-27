# 🚀 Maven Day 7 - Maven Profiles & settings.xml

## Objective

Learn:

- Maven Profiles
- DEV / UAT / PROD Builds
- Environment Specific Configurations
- settings.xml
- Jenkins Parameterized Builds
- Enterprise Maven Best Practices

---

# Problem Statement

A Portfolio Management Platform has multiple environments:

```text
DEV
UAT
PROD
```

Each environment has different configurations.

Example:

DEV
↓
dev-oracle.company.com

UAT
↓
uat-oracle.company.com

PROD
↓
prod-oracle.company.com
```

Question:

How can the same application be built differently for each environment?

Answer:

```text
Maven Profiles
```

---

# What is a Maven Profile?

A Maven Profile provides environment-specific configuration.

Profiles help customize:

- Database URL
- Environment Variables
- Build Parameters
- Plugin Configuration

---


```xml
<profile>

    <id>dev</id>

    <properties>

        <environment.name>DEV</environment.name>

        <db.url>
            dev-oracle.company.com
        </db.url>

    </properties>

</profile>
```

---

# UAT Profile

```xml
<profile>

    <id>uat</id>

    <properties>

        <environment.name>UAT</environment.name>

        <db.url>
            uat-oracle.company.com
        </db.url>

    </properties>

</profile>
```

---

# PROD Profile

```xml
<profile>

    <id>prod</id>

    <properties>

        <environment.name>PROD</environment.name>

        <db.url>
            prod-oracle.company.com
        </db.url>

    </properties>

</profile>
```

---

# Complete Profile Example

```xml
<profiles>

    <profile>

        <id>dev</id>

        <properties>

            <environment.name>DEV</environment.name>

        </properties>

    </profile>

    <profile>

        <id>uat</id>

        <properties>

            <environment.name>UAT</environment.name>

        </properties>

    </profile>

    <profile>

        <id>prod</id>

        <properties>

            <environment.name>PROD</environment.name>

        </properties>

    </profile>

</profiles>
```

---

# Activating Profiles

## Build DEV

```bash
mvn clean package -Pdev
```

---

## Build UAT

```bash
mvn clean package -Puat
```

---

## Build PROD

```bash
mvn clean package -Pprod
```

---
# View Active Profile

Command:

```bash
mvn help:active-profiles
```

Example:

```text
Active Profiles:

dev
```

---

# View All Profiles

Command:

```bash
mvn help:all-profiles
```

Displays:

```text
dev
uat
prod
```

---

# What is settings.xml?

Maven configuration file.

Stores:

- Credentials
- Repository Information
- Proxy Configuration
- Mirrors
- Profiles

---

# Location of settings.xml

Windows:

```text
C:\Users\<username>\.m2\settings.xml
```

Linux:

```text
~/.m2/settings.xml
```

---

# Why Use settings.xml?

Avoid storing credentials inside:

```xml
pom.xml
```

Bad Example:

```xml
<password>admin123</password>
```

Good Practice:

```text
Store credentials in settings.xml
```

---

# Example settings.xml

```xml
<settings>

    <servers>

        <server>

            <id>nexus</id>

            <username>admin</username>

            <password>******</password>

        </server>

    </servers>

</settings>
```

---

# Jenkins Integration

Real Pipeline:

```groovy
pipeline {

    agent any

    parameters {

        choice(
            name: 'ENV',
            choices: ['dev','uat','prod']
        )

    }
    stages {

        stage('Build') {

            steps {

                sh "mvn clean package -P${ENV}"

            }
 }

    }

}
```

---

# Enterprise Build Flow

```text
Developer
      ↓
GitHub
      ↓
Jenkins
      ↓
Select Environment
      ↓
Maven Profile
      ↓
Build Artifact
      ↓
Deploy
```

---

# Portfolio Management Platform Example

Services:

```text
portfolio-service

trade-service

client-service

risk-engine
```

Build for DEV:

```bash
mvn clean package -Pdev
```

Build for UAT:

```bash
mvn clean package -Puat
```

Build for PROD:

```bash
mvn clean package -Pprod
```

---

# Common Commands

## Show Active Profiles

```bash
mvn help:active-profiles
```

---

## Show All Profiles

```bash
mvn help:all-profiles
```

---

## Build Using Profile

```bash
mvn clean package -Pdev

mvn clean package -Puat

mvn clean package -Pprod
```

---

# Interview Questions

## What is a Maven Profile?

A Maven Profile provides environment-specific configurations and build settings.

---

## Why use Maven Profiles?

To support:

```text
DEV
UAT
PROD
```

using the same codebase.

---

## How do you activate a Maven Profile?

```bash
mvn clean package -Pdev
```

---

## What is settings.xml?

A Maven configuration file used for credentials, repositories, mirrors, and profile configurations.

---

## Where is settings.xml located?

Windows:

```text
C:\Users\<user>\.m2\settings.xml
```

Linux:

```text
~/.m2/settings.xml
```

---

## Why store credentials in settings.xml?

To prevent exposing secrets in source code repositories.

---

# Real DevOps Use Case

Environment-specific deployment:

```text
DEV Build
 ↓
mvn clean package -Pdev
```

```text
UAT Build
 ↓
mvn clean package -Puat
```

```text
PROD Build
 ↓
mvn clean package -Pprod
```

Same source code.

Different configurations.

---

# Key Learnings

✅ Maven Profiles support environment-specific builds

✅ DEV, UAT, and PROD can use the same codebase

✅ Profiles are activated using `-P`

✅ settings.xml stores credentials securely

✅ Jenkins commonly uses Maven profiles

✅ Enterprise deployments heavily rely on profiles

---

# Commands Practiced

```bash
mvn help:all-profiles

mvn help:active-profiles

mvn clean package -Pdev

mvn clean package -Puat

mvn clean package -Pprod
```

---

## Status

✅ Completed

