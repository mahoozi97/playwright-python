### playwright

A high-level API to automate web browsers

### pytest-playwright

A pytest wrapper with fixtures for Playwright to automate web browsers

### Install

```bash
pip install playwright pytest-playwright

# install browser binaries
playwright install

# verify installing
playwright --version
pytest --version

# install if needed
pip install pytest-base-url
```

### Running Tests Manually

```bash
# Run a specific test file from your terminal
pytest file_name.py

# Run a specific test function or class
pytest file_name.py::test_function_name
```

### Keyboard Shortcuts (VS Code — macOS)

Add the following shortcuts to **Keyboard Shortcuts (JSON)** on macOS:

- `cmd+t` — Focus terminal and run `pytest` on the current file
- `shift+cmd+t` — Focus terminal and run `pytest` on the selected function

```json
// Place your key bindings in this file to override the defaults
[
  {
    "key": "cmd+t",
    "command": "runCommands",
    "args": {
      "commands": [
        "workbench.action.terminal.focus",
        {
          "command": "workbench.action.terminal.sendSequence",
          "args": {
            "text": "pytest ${relativeFile}\u000d"
          }
        }
      ]
    },
    "when": "editorTextFocus && editorLangId == 'python'"
  },
  {
    "key": "shift+cmd+t",
    "command": "runCommands",
    "args": {
      "commands": [
        "workbench.action.terminal.focus",
        {
          "command": "workbench.action.terminal.sendSequence",
          "args": {
            "text": "pytest ${relativeFile}::${selectedText}\u000d"
          }
        }
      ]
    },
    "when": "editorTextFocus && editorLangId == 'python' && editorHasSelection"
  }
]
```
