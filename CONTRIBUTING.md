# Contributing to ansible-role-apache

Thank you for your interest in contributing! This document provides guidelines for contributing to this project.

## How to Contribute

### Reporting Bugs

- Check if the bug has already been reported in [Issues](../../issues)
- If not, create a new issue with:
  - Clear title and description
  - Steps to reproduce
  - Expected vs actual behavior
  - Ansible version and OS details
  - Relevant logs or error messages

### Suggesting Features

- Check if the feature has been requested in [Issues](../../issues)
- Create a new issue with:
  - Clear description of the feature
  - Use case and benefits
  - Possible implementation approach

### Submitting Changes

1. **Fork the repository**

2. **Create a feature branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

3. **Make your changes**
   - Follow existing code style
   - Add/update tests if applicable
   - Update documentation (README.md, CHANGELOG.md)

4. **Test your changes**
   ```bash
   ansible-lint
   ansible-playbook tests/test.yml --syntax-check
   ```

5. **Commit your changes**
   - Use clear, descriptive commit messages
   - Reference issue numbers if applicable
   ```bash
   git commit -m "Add feature: description (#issue-number)"
   ```

6. **Push to your fork**
   ```bash
   git push origin feature/your-feature-name
   ```

7. **Create a Pull Request**
   - Provide clear description of changes
   - Reference related issues
   - Ensure CI checks pass

## Code Style

- Follow [Ansible best practices](https://docs.ansible.com/ansible/latest/tips_tricks/ansible_tips_tricks.html)
- Use YAML syntax with 2-space indentation
- Use fully qualified collection names (e.g., `ansible.builtin.apt`)
- Add `become: true` to tasks requiring privilege escalation
- Use descriptive task names
- Add comments for complex logic

## Testing

- All changes should pass `ansible-lint`
- Test on supported Ubuntu versions (22.04, 24.04)
- Ensure idempotency (running twice produces same result)
- Update tests when adding new features

## Questions?

Feel free to open an issue for any questions about contributing.

Thank you for helping make this role better!
