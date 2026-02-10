# Style Guides

Style guides help establish a shared set of conventions for how we write, structure, and communicate work across the project. They exist to reduce ambiguity, improve readability, and make collaboration smoother, especially as the number of contributors grows.

Rather than limiting creativity, these guidelines provide a common baseline so decisions don’t have to be re-debated in every pull request. The goal is consistency over preference, clarity over cleverness, and progress over perfection.

By following these style guides, contributors can:

- Understand changes faster
- Review code and documentation more efficiently
- Communicate intent clearly and predictably
- Spend less time on formatting and more time shipping quality work

These guides are living standards. They may evolve as the project grows, but they should always remain practical, lightweight, and focused on helping contributors work better together.

## Contributing Code

Before committing or pushing changes, we aim to follow a set of standards to keep commits and changes easy to understand and meaningful.
These standards are used to enhance communication between fellow contributors who write and read code for the project. Fewer chances of overthinking communication and a higher chance of shipping high quality contributions.

### Commit Guidelines

We follow and extend [this framework](https://github.com/wgtechlabs/clean-commit), we recommend to at least take a glance or skim through the [specification](https://github.com/wgtechlabs/clean-commit/blob/main/SPECIFICATION.md). Basically, we make commits in this format: `{emoji} {type} {(scope)<optional>}: {description}`.

| Emoji | Type       | What it covers                                               |
| :---: | ---------- | ------------------------------------------------------------ |
|  📦   | `new`      | Adding new features, files, or capabilities                  |
|  🔧   | `update`   | Changing existing code, refactoring, improvements, bug fixes |
|  🗑️   | `remove`   | Removing code, files, features, or dependencies              |
|  🔒   | `security` | Security fixes, patches, vulnerability resolutions           |
|  ⚙️   | `setup`    | Project configs, CI/CD, tooling, build systems               |
|  ☕   | `chore`    | Maintenance tasks, dependency updates, housekeeping          |
|  🧪   | `test`     | Adding, updating, or fixing tests                            |
|  📖   | `docs`     | Documentation changes and updates                            |
|  🏷️   | `release`  | Version releases and release preparation                     |

!!! Example "Examples"

    ```
    📦 new: user authentication system
    🔧 update (api): improve error handling  # with optional scope
    🔒 security (auth): fix jwt token validation bypass
    🗑️ remove (deps): unused axios dependency
    ☕ chore (deps): bump react from 17.0.2 to 18.2.0
    📖 docs: fix typos in contributing guide
    ```

### Conventional Comments

When communicating with fellow contributors, it is recommended to follow this [format](https://conventionalcomments.org/) or communicate so in a similar format that is practical and direct to the point.
