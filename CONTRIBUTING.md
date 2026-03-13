# Contributing to ES Search

Thank you for your interest in contributing to ES Search! This document provides guidelines and instructions for contributing to this project.

## 🤝 How to Contribute

We welcome contributions from everyone! Here are some ways you can contribute:

- Report bugs
- Suggest new features
- Submit pull requests
- Improve documentation
- Share usage examples
- Help other users

## 🐛 Reporting Bugs

Before creating bug reports, please check the existing issues to avoid duplicates.

### Bug Report Template

```markdown
**Describe the bug**
A clear and concise description of what the bug is.

**To Reproduce**
Steps to reproduce the behavior:
1. Go to '...'
2. Click on '....'
3. Scroll down to '....'
4. See error

**Expected behavior**
A clear and concise description of what you expected to happen.

**Screenshots**
If applicable, add screenshots to help explain your problem.

**Environment:**
- OS: [e.g., Windows 10/11]
- ES Version: [e.g., 1.1.0.26]
- Everything Version: [e.g., 1.4.1.1024]

**Additional context**
Add any other context about the problem here.
```

## 💡 Suggesting Features

Feature requests are welcome! Please provide:

1. A clear description of the feature
2. Use cases for the feature
3. Examples of how the feature would work
4. Any alternatives or workarounds you've considered

### Feature Request Template

```markdown
**Is your feature request related to a problem? Please describe.**
A clear and concise description of what the problem is. Ex. I'm always frustrated when [...]

**Describe the solution you'd like**
A clear and concise description of what you want to happen.

**Describe alternatives you've considered**
A clear and concise description of any alternative solutions or features you've considered.

**Additional context**
Add any other context or screenshots about the feature request here.
```

## 📝 Pull Request Process

### 1. Fork the Repository

Click the "Fork" button in the top right corner of the repository page.

### 2. Clone Your Fork

```bash
git clone https://github.com/YOUR_USERNAME/es-search.git
cd es-search
```

### 3. Create a Branch

Create a new branch for your contribution:

```bash
git checkout -b feature/your-feature-name
# or
git checkout -b fix/your-bug-fix
```

### 4. Make Your Changes

- Make your changes to the code or documentation
- Follow the existing code style and formatting
- Add comments for complex logic
- Update documentation if needed

### 5. Test Your Changes

- Test your changes thoroughly
- Ensure all examples work correctly
- Verify documentation is accurate
- Check for spelling and grammar errors

### 6. Commit Your Changes

Write clear, concise commit messages:

```bash
git add .
git commit -m "Add: Your feature description"
# or
git commit -m "Fix: Your bug fix description"
```

### 7. Push to Your Fork

```bash
git push origin feature/your-feature-name
```

### 8. Create a Pull Request

1. Go to the original repository
2. Click "New Pull Request"
3. Select your branch
4. Fill in the PR template
5. Submit your PR

### Pull Request Template

```markdown
**Description**
Brief description of changes made in this pull request.

**Type of Change**
- [ ] Bug fix (non-breaking change which fixes an issue)
- [ ] New feature (non-breaking change which adds functionality)
- [ ] Breaking change (fix or feature that would cause existing functionality to not work as expected)
- [ ] Documentation update

**Testing**
Describe the tests you ran to verify your changes.

**Checklist**
- [ ] My code follows the style guidelines of this project
- [ ] I have performed a self-review of my own code
- [ ] I have commented my code, particularly in hard-to-understand areas
- [ ] I have made corresponding changes to the documentation
- [ ] My changes generate no new warnings
- [ ] I have tested my changes locally
```

## 📄 Documentation Contributions

Documentation improvements are highly appreciated! You can help by:

- Fixing typos and grammatical errors
- Adding more examples
- Improving explanations
- Adding screenshots or diagrams
- Translating documentation

### Documentation Guidelines

- Use clear, concise language
- Provide working examples
- Include expected output
- Add context and explanations
- Follow existing formatting

## 🎨 Code Style Guidelines

- Use consistent formatting
- Write clear, descriptive variable names
- Add comments for complex logic
- Follow existing patterns in the codebase
- Keep changes focused and minimal

## 🧪 Testing

When contributing code changes:

1. Test your changes thoroughly
2. Verify all examples work correctly
3. Test on different Windows versions if possible
4. Check for edge cases
5. Ensure backward compatibility

## 📋 Development Setup

### Prerequisites

- Windows 10/11
- Git
- Everything Search
- ES (Everything CLI)
- A text editor (VS Code recommended)

### Setting Up Development Environment

```bash
# Clone the repository
git clone https://github.com/WhizZest/es-search.git
cd es-search

# Create a new branch
git checkout -b feature/your-feature

# Make your changes
# Edit files as needed

# Test your changes
# Verify examples work correctly

# Commit and push
git add .
git commit -m "Your commit message"
git push origin feature/your-feature
```

## 📖 Project Structure

```
es-search/
├── README.md           # Main project documentation
├── SKILL.md            # ES Search skill documentation
├── EXAMPLES.md         # Usage examples
├── CONTRIBUTING.md     # This file
├── LICENSE             # MIT License
└── .gitignore         # Git ignore rules
```

## 🏷️ Commit Message Guidelines

Use clear, descriptive commit messages:

- `Add:` - New features
- `Fix:` - Bug fixes
- `Update:` - Updates to existing features
- `Docs:` - Documentation changes
- `Refactor:` - Code refactoring
- `Test:` - Adding or updating tests
- `Chore:` - Maintenance tasks

Examples:
```
Add: Example for searching by file attributes
Fix: Correct date format in JSON export example
Docs: Update installation instructions for Windows 11
Refactor: Reorganize examples by category
```

## 🔄 Syncing Your Fork

Keep your fork up-to-date with the main repository:

```bash
# Add upstream remote
git remote add upstream https://github.com/WhizZest/es-search.git

# Fetch upstream changes
git fetch upstream

# Merge upstream changes into your branch
git merge upstream/main

# Push updated changes to your fork
git push origin your-branch
```

## 📧 Getting Help

If you need help contributing:

1. Check existing issues and pull requests
2. Read the documentation thoroughly
3. Ask questions in issues
4. Join community discussions

## 🎉 Recognition

Contributors will be recognized in the project's contributors section. All contributions are valuable and appreciated!

## 📜 Code of Conduct

### Our Pledge

We as members, contributors, and leaders pledge to make participation in our community a harassment-free experience for everyone, regardless of age, body size, visible or invisible disability, ethnicity, sex characteristics, gender identity and expression, level of experience, education, socio-economic status, nationality, personal appearance, race, religion, or sexual identity and orientation.

### Our Standards

Examples of behavior that contributes to a positive environment:

- Using welcoming and inclusive language
- Being respectful of differing viewpoints and experiences
- Gracefully accepting constructive criticism
- Focusing on what is best for the community
- Showing empathy towards other community members

### Unacceptable Behavior

Examples of unacceptable behavior:

- The use of sexualized language or imagery
- Trolling, insulting/derogatory comments, or personal/political attacks
- Public or private harassment
- Publishing others' private information without explicit permission
- Other conduct which could reasonably be considered inappropriate

### Enforcement

Project maintainers have the right and responsibility to remove, edit, or reject comments, commits, code, wiki edits, issues, and other contributions that are not aligned with this Code of Conduct.

## 📞 Contact

For questions or discussions:

- Open an issue on GitHub
- Mention `@WhizZest` for maintainer attention
- Check existing discussions first

---

Thank you for contributing to ES Search! Your contributions help make this project better for everyone. 🙏