# My Project

A simple Java application built with Maven and automated CI/CD using Jenkins.

## Project Overview

This is a basic Java "Hello World" application that demonstrates:
- Maven project structure and configuration
- Automated build and testing with Jenkins CI/CD
- Executable JAR creation
- Git integration and deployment workflow

## Project Structure

```
maven-project/
├── README.md
├── Jenkinsfile                 # Jenkins pipeline configuration
├── pom.xml                     # Maven project configuration
├── src/
│   └── main/
│       └── java/
│           └── com/
│               └── cloudnautic/
│                   └── app/
│                       └── App.java    # Main application class
└── target/                     # Build output directory (generated)
    └── myproject-1.0.jar      # Executable JAR file
```

## Prerequisites

- Java 11 or higher
- Maven 3.6+
- Git

## Building the Project

### Local Build

1. **Clean and compile:**
   ```bash
   mvn clean compile
   ```

2. **Run tests:**
   ```bash
   mvn test
   ```

3. **Create executable JAR:**
   ```bash
   mvn clean package
   ```

4. **Run the application:**
   ```bash
   java -jar target/myproject-1.0.jar
   ```

### Expected Output
```
Hello, World!
```

## Jenkins CI/CD Pipeline

The project includes a Jenkins pipeline (`Jenkinsfile`) with the following stages:

1. **Checkout** - Retrieves code from the Git repository
2. **Build** - Compiles the Java source code
3. **Test** - Runs unit tests (when available)
4. **Package** - Creates the executable JAR file
5. **Deploy** - Copies artifacts to deployment directory

### Jenkins Requirements

- Jenkins server with Maven and JDK tools configured
- Tools must be named:
  - `myMaven` - Maven installation
  - `myJDK` - Java JDK installation

### Pipeline Configuration

The pipeline is configured to:
- Use the `main` branch from the GitHub repository
- Build with Maven using Java 11
- Archive the generated JAR file
- Deploy artifacts to a `deploy/` directory

## Maven Configuration

### Key Dependencies
- **JUnit Jupiter API** (5.7.0) - For unit testing
- **JUnit Jupiter Engine** (5.7.0) - Test execution engine

### Plugins
- **Maven Compiler Plugin** - Java 11 compilation
- **Maven Surefire Plugin** - Test execution
- **Maven JAR Plugin** - Executable JAR creation with manifest

## Development

### Adding New Features

1. Create feature branch:
   ```bash
   git checkout -b feature/your-feature-name
   ```

2. Make changes and test locally:
   ```bash
   mvn clean package
   java -jar target/myproject-1.0.jar
   ```

3. Commit and push:
   ```bash
   git add .
   git commit -m "Add your feature description"
   git push origin feature/your-feature-name
   ```

4. Create pull request to `main` branch

### Adding Tests

Create test files in `src/test/java/com/cloudnautic/app/` following JUnit 5 conventions.

Example test structure:
```java
package com.cloudnautic.app;

import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

class AppTest {
    @Test
    void testMain() {
        // Test implementation
    }
}
```

## Deployment

The Jenkins pipeline automatically:
1. Builds the project on every commit to `main`
2. Runs all tests
3. Creates deployment artifacts
4. Copies JAR to deployment directory

Manual deployment:
```bash
# Build the project
mvn clean package

# Deploy manually
mkdir -p deploy
cp target/*.jar deploy/
```

## Troubleshooting

### Common Issues

1. **"No main manifest attribute" error:**
   - Ensure Maven JAR plugin is configured with main class
   - Rebuild with `mvn clean package`

2. **Jenkins build fails:**
   - Check tool names are `myMaven` and `myJDK`
   - Verify Git repository URL and branch name

3. **Compilation errors:**
   - Ensure Java 11+ is installed
   - Check package declarations match directory structure

### Build Logs

Check Maven output for detailed error information:
```bash
mvn clean package -X  # Debug mode
```

## Contributing

1. Fork the repository
2. Create feature branch
3. Make changes with tests
4. Ensure all builds pass
5. Submit pull request

## License

This project is open source and available under the MIT License.

## Contact

- Repository: https://github.com/atulkamble/maven-project
- Issues: https://github.com/atulkamble/maven-project/issues