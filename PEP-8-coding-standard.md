# PEP 8 Guidelines for AI-Generated Codebases

## Prompt Engineering for PEP 8 Compliance

### Initial Project Setup Prompts
- "Follow PEP 8 style guide for all Python code"
- "Use 4 spaces for indentation, never tabs"
- "Limit all lines to 79 characters maximum"
- "Use lowercase_with_underscores for functions and variables"
- "Use CapitalizedWords for class names"
- "Add docstrings to all public functions, classes, and modules"

### Specific Style Instructions
- "Place imports at the top, grouped by: standard library, third-party, local"
- "Use descriptive variable names, avoid single letters except in loops"
- "Add type hints following PEP 484"
- "Include inline comments for complex logic, separated by 2 spaces"
- "Use f-strings for string formatting (Python 3.6+)"

## Validation and Quality Control

### Automated Tools Configuration
- **Pre-generation setup:**
  - Configure `.flake8` file with project-specific rules
  - Set up `pyproject.toml` for Black formatter
  - Create `.pre-commit-config.yaml` for automatic checking
  
### Essential Tools
- **flake8**: `flake8 --max-line-length=79 --exclude=venv`
- **black**: `black --line-length 79 --check .`
- **autopep8**: `autopep8 --aggressive --aggressive --diff`
- **pylint**: `pylint --rcfile=.pylintrc src/`
- **mypy**: `mypy --strict src/`

### CI/CD Pipeline Checks
```yaml
# Example GitHub Actions workflow
- name: Lint with flake8
  run: |
    pip install flake8
    flake8 . --count --select=E9,F63,F7,F82 --show-source --statistics
    flake8 . --count --exit-zero --max-complexity=10 --max-line-length=79
```

## AI-Specific Instructions

### Consistency Prompts
- "Maintain consistent quote style throughout the project (single/double)"
- "Use the same import style as existing modules"
- "Follow the established error handling pattern in this codebase"
- "Match the docstring format used in other files"

### Code Generation Rules
- "Generate complete modules, not fragments"
- "Include all necessary imports at the top"
- "Add `if __name__ == '__main__':` blocks where appropriate"
- "Create `__init__.py` files for all packages"
- "Include type hints for all function parameters and returns"

### Common AI Pitfalls to Avoid
- "Don't use tabs even if the AI's training data contains them"
- "Don't mix naming conventions (stick to snake_case)"
- "Don't leave TODO comments without context"
- "Don't use mutable default arguments"
- "Don't import modules inside functions unless necessary"

## Project Structure Guidelines

### Directory Layout
```
project/
├── src/
│   ├── __init__.py
│   ├── core/
│   │   ├── __init__.py
│   │   └── main.py
│   └── utils/
│       ├── __init__.py
│       └── helpers.py
├── tests/
├── docs/
├── requirements.txt
├── setup.py
├── .flake8
├── .gitignore
└── README.md
```

### File Naming
- "Use lowercase_with_underscores.py for all Python files"
- "Test files should start with test_ or end with _test.py"
- "Keep module names short and descriptive"
- "Avoid using hyphens in Python file names"

## Testing and Documentation

### Test Generation Instructions
- "Create unit tests following PEP 8 style"
- "Use descriptive test method names: test_function_does_specific_thing"
- "Group related tests in classes: TestClassName"
- "Add docstrings to test methods explaining what they test"

### Documentation Requirements
- "Generate comprehensive docstrings in NumPy/Google/Sphinx style"
- "Include usage examples in docstrings"
- "Document all parameters, returns, and exceptions"
- "Add module-level docstrings explaining purpose"

## Maintenance and Refactoring

### Refactoring Prompts
- "Refactor this module to comply with PEP 8"
- "Break long functions into smaller, focused functions"
- "Extract magic numbers into named constants"
- "Consolidate duplicate code into reusable functions"

### Code Review Checklist
- All functions under 79 characters per line
- No trailing whitespace
- Consistent indentation (4 spaces)
- Proper spacing around operators
- Meaningful variable names
- Appropriate use of blank lines
- Comments are complete sentences
- Docstrings for all public APIs

## Configuration Templates

### .flake8
```ini
[flake8]
max-line-length = 79
exclude = .git,__pycache__,venv,build,dist
ignore = E203, W503
```

### pyproject.toml (for Black)
```toml
[tool.black]
line-length = 79
target-version = ['py38']
include = '\.pyi?$'
```

### .editorconfig
```ini
[*.py]
indent_style = space
indent_size = 4
end_of_line = lf
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true
max_line_length = 79
```

## Best Practices for AI Collaboration

### Version Control
- "Generate meaningful commit messages following conventional commits"
- "Create atomic commits (one feature/fix per commit)"
- "Include PEP 8 compliance in commit messages when fixing style"

### Code Organization
- "Group related functionality into classes"
- "Create separate modules for different concerns"
- "Use `__all__` to define public APIs"
- "Implement proper exception hierarchies"

### Performance Considerations
- "Use generators for large datasets"
- "Implement `__slots__` for classes with fixed attributes"
- "Use list comprehensions appropriately"
- "Avoid premature optimization"

Remember: When working with AI-generated code, always validate output with automated tools and establish clear style guidelines in your initial prompts. Consistency is more important than any individual rule.