# CLAUDE.md - AI Assistant Guide for topsteps_code

**Last Updated:** 2025-11-20
**Repository Owner:** CIOU,GUO-YU (zxcvbn1294)
**License:** MIT
**Created:** October 8, 2025

---

## Table of Contents

1. [Repository Overview](#repository-overview)
2. [Current Project State](#current-project-state)
3. [Repository Structure](#repository-structure)
4. [Git Workflow & Branch Strategy](#git-workflow--branch-strategy)
5. [Development Guidelines](#development-guidelines)
6. [Code Conventions](#code-conventions)
7. [Testing Strategy](#testing-strategy)
8. [Documentation Standards](#documentation-standards)
9. [AI Assistant Workflow](#ai-assistant-workflow)
10. [Future Development Roadmap](#future-development-roadmap)

---

## Repository Overview

### Purpose
This is a starter repository for the **topsteps_code** project. The repository was initialized in October 2025 and is currently in its early stages.

### Repository Information
- **GitHub URL:** https://github.com/zxcvbn1294/topsteps_code
- **Primary Language:** To be determined (no source code yet)
- **License:** MIT License (Copyright 2025 CIOU,GUO-YU)
- **Development Tool:** Claude Code integrated

### Key Stakeholders
- **Owner/Author:** CIOU,GUO-YU (jack chiou)
- **AI Assistant:** Claude (Anthropic)

---

## Current Project State

### Status: **INITIAL SETUP PHASE**

As of November 2025, this repository contains:
- ✅ MIT License file
- ✅ Git repository initialized
- ✅ Test file (`test.txt`) for workflow verification
- ❌ No source code
- ❌ No package manager configuration
- ❌ No build tooling
- ❌ No testing framework
- ❌ No documentation (README.md)

### Commit History
```
b2a5f2c - Merge branch 'main' (Oct 8, 2025)
dd42544 - 新增測試檔案 [Added test file] (Oct 8, 2025) - with Claude
04cd5c0 - Initial commit (Oct 8, 2025)
```

The Chinese commit message "新增測試檔案" indicates this may be developed by Chinese-speaking contributors, though documentation should be maintained in English for broader accessibility.

---

## Repository Structure

### Current Structure
```
topsteps_code/
├── LICENSE              # MIT License file
├── test.txt            # Test file for git workflow
├── CLAUDE.md           # This file - AI assistant guide
└── .git/               # Git metadata
```

### Recommended Future Structure

When development begins, consider organizing the project as follows:

```
topsteps_code/
├── .github/            # GitHub workflows and templates
│   ├── workflows/      # CI/CD pipelines
│   └── ISSUE_TEMPLATE/ # Issue templates
├── docs/               # Project documentation
│   ├── api/           # API documentation
│   ├── guides/        # User guides
│   └── architecture/  # Architecture decisions
├── src/               # Source code
│   ├── components/    # Reusable components (if applicable)
│   ├── utils/         # Utility functions
│   ├── services/      # Business logic/services
│   └── config/        # Configuration files
├── tests/             # Test files
│   ├── unit/          # Unit tests
│   ├── integration/   # Integration tests
│   └── e2e/           # End-to-end tests
├── scripts/           # Build and deployment scripts
├── .gitignore         # Git ignore rules
├── package.json       # Dependencies (if Node.js)
├── README.md          # Project overview
├── CLAUDE.md          # This file
├── CONTRIBUTING.md    # Contribution guidelines
├── CHANGELOG.md       # Version history
└── LICENSE            # MIT License
```

---

## Git Workflow & Branch Strategy

### Branch Naming Convention

#### Claude Code Branches (AI Development)
- **Format:** `claude/claude-md-<session-id>`
- **Example:** `claude/claude-md-mi7ev5g5uprc67u8-01GbonEGEV3zCN58trxhTCV5`
- **Critical:** All AI assistant branches MUST start with `claude/` prefix
- **Note:** Pushing to branches without correct naming will fail with 403 error

#### Human Developer Branches
- **Feature branches:** `feature/<feature-name>`
- **Bug fixes:** `fix/<bug-description>`
- **Hotfixes:** `hotfix/<issue-number>`
- **Experimental:** `experiment/<experiment-name>`

### Branch Strategy

1. **Main Branch:** `main` (protected)
   - Production-ready code only
   - Requires pull request reviews
   - All commits must pass CI/CD checks

2. **Development Branches:** Various feature/fix branches
   - Short-lived branches for specific changes
   - Merged via pull requests
   - Deleted after successful merge

3. **Claude Branches:** `claude/*`
   - AI-assisted development sessions
   - Created per session with unique session ID
   - Must be pushed with `-u origin <branch-name>`

### Git Commands

#### For AI Assistants (Claude)
```bash
# Pushing changes (CRITICAL: use -u flag)
git push -u origin claude/claude-md-<session-id>

# Network error handling: Retry up to 4 times with exponential backoff
# Retry delays: 2s, 4s, 8s, 16s

# Fetching specific branches
git fetch origin <branch-name>

# Pulling changes
git pull origin <branch-name>
```

#### Commit Message Format
```
<type>: <subject>

<body>

<footer>
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, no logic change)
- `refactor`: Code refactoring
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

**Example:**
```
feat: add user authentication module

Implemented JWT-based authentication with refresh tokens.
Added login, logout, and token refresh endpoints.

Co-authored-by: Claude <noreply@anthropic.com>
```

---

## Development Guidelines

### Before Starting Development

1. **Determine Project Type**
   - Web application (frontend/backend/fullstack)
   - Library/package
   - CLI tool
   - API service
   - Mobile app
   - Desktop application

2. **Choose Technology Stack**
   - Programming language(s)
   - Framework(s)
   - Database(s)
   - Build tools
   - Testing frameworks

3. **Set Up Project Configuration**
   - Initialize package manager (npm, pip, cargo, etc.)
   - Configure linters and formatters
   - Set up pre-commit hooks
   - Create .gitignore file

4. **Create Initial Documentation**
   - README.md with project overview
   - CONTRIBUTING.md for contributors
   - Code of Conduct (optional)

### Security Best Practices

⚠️ **Critical Security Reminders:**
- Never commit secrets, API keys, or credentials
- Use environment variables for sensitive configuration
- Implement input validation to prevent injection attacks
- Follow OWASP Top 10 guidelines
- Sanitize user inputs to prevent XSS
- Use parameterized queries to prevent SQL injection
- Implement proper authentication and authorization
- Keep dependencies updated for security patches

### Code Quality Standards

- **Linting:** Configure and enforce code linting
- **Formatting:** Use consistent code formatting (Prettier, Black, rustfmt, etc.)
- **Type Safety:** Use TypeScript, type hints, or static analysis where applicable
- **Code Review:** All changes should be reviewed via pull requests
- **Documentation:** Document public APIs, complex logic, and architectural decisions

---

## Code Conventions

### General Principles

1. **Readability First:** Code should be self-documenting
2. **DRY Principle:** Don't Repeat Yourself
3. **SOLID Principles:** Follow object-oriented design principles
4. **KISS:** Keep It Simple, Stupid
5. **YAGNI:** You Aren't Gonna Need It (avoid over-engineering)

### Naming Conventions

#### Variables and Functions
```
camelCase      - JavaScript/TypeScript variables and functions
snake_case     - Python variables and functions
PascalCase     - Classes, interfaces, types
SCREAMING_CASE - Constants
kebab-case     - File names, URLs
```

#### Files and Directories
- Use descriptive, lowercase names
- Separate words with hyphens or underscores (be consistent)
- Component files should match component names

### Comments and Documentation

```javascript
/**
 * Brief description of function
 *
 * @param {Type} paramName - Description of parameter
 * @returns {Type} Description of return value
 * @throws {ErrorType} Description of when error is thrown
 *
 * @example
 * functionName(arg1, arg2);
 */
function functionName(paramName) {
  // Implementation
}
```

### Error Handling

- Always handle errors explicitly
- Use try-catch blocks appropriately
- Log errors with sufficient context
- Return meaningful error messages
- Don't expose internal error details to end users

---

## Testing Strategy

### Testing Pyramid

1. **Unit Tests (70%)**
   - Test individual functions and methods
   - Fast, isolated, deterministic
   - Mock external dependencies

2. **Integration Tests (20%)**
   - Test interaction between components
   - Verify data flow and API contracts

3. **End-to-End Tests (10%)**
   - Test complete user workflows
   - Verify system behavior from user perspective

### Test Organization

```
tests/
├── unit/
│   ├── utils.test.js
│   └── services.test.js
├── integration/
│   └── api.test.js
├── e2e/
│   └── user-flow.test.js
└── fixtures/
    └── test-data.json
```

### Test Naming Convention

```javascript
describe('ComponentName', () => {
  describe('methodName', () => {
    it('should do something when condition is met', () => {
      // Arrange
      // Act
      // Assert
    });
  });
});
```

### Code Coverage Goals

- **Minimum:** 80% overall coverage
- **Critical paths:** 100% coverage
- **New code:** Should not decrease overall coverage

---

## Documentation Standards

### README.md Structure

```markdown
# Project Name

Brief description (1-2 sentences)

## Features
- Feature 1
- Feature 2

## Installation
Step-by-step installation instructions

## Usage
Code examples and usage instructions

## API Documentation
Link to detailed API docs

## Contributing
Link to CONTRIBUTING.md

## License
MIT License - see LICENSE file
```

### Code Documentation

- **Public APIs:** Must be documented with JSDoc/docstrings
- **Complex Logic:** Add explanatory comments
- **Architecture Decisions:** Document in `docs/architecture/`
- **API Endpoints:** Maintain OpenAPI/Swagger documentation

### Inline Documentation

```javascript
// Good: Explains WHY
// Retry with exponential backoff to handle network instability
await retryWithBackoff(apiCall, { maxAttempts: 4 });

// Bad: Explains WHAT (code already shows this)
// Call retry function with api call
await retryWithBackoff(apiCall, { maxAttempts: 4 });
```

---

## AI Assistant Workflow

### When Working as Claude Code Assistant

#### 1. Understanding the Task
- Read the user's request carefully
- Ask clarifying questions if requirements are ambiguous
- Check existing code and conventions before starting

#### 2. Planning Phase
- Use `TodoWrite` tool for complex multi-step tasks
- Break down large tasks into smaller, manageable steps
- Present plan to user before implementation (for significant changes)

#### 3. Implementation Phase
- Read existing files before editing
- Prefer editing existing files over creating new ones
- Follow existing code patterns and conventions
- Write secure code (avoid OWASP Top 10 vulnerabilities)
- Include error handling and validation

#### 4. Testing Phase
- Run existing tests to ensure no regression
- Add tests for new functionality
- Verify the implementation works as expected

#### 5. Documentation Phase
- Update relevant documentation
- Add code comments for complex logic
- Update CHANGELOG.md for significant changes

#### 6. Commit Phase
- Write clear, descriptive commit messages
- Follow commit message format conventions
- Use co-authoring attribution when appropriate
- **ONLY commit when explicitly asked by the user**

#### 7. Push Phase
- Use `git push -u origin <branch-name>`
- Verify branch name starts with `claude/`
- Retry on network errors (up to 4 times with exponential backoff)

### Tool Usage Best Practices

1. **File Operations:**
   - Use `Read` instead of `cat`
   - Use `Edit` instead of `sed/awk`
   - Use `Write` instead of `echo >>`
   - Use `Glob` instead of `find` or `ls`
   - Use `Grep` instead of `grep` or `rg`

2. **Code Exploration:**
   - Use `Task` tool with `subagent_type=Explore` for broad codebase exploration
   - Use direct tools (`Grep`, `Glob`) for specific file/pattern searches
   - Read files in parallel when exploring multiple areas

3. **Parallel Execution:**
   - Execute independent tool calls in parallel
   - Make sequential calls only when dependencies exist
   - Never use placeholders in tool parameters

### Communication Style

- Be concise and technical
- Avoid emojis unless explicitly requested
- Focus on facts and problem-solving
- Use code references with `file:line` format
- No unnecessary praise or validation

---

## Future Development Roadmap

### Phase 1: Project Initialization (Current)
- [x] Create repository
- [x] Add LICENSE
- [x] Add test file for workflow verification
- [x] Create CLAUDE.md documentation
- [ ] Create README.md
- [ ] Add .gitignore
- [ ] Determine project purpose and technology stack

### Phase 2: Project Setup
- [ ] Initialize package manager
- [ ] Set up project structure
- [ ] Configure build tools
- [ ] Set up testing framework
- [ ] Configure linting and formatting
- [ ] Set up pre-commit hooks

### Phase 3: Core Development
- [ ] Implement core functionality
- [ ] Write tests
- [ ] Create API documentation
- [ ] Set up CI/CD pipeline

### Phase 4: Documentation & Polish
- [ ] Complete user documentation
- [ ] Add code examples
- [ ] Create contribution guidelines
- [ ] Prepare for first release

---

## Questions for Repository Owner

To better assist with development, please clarify:

1. **Project Purpose:** What is topsteps_code intended to do?
2. **Technology Stack:** Which programming languages/frameworks should be used?
3. **Target Users:** Who will use this project?
4. **Key Features:** What are the primary features to implement?
5. **Timeline:** Are there any deadlines or milestones?
6. **Integration:** Will this integrate with other systems?
7. **Deployment:** Where will this be deployed (cloud, on-premise, etc.)?

---

## References & Resources

### Git & GitHub
- [Git Documentation](https://git-scm.com/doc)
- [GitHub Flow](https://guides.github.com/introduction/flow/)
- [Conventional Commits](https://www.conventionalcommits.org/)

### Security
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [Security Best Practices](https://cheatsheetseries.owasp.org/)

### Claude Code
- [Claude Code Documentation](https://docs.claude.com/en/docs/claude-code/)
- [Claude Code GitHub](https://github.com/anthropics/claude-code)

---

## Changelog

### 2025-11-20
- Created comprehensive CLAUDE.md documentation
- Documented current repository state
- Established development guidelines and conventions
- Defined git workflow and branch strategy
- Added AI assistant workflow instructions

### 2025-10-08
- Repository initialized with MIT License
- Added test.txt for workflow verification
- First Claude-assisted commit

---

## Contact & Support

- **Repository Owner:** CIOU,GUO-YU (jack chiou)
- **GitHub Issues:** https://github.com/zxcvbn1294/topsteps_code/issues
- **Claude Code Feedback:** https://github.com/anthropics/claude-code/issues

---

**Note:** This document should be updated as the project evolves. When making significant changes to project structure, conventions, or workflows, update this file accordingly.
