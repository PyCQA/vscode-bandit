![logotype-sm](https://github.com/user-attachments/assets/3e8c0b13-38cd-4f2a-a001-9fa20aaea533)

# Bandit extension for Visual Studio Code

A Visual Studio Code extension for the [Bandit](https://github.com/PyCQA/bandit) static analysis security tool, developed and maintained by the original authors of Bandit. This extension comes bundled with Bandit version 1.8.3.

It is compatible with all [actively supported versions](https://devguide.python.org/#status-of-python-branches) of the Python programming language.

For more information about Bandit, visit https://bandit.readthedocs.io/.

## Settings

There are several settings you can configure to customize the behavior of this extension.
| Setting                   | Default              | Description                                                                                                                                                                                                                                                                                                                                                                                   |
|---------------------------|----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `bandit.args`             | `[]`                 | Arguments passed to Bandit for linting Python files. Each argument should be a separate string in the array. <br> Examples: <br> - `"bandit.args": ["--severity-level=high"]` <br> - `"bandit.args": ["--skip=B603", "--confidence-level=high"]`                                                                                                                                              |
| `bandit.cwd`              | `${workspaceFolder}` | Sets the current working directory used to lint Python files with Bandit. By default, it uses the root directory of the workspace. You can set it to `${fileDirname}` to use the parent folder of the file being linted.                                                                                                                                                                      |
| `bandit.enabled`          | `true`               | Enable/disable linting Python files with Bandit. This can be set globally or per workspace. When disabled, the linting server continues to monitor files but does not perform linting or expose code actions.                                                                                                                                                                                 |
| `bandit.path`             | `[]`                 | Path or command used by the extension to run Bandit. Accepts an array of strings (each arg separate). <br> Examples: <br> - `"bandit.path": ["~/global_env/bandit"]` <br> - `"bandit.path": ["bandit"]` <br> - `"bandit.path": ["${interpreter}", "-m", "bandit"]` <br> If set to `["bandit"]`, it uses the Bandit available in your `PATH`. Note: Using a custom path may slow down linting. |
| `bandit.interpreter`      | `[]`                 | Python executable or command used to launch Bandit. Accepts an array of strings (each arg separate). If left as `[]`, it uses the selected Python interpreter.                                                                                                                                                                                                                                |
| `bandit.importStrategy`   | `useBundled`         | Specifies which Bandit binary to use. `useBundled` uses the version shipped with the extension. `fromEnvironment` uses the Bandit in the current Python environment. If it can't find one, it falls back to the bundled version. Overridden if `bandit.path` is set.                                                                                                                          |
| `bandit.showNotifications` | `off`                | Controls when extension notifications appear. Options: `onError`, `onWarning`, `always`, `off`.                                                                                                                                                                                                                                                                                               |

### Variable Substitution

The following variables are supported for substitution in the `bandit.args`, `bandit.cwd`, `bandit.path`, and `bandit.interpreter` settings:

| Variable                        | Description                                                                       | Supported In                         |
|---------------------------------|-----------------------------------------------------------------------------------|--------------------------------------|
| `${workspaceFolder}`            | Root directory of the currently active workspace folder                           | `args`, `cwd`, `path`, `interpreter` |
| `${workspaceFolder:FolderName}` | Root directory of a specific workspace folder in a multi-root workspace           | `args`, `path`, `interpreter`        |
| `${userHome}`                   | Path to the current user's home directory                                         | `args`, `path`, `interpreter`        |
| `${env:EnVarName}`              | Value of the environment variable `EnVarName`                                     | `args`, `path`, `interpreter`        |
| `${interpreter}`                | Python executable used by Bandit (workspace interpreter or bandit.interpreter)    | `path` only                          |
| `${fileDirname}`                | Directory of the file being linted.                                               | `cwd` only                           |

## Commands

| Command                | Description                       |
| ---------------------- | --------------------------------- |
| Bandit: Restart Server | Force re-start the linter server. |

## Logging

From the Command Palette (**View** > **Command Palette ...**), run the **Developer: Set Log Level...** command. Select **Bandit** from the **Extension logs** group. Then select the log level you want to set.

To open the logs, click on the language status icon (`{}`) on the bottom right of the Status bar, next to the Python language mode. Locate the **Bandit** entry and select **Open logs**.

## Troubleshooting

In this section, you will find some common issues you might encounter and how to resolve them. If you are experiencing any issues that are not covered here, please [file an issue](https://github.com/PyCQA/vscode-bandit/issues).
