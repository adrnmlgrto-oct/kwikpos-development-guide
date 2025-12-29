# Prerequisites

Before you start developing for KwikPOS projects, ensure you have the necessary knowledge and tools.

## Required Knowledge

### Version Control
  - **Git fundamentals**
  - Cloning repositories
  - Creating and managing branches
  - Committing and pushing changes
  - Pull requests and code reviews
  - Resolving merge conflicts
  - Basic Git workflows (feature branches, main branch)

### Frontend Development (Angular)
  - **Node.js** and npm package management
  - **TypeScript** fundamentals
  - Angular framework basics
  - Components, templates, and data binding
  - Services and dependency injection
  - RxJS and Observables
  - HTTP client and API integration
  - Routing and navigation
  - Angular forms and validation

### Flutter Development
  - **Dart programming language** fundamentals
  - Flutter widget system and UI composition
  - State management concepts (setState, Provider, Bloc, etc.)
  - Asynchronous programming (Futures, Streams, async/await)
  - Navigation and routing
  - API integration and HTTP requests
  - Local data persistence (SharedPreferences, SQLite)
  - Flutter app lifecycle and debugging

### Java Development
  - **Core Java** programming
  - Object-oriented programming concepts
  - Java collections and data structures
  - Exception handling
  - File I/O operations
  - Multithreading basics

### Spring Boot Framework
  - **Spring Boot fundamentals**
  - Dependency injection and IoC containers
  - REST API development
  - Spring MVC architecture
  - Configuration management
  - Spring Boot annotations (`@RestController`, `@Service`, `@Bean`, etc.)

### Database
  - **SQL fundamentals**
    - Basic SQL queries (`SELECT`, `INSERT`, `UPDATE`, `DELETE`)
    - Joins and relationships
    - Database design principles
    - Optimizations, indexing, etc.
  - **Relational Databases (RDBMS)**
    - Microsoft SQL Server
    - MySQL
    - SQLite
    - PostgreSQL

### API Development
  - **RESTful API concepts**
  - HTTP methods (`GET`, `POST`, `PUT`, `DELETE`)
  - Request/response structure
  - Status codes
  - API testing with tools like Postman or curl

### Build Tools
  - **Maven**
  - Understanding pom.xml configuration
  - Dependency management
  - Building and packaging applications
  - Maven lifecycle phases

## Development Tools

### Required Software

#### For KwikPOS Live Development
- **JDK 8**
  ```bash
  java -version  # Should show Java 8
  ```
- **Maven 3.6+**
  ```bash
  mvn -version
  ```
- **MySQL 8.0**
  ```bash
  mysql --version
  ```
- **Apache Tomcat 9.0** (for local testing)

#### For KwikPOS API Development
- **JDK 17**
  ```bash
  java -version  # Should show Java 17
  ```
- **Maven 3.8+**
  ```bash
  mvn -version
  ```
- **Apache Tomcat 10.0** (for local testing)

#### For Frontend Development (Angular)
- **Node.js** (LTS version recommended)
  ```bash
  node --version
  npm --version
  ```
- **Angular CLI**
  ```bash
  npm install -g @angular/cli
  ng version
  ```
- **TypeScript**
  ```bash
  npm install -g typescript
  tsc --version
  ```

#### For Flutter Development
- **Flutter SDK** (latest stable version)
  ```bash
  flutter --version
  flutter doctor  # Check installation
  ```
- **Dart SDK** (comes with Flutter)
  ```bash
  dart --version
  ```
- **Android Studio** or **VS Code** with Flutter/Dart plugins
- **Android SDK** (for Android development)
- **Xcode** (for iOS development, macOS only)
- **Chrome** or **Edge** (for web development)

#### General Development Tools
- **Git** (v2.30+)
  ```bash
  git --version
  ```
- **IDE:** IntelliJ IDEA (recommended), Eclipse, or Visual Studio Code with Java Extensions
- **API Testing:** Postman or similar REST API testing tool
- **Database Management:** MySQL 8.0 CE Workbench (*MySQL*), DB Browser (*SQLite*), SQL Server Management Studio 19 (*MS SQL*), etc.

### Recommended IDE Setup

#### IntelliJ IDEA
- Install Spring Boot plugin
- Configure Java SDK for each project (Java 8 for KwikPOS Live, Java 17 for KwikPOS API)
- Enable Maven auto-import
- Install Lombok plugin (if used in projects)

#### Eclipse
- Install Spring Tools Suite (STS)
- Configure JDK versions
- Import as Maven projects

#### VS Code (for Java)
- Install Extension Pack for Java
- Install Spring Boot Extension Pack
- Configure Java SDK paths
- Install Lombok Annotations Support for VS Code

#### VS Code (for Angular)
- Install Angular Language Service extension
- Install Angular Snippets extension
- Install TSLint or ESLint extension
- Install Prettier for code formatting
- Configure TypeScript settings

#### Android Studio (for Flutter)
- Install Flutter and Dart plugins
- Configure Flutter SDK path
- Set up Android emulator or connect physical device
- Enable Dart analysis

#### VS Code (for Flutter)
- Install Flutter extension
- Install Dart extension
- Configure Flutter SDK path
- Set up debugging configurations

## Optional but Helpful

- **Basic Linux/Unix commands** - Helpful for server deployment and troubleshooting
- **AWS familiarity** - Understanding EC2, deployment concepts for KwikPOS Live
- **Docker basics** - May be useful for containerized development environments
- **API documentation tools** - Swagger/OpenAPI experience is a plus

## Verification Checklist

Before proceeding to project setup, verify you have:

**For Backend Development (KwikPOS Live/API):**

- Git installed and configured with your credentials
- Appropriate JDK version installed for your project
- Maven installed and accessible from command line
- MySQL & MS SQL Server installed (for KwikPOS Live development)
- IDE installed with Spring Boot support
- Basic understanding of Spring Boot and REST APIs
- Ability to clone repositories and create branches

**For Frontend Development (Angular):**

- Git installed and configured with your credentials
- Node.js and npm installed
- Angular CLI installed globally
- TypeScript installed and configured
- IDE (VS Code recommended) with Angular extensions
- Basic understanding of Angular and TypeScript
- Familiarity with RxJS and HTTP client

**For Flutter Development:**

- Git installed and configured with your credentials
- Flutter SDK installed and in PATH
- `flutter doctor` shows no critical issues
- IDE (Android Studio or VS Code) with Flutter/Dart plugins installed
- Android SDK installed (for Android development)
- Ability to run Flutter apps on emulator or device
- Basic understanding of Flutter widgets and state management

## Next Steps

Once you've verified all prerequisites, proceed to:

1. [Getting Started](getting-started.md) - Overview of the KwikPOS ecosystem
2. [Projects](projects/kwikpos-live.md) - Detailed project documentation

## Getting Help

If you need help with prerequisites:

- **Tool Installation:** Check official documentation for each tool
- **Java/Spring Boot Concepts:** Review Spring Boot official guides
- **Flutter/Dart Concepts:** Review Flutter official documentation at flutter.dev
- **Git Questions:** Consult Git documentation or your team lead
- **Access Issues:** Contact your team lead for repository credentials
- **Flutter Setup Issues:** Run `flutter doctor -v` for detailed diagnostics
