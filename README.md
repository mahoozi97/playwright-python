### playwright

A high-level API to automate web browsers

### pytest-playwright

A pytest wrapper with fixtures for Playwright to automate web browsers

### Install

```bash
pip install playwright pytest-playwright pytest-base-url pytest-html

# install browser binaries
playwright install

# verify installing
playwright --version
pytest --version
```

### Running Tests Manually

```bash
# List all available pytest and plugin CLI options (including Playwright and HTML flags)
pytest --help

# Run a specific test file from your terminal
pytest file_name.py

# Run a specific test function or class
pytest file_name.py::test_function_name

# Run with visible browser (headed mode)
pytest file_name.py --headed

# Capture screenshots for every test
pytest file_name.py --screenshot=on

# Combine flags on a single test function
pytest file_name.py::test_function_name --headed --screenshot=on
```

### Keyboard Shortcuts (VS Code — macOS)

Add the following shortcuts to **Keyboard Shortcuts (JSON)** (`Preferences: Open Keyboard Shortcuts (JSON)`) on macOS. Each chord starts with `cmd+k` (current file) or `shift+cmd+k` (selected function):

#### Current File (`cmd+k ...`)

| Shortcut | Command & Mode |
| :--- | :--- |
| cmd+k&nbsp;t | Focus terminal and run `pytest <file>` (headless) |
| cmd+k&nbsp;h | Focus terminal and run `pytest <file> --headed` (visible browser) |
| cmd+k&nbsp;s | Focus terminal and run `pytest <file> --screenshot=on` (headless + screenshot) |
| cmd+k&nbsp;v | Focus terminal and run `pytest <file> --video=on` (record video) |
| cmd+k&nbsp;r | Focus terminal and run `pytest <file> --html=reports/<file>.html --self-contained-html` |

#### Selected Function (`shift+cmd+k ...`)

| Shortcut | Command & Mode |
| :--- | :--- |
| shift+cmd+k&nbsp;t | Focus terminal and run `pytest <file>::<function>` (headless) |
| shift+cmd+k&nbsp;h | Focus terminal and run `pytest <file>::<function> --headed` (visible browser) |
| shift+cmd+k&nbsp;s | Focus terminal and run `pytest <file>::<function> --screenshot=on` (headless + screenshot) |
| shift+cmd+k&nbsp;v | Focus terminal and run `pytest <file>::<function> --video=on` (record video) |
| shift+cmd+k&nbsp;r | Focus terminal and run `pytest <file>::<function> --html=reports/<file>-<function>.html --self-contained-html` |

```json
// Place your key bindings in this file to override the defaults
[
  // --- Current File (cmd+k ...) ---
  {
    "key": "cmd+k t",
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
    "key": "cmd+k h",
    "command": "runCommands",
    "args": {
      "commands": [
        "workbench.action.terminal.focus",
        {
          "command": "workbench.action.terminal.sendSequence",
          "args": {
            "text": "pytest ${relativeFile} --headed\u000d"
          }
        }
      ]
    },
    "when": "editorTextFocus && editorLangId == 'python'"
  },
  {
    "key": "cmd+k s",
    "command": "runCommands",
    "args": {
      "commands": [
        "workbench.action.terminal.focus",
        {
          "command": "workbench.action.terminal.sendSequence",
          "args": {
            "text": "pytest ${relativeFile} --screenshot=on\u000d"
          }
        }
      ]
    },
    "when": "editorTextFocus && editorLangId == 'python'"
  },
  {
    "key": "cmd+k v",
    "command": "runCommands",
    "args": {
      "commands": [
        "workbench.action.terminal.focus",
        {
          "command": "workbench.action.terminal.sendSequence",
          "args": {
            "text": "pytest ${relativeFile} --video=on\u000d"
          }
        }
      ]
    },
    "when": "editorTextFocus && editorLangId == 'python'"
  },
  {
    "key": "cmd+k r",
    "command": "runCommands",
    "args": {
      "commands": [
        "workbench.action.terminal.focus",
        {
          "command": "workbench.action.terminal.sendSequence",
          "args": {
            "text": "pytest ${relativeFile} --html=reports/${fileBasenameNoExtension}.html --self-contained-html\u000d"
          }
        }
      ]
    },
    "when": "editorTextFocus && editorLangId == 'python'"
  },

  // --- Selected Function (shift+cmd+k ...) ---
  {
    "key": "shift+cmd+k t",
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
  },
  {
    "key": "shift+cmd+k h",
    "command": "runCommands",
    "args": {
      "commands": [
        "workbench.action.terminal.focus",
        {
          "command": "workbench.action.terminal.sendSequence",
          "args": {
            "text": "pytest ${relativeFile}::${selectedText} --headed\u000d"
          }
        }
      ]
    },
    "when": "editorTextFocus && editorLangId == 'python' && editorHasSelection"
  },
  {
    "key": "shift+cmd+k s",
    "command": "runCommands",
    "args": {
      "commands": [
        "workbench.action.terminal.focus",
        {
          "command": "workbench.action.terminal.sendSequence",
          "args": {
            "text": "pytest ${relativeFile}::${selectedText} --screenshot=on\u000d"
          }
        }
      ]
    },
    "when": "editorTextFocus && editorLangId == 'python' && editorHasSelection"
  },
  {
    "key": "shift+cmd+k v",
    "command": "runCommands",
    "args": {
      "commands": [
        "workbench.action.terminal.focus",
        {
          "command": "workbench.action.terminal.sendSequence",
          "args": {
            "text": "pytest ${relativeFile}::${selectedText} --video=on\u000d"
          }
        }
      ]
    },
    "when": "editorTextFocus && editorLangId == 'python' && editorHasSelection"
  },
  {
    "key": "shift+cmd+k r",
    "command": "runCommands",
    "args": {
      "commands": [
        "workbench.action.terminal.focus",
        {
          "command": "workbench.action.terminal.sendSequence",
          "args": {
            "text": "pytest ${relativeFile}::${selectedText} --html=reports/${fileBasenameNoExtension}__${selectedText}.html --self-contained-html\u000d"
          }
        }
      ]
    },
    "when": "editorTextFocus && editorLangId == 'python' && editorHasSelection"
  }
]
```
