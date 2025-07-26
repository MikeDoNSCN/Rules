# Universal Coding Standard

## Project Overview
This coding standard provides a framework for consistent, maintainable, and scalable software development across any technology stack or project type. Adapt these guidelines to your specific needs while maintaining the core principles.

## Directory Structure Principles

### Standard Layout
```
project-name/
├── README.md                       # Project overview and setup
├── .gitignore                      # Version control ignore rules
├── .env.example                    # Environment variables template
├── CHANGELOG.md                    # Version history
├── LICENSE                         # License information
├── src/                           # Source code
│   ├── core/                      # Core business logic
│   ├── api/                       # API/interface layer
│   ├── services/                  # Service layer
│   ├── models/                    # Data models/entities
│   ├── utils/                     # Utility functions
│   └── config/                    # Configuration files
├── tests/                         # All test files
│   ├── unit/                      # Unit tests
│   ├── integration/               # Integration tests
│   └── e2e/                       # End-to-end tests
├── docs/                          # Documentation
│   ├── api.md                     # API documentation
│   ├── setup.md                   # Setup instructions
│   └── architecture.md            # System architecture
├── scripts/                       # Build/deployment scripts
├── assets/                        # Static assets (if applicable)
├── config/                        # Configuration files
├── logs/                          # Log files (gitignored)
└── dist/                          # Build output (gitignored)
```

### Technology-Specific Adaptations
- **Web Frontend**: Add `public/`, `components/`, `hooks/`, `contexts/`
- **Backend API**: Add `controllers/`, `middleware/`, `routes/`
- **Mobile**: Add `screens/`, `navigation/`, `components/`
- **Desktop**: Add `views/`, `controllers/`, `resources/`
- **Data Science**: Add `notebooks/`, `data/`, `models/`, `pipelines/`

## Naming Conventions

### Files and Directories
- Use lowercase with hyphens for directories: `user-management/`
- Use descriptive names: `user-authentication.js` not `ua.js`
- Keep names under 50 characters when possible
- Use consistent extensions for file types

### Language-Specific Conventions

#### Python
```python
# Files: snake_case
user_service.py
email_validator.py

# Classes: PascalCase
class UserService:
class EmailValidator:

# Functions/Variables: snake_case
def validate_email():
user_count = 0

# Constants: UPPER_SNAKE_CASE
MAX_RETRY_COUNT = 3
DEFAULT_TIMEOUT = 30
```

#### JavaScript/TypeScript
```javascript
// Files: camelCase or kebab-case
userService.js
user-service.js

// Classes: PascalCase
class UserService {}
class EmailValidator {}

// Functions/Variables: camelCase
function validateEmail() {}
const userCount = 0;

// Constants: UPPER_SNAKE_CASE
const MAX_RETRY_COUNT = 3;
const DEFAULT_TIMEOUT = 30;
```

#### Java/C#
```java
// Files: PascalCase (matching class name)
UserService.java
EmailValidator.cs

// Classes: PascalCase
public class UserService {}

// Methods/Variables: camelCase
public void validateEmail() {}
private int userCount = 0;

// Constants: UPPER_SNAKE_CASE
public static final int MAX_RETRY_COUNT = 3;
```

## Code Style Guidelines

### Universal Principles
1. **Consistency**: Follow the same patterns throughout the project
2. **Readability**: Code should tell a story
3. **Simplicity**: Prefer simple solutions over complex ones
4. **DRY**: Don't Repeat Yourself
5. **SOLID**: Follow SOLID principles for object-oriented code

### Function/Method Structure
```python
def function_name(param1: Type, param2: Type) -> ReturnType:
    """
    Brief description of what the function does.
    
    Args:
        param1: Description of parameter
        param2: Description of parameter
        
    Returns:
        Description of return value
        
    Raises:
        ExceptionType: When this exception occurs
    """
    # Implementation
    pass
```

### Class Structure
```python
class ClassName:
    """
    Brief description of the class purpose.
    
    Attributes:
        attribute1: Description
        attribute2: Description
    """
    
    def __init__(self, param1: Type):
        """Initialize the class."""
        self.attribute1 = param1
        
    def public_method(self) -> Type:
        """Public method description."""
        pass
        
    def _private_method(self) -> Type:
        """Private method description."""
        pass
```

### Code Formatting
- **Indentation**: Use consistent indentation (4 spaces or tabs, never mix)
- **Line Length**: Maximum 80-120 characters per line
- **Blank Lines**: Use blank lines to separate logical sections
- **Comments**: Write comments that explain "why", not "what"

## Documentation Standards

### README Template
```markdown
# Project Name

## Description
Brief description of what the project does.

## Installation
Step-by-step installation instructions.

## Usage
Basic usage examples.

## Configuration
Environment variables and configuration options.

## API Reference
Link to API documentation (if applicable).

## Contributing
How to contribute to the project.

## License
License information.
```

### Code Documentation
- **File Headers**: Include purpose, author, and creation date
- **Function Documentation**: Document all public functions
- **Complex Logic**: Add inline comments for complex algorithms
- **API Documentation**: Use tools like Swagger, JSDoc, or Sphinx

### Documentation Types
1. **README**: Project overview and quick start
2. **API Docs**: Detailed API reference
3. **Architecture**: System design and decisions
4. **Setup Guide**: Detailed installation and configuration
5. **User Guide**: How to use the application
6. **Developer Guide**: How to contribute and extend

## Testing Conventions

### Test Structure
```python
# test_module_name.py
import pytest
from src.module import ClassName

class TestClassName:
    """Test class for ClassName"""
    
    @pytest.fixture
    def instance(self):
        """Create test instance"""
        return ClassName(test_param)
        
    def test_method_success(self, instance):
        """Test successful operation"""
        # Arrange
        input_data = create_test_data()
        
        # Act
        result = instance.method(input_data)
        
        # Assert
        assert result.is_valid
        assert result.value == expected_value
        
    def test_method_with_invalid_input(self, instance):
        """Test with invalid input"""
        # Test implementation
```

### Testing Guidelines
- **Naming**: `test_<method>_<condition>_<expected_result>`
- **Structure**: Follow Arrange-Act-Assert pattern
- **Coverage**: Aim for 80%+ code coverage
- **Independence**: Tests should not depend on each other
- **Speed**: Unit tests should run quickly (< 1 second each)

### Test Types
1. **Unit Tests**: Test individual functions/methods
2. **Integration Tests**: Test component interactions
3. **End-to-End Tests**: Test complete user workflows
4. **Performance Tests**: Test system performance
5. **Security Tests**: Test for vulnerabilities

## Error Handling

### Exception Hierarchy
```python
# Define custom exceptions
class ProjectError(Exception):
    """Base exception for this project"""
    pass

class ValidationError(ProjectError):
    """Raised when validation fails"""
    pass

class ConfigurationError(ProjectError):
    """Raised when configuration is invalid"""
    pass
```

### Error Handling Patterns
```python
try:
    result = risky_operation()
except SpecificError as e:
    logger.error(f"Known error occurred: {e}")
    # Handle gracefully
    return default_value
except Exception as e:
    logger.exception("Unexpected error occurred")
    # Log and re-raise or handle appropriately
    raise
finally:
    # Cleanup code
    cleanup_resources()
```

### Error Response Format (APIs)
```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid input provided",
    "details": {
      "field": "email",
      "reason": "Invalid email format"
    },
    "timestamp": "2025-07-26T10:30:00Z"
  }
}
```

## Version Control (Git)

### Branch Naming
- **Feature**: `feature/user-authentication`
- **Bug Fix**: `fix/login-validation-error`
- **Hotfix**: `hotfix/security-patch`
- **Release**: `release/v1.2.0`
- **Refactor**: `refactor/database-layer`

### Commit Message Format
```
<type>(<scope>): <subject>

<body>

<footer>
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, etc.)
- `refactor`: Code refactoring
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

**Example:**
```
feat(auth): add JWT token validation

- Implement JWT middleware for route protection
- Add token expiration handling
- Update user authentication flow
- Add comprehensive test coverage

Closes #123
Breaking Change: Auth header format changed
```

## Configuration Management

### Environment Variables
```bash
# .env.example
# Database
DATABASE_URL=postgresql://localhost:5432/myapp
DATABASE_POOL_SIZE=10

# API
API_PORT=3000
API_HOST=localhost
JWT_SECRET=your-secret-key

# Logging
LOG_LEVEL=info
LOG_FORMAT=json

# External Services
REDIS_URL=redis://localhost:6379
EMAIL_SERVICE_API_KEY=your-api-key
```

### Configuration Patterns
1. **Environment-based**: Different configs for dev/staging/prod
2. **Hierarchical**: Default → Environment → Local overrides
3. **Validation**: Validate configuration on startup
4. **Documentation**: Document all configuration options

## Security Practices

### Input Validation
- Validate all user inputs
- Use parameterized queries for databases
- Sanitize data before processing
- Implement rate limiting

### Authentication & Authorization
- Use strong password policies
- Implement proper session management
- Use HTTPS in production
- Follow principle of least privilege

### Data Protection
- Encrypt sensitive data at rest
- Use secure communication protocols
- Implement proper logging (avoid logging secrets)
- Regular security audits

## Performance Guidelines

### General Principles
- **Measure First**: Profile before optimizing
- **Async Operations**: Use async/await for I/O operations
- **Caching**: Implement caching strategically
- **Database**: Optimize queries and use indexes
- **Memory**: Monitor memory usage and prevent leaks

### Performance Checklist
- [ ] Database queries optimized
- [ ] Appropriate caching implemented
- [ ] Async operations used for I/O
- [ ] Memory leaks checked
- [ ] Load testing performed
- [ ] Monitoring in place

## Logging Standards

### Log Levels
```python
logger.debug("Detailed debugging information")
logger.info("General information about application flow")
logger.warning("Warning about potential issues")
logger.error("Error that prevented operation from completing")
logger.critical("Critical error that may cause application to terminate")
```

### Log Format
```python
import logging

logging.basicConfig(
    format='%(asctime)s - %(name)s - %(levelname)s - %(funcName)s:%(lineno)d - %(message)s',
    level=logging.INFO
)
```

### What to Log
- **Application startup/shutdown**
- **User authentication events**
- **Error conditions**
- **Performance metrics**
- **Security events**
- **Business logic milestones**

### What NOT to Log
- Passwords or secrets
- Personal identifiable information (PII)
- Credit card numbers
- Session tokens

## Development Workflow

### Setup Checklist
- [ ] Development environment configured
- [ ] Dependencies installed
- [ ] Environment variables set
- [ ] Database migrations run
- [ ] Tests passing
- [ ] Linting/formatting tools configured

### Code Review Checklist
- [ ] Code follows style guidelines
- [ ] All tests pass
- [ ] Documentation updated
- [ ] No hardcoded values
- [ ] Error handling implemented
- [ ] Security considerations addressed
- [ ] Performance impact considered

### Pre-deployment Checklist
- [ ] All tests pass (unit, integration, e2e)
- [ ] Code review completed
- [ ] Documentation updated
- [ ] Environment variables configured
- [ ] Database migrations ready
- [ ] Monitoring configured
- [ ] Rollback plan prepared

## Tool Recommendations

### Code Quality
- **Linting**: ESLint (JS), Pylint (Python), RuboCop (Ruby)
- **Formatting**: Prettier (JS), Black (Python), Gofmt (Go)
- **Type Checking**: TypeScript, mypy (Python), Flow

### Testing
- **Unit Testing**: Jest (JS), pytest (Python), JUnit (Java)
- **E2E Testing**: Cypress, Selenium, Playwright
- **API Testing**: Postman, Insomnia, REST Assured

### CI/CD
- **Platforms**: GitHub Actions, GitLab CI, Jenkins
- **Containerization**: Docker, Kubernetes
- **Monitoring**: DataDog, New Relic, Prometheus

## Adaptation Guidelines

### For Small Teams (1-5 developers)
- Simplify documentation requirements
- Focus on essential tests
- Use automated tools for code formatting
- Prioritize code review over formal processes

### For Large Teams (10+ developers)
- Enforce strict coding standards
- Implement comprehensive testing
- Use detailed documentation
- Establish formal review processes

### For Different Project Types
- **Web Applications**: Add frontend-specific guidelines
- **APIs**: Focus on endpoint design and documentation
- **Libraries**: Emphasize public API design
- **Data Science**: Add notebook and data handling guidelines
- **Mobile Apps**: Include platform-specific conventions

## Quick Reference Commands

```bash
# Common development commands (adapt to your stack)

# Setup
./scripts/setup.sh

# Development
npm start / python app.py / mvn spring-boot:run

# Testing
npm test / pytest / mvn test

# Linting
npm run lint / flake8 . / mvn checkstyle:check

# Building
npm run build / python setup.py build / mvn package

# Deployment
./scripts/deploy.sh
```

---

**Remember**: This standard is a starting point. Adapt it to your team's needs, technology stack, and project requirements. The key is consistency and clarity across your development process.