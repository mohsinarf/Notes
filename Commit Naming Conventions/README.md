# Commit Messages
The basic structure of a conventional commit message is as follows:

```
<type>(<optional scope>): <message>
```

Here's a breakdown of each part:

1.  Type: Describes the purpose of the commit. Common types include:
    - feat: A new feature for the user or a significant change.
    - fix: A bug fix.
    - docs: Documentation changes.
    - style: Code style changes (formatting, indentation).
    - refactor: Code refactoring, without changing external behavior.
    - test: Adding or modifying tests.
    - chore: Routine tasks, maintenance, or tooling changes.
2.  Optional Scope: Describes the module, component, or area of the project affected by the commit.

3.  Message: A brief, imperative statement that describes what the commit does. It should be in the present tense and not exceed 72 characters.

### Examples
Here are a few examples:
```
feat(user-auth): add password reset functionality

fix(ui): resolve issue with button alignment

docs(readme): update installation instructions

style(css): improve code formatting
```