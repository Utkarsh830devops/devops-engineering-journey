---

# Why Dependency Scope Matters

Not every dependency should be included in the final application.

Examples:

- Spring Boot
- JUnit
- Oracle JDBC
- Lombok

Maven uses scopes to determine where and how dependencies are used.

---

# Dependency Scopes

## 1. Compile Scope (Default)

Available during:

- Compilation
- Testing
- Runtime

Example:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
    <version>3.5.0</version>
</dependency>
```

Used for:

- Spring Boot
- Logging Libraries
- Utility Libraries

---

## 2. Test Scope

Available only during testing.

Example:

```xml
<dependency>
    <groupId>junit</groupId>
    <artifactId>junit</artifactId>
    <version>4.13.2</version>
    <scope>test</scope>
</dependency>
```

Used for:

- JUnit
- Mockito

Included in Production Artifact?

```text
No
```

---

## 3. Provided Scope

Provided by the container/server.

Example:

```xml
<dependency>
    <groupId>jakarta.servlet</groupId>
    <artifactId>jakarta.servlet-api</artifactId>
    <version>6.0.0</version>
    <scope>provided</scope>
</dependency>
```

Examples:

- Tomcat
- JBoss
- WebLogic

Included in Production Artifact?

```text
No
```

---

## 4. Runtime Scope

Not needed during compilation.

Required only during runtime.

Example:

```xml
<dependency>
    <groupId>com.oracle.database.jdbc</groupId>
    <artifactId>ojdbc11</artifactId>
    <version>23.2.0.0</version>
    <scope>runtime</scope>
</dependency>
```

Examples:

- Oracle JDBC
- MySQL JDBC

---

# Scope Comparison

| Scope | Compile | Runtime | Test |
|---------|---------|---------|---------|
| compile | ✅ | ✅ | ✅ |
| test | ❌ | ❌ | ✅ |
| provided | ✅ | ❌ | ✅ |
| runtime | ❌ | ✅ | ✅ |

---

# Transitive Dependencies

When one dependency automatically pulls other dependencies.

Example:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
    <version>3.5.0</version>
</dependency>
```

Automatically downloads:

```text
spring-core
spring-context
spring-beans
spring-web
spring-webmvc
```

This is called:

```text
Transitive Dependency
```

---

# View Dependency Tree

Command:

```bash
mvn dependency:tree
```

Example Output:

```text
portfolio-service
└── spring-boot-starter-web
    ├── spring-core
    ├── spring-context
    ├── spring-beans
    └── spring-web
```

---

# Maven Build Lifecycle

```text
validate
   ↓
compile
   ↓
test
   ↓
package
   ↓
verify
   ↓
install
   ↓
deploy
```

---

# Compile Phase

Command:

```bash
mvn compile
```

Converts:

```text
.java
```

into:

```text
.class
```

Output Directory:

```text
target/classes
```

---

# Test Phase

Command:

```bash
mvn test
```

Runs:

- JUnit Tests
- Mockito Tests

---

# Package Phase

Command:

```bash
mvn package
```
Creates:

```text
target/
```

Example:

```text
portfolio-service-1.0.0.jar
```

---

# Install Phase

Command:

```bash
mvn install
```

Creates JAR and stores it in:

```text
~/.m2/repository
```

---

# Clean Phase

Command:

```bash
mvn clean
```

Removes:

```text
target/
```

Old build files are deleted.

---

# Most Common Command

```bash
mvn clean package
```

Process:

```text
Delete old build
       ↓
Compile
       ↓
Test
       ↓
Create JAR
```

---

# Real Jenkins Pipeline Example

```groovy
stage('Build') {
    sh 'mvn clean package'
}
```

Output:

```text
target/
 └── portfolio-service-1.0.0.jar
```

Then:

```text
Docker Build
      ↓
Docker Image
      ↓
Kubernetes Deployment
```

---

# Common Build Issues

## Dependency Not Found

Error:

```text
Could not resolve dependency
```

Check:

```bash
mvn dependency:tree
```

---

## Java Version Issue

Error:

```text
Unsupported class version
```

Verify:

```bash
java -version
```

---

## Corrupted Local Repository

Fix:

```bash
rm -rf ~/.m2/repository
```

Then:

```bash
mvn clean install
```

---

# Real DevOps Flow

GitHub
↓
Jenkins
↓
Maven Build
↓
JAR
↓
Docker Build
↓
Container Registry
↓
Kubernetes
↓
Production

---

# Interview Questions

## What is Dependency Scope?

Dependency scope determines when a dependency is available during build and runtime.

---

## Difference between compile and test scope?

Compile:

```text
Available everywhere
```

Test:

```text
Available only during testing
```

---

## What are Transitive Dependencies?

Dependencies automatically downloaded because another dependency requires them.

---

## What does mvn clean package do?

```text
Deletes old build
Compiles source code
Runs tests
Creates JAR
```

---

## Where does Maven store dependencies?

```text
~/.m2/repository
```

---

## Which Maven command is most commonly used in Jenkins?

```bash
mvn clean package
```

---

# Key Learnings

✅ Dependency Scope controls dependency visibility

✅ compile is the default scope

✅ test scope is used for testing libraries

✅ runtime scope is used for database drivers

✅ Transitive dependencies are downloaded automatically

✅ mvn clean package is the most common CI/CD build command

✅ Jenkins uses Maven to build artifacts before Docker image creation

---

## Status

✅ Completed
