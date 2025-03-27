# Bandit extension for Visual Studio Code

A Visual Studio Code extension with support for the Bandit static analysis tool. This extension ships with bandit=1.8.3.

This extension supports all [actively supported versions](https://devguide.python.org/#status-of-python-branches) of the Python language.

For more information on Bandit, see https://bandit.readthedocs.io/

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
| `bandit.showNotification` | `off`                | Controls when extension notifications appear. Options: `onError`, `onWarning`, `always`, `off`.                                                                                                                                                                                                                                                                                               |

The following variables are supported for substitution in the `bandit.args`, `bandit.cwd`, `bandit.path`, and `bandit.interpreter` settings:

-   `${workspaceFolder}`
-   `${workspaceFolder:FolderName}`
-   `${userHome}`
-   `${env:EnvVarName}`

The `bandit.path` setting also supports the `${interpreter}` variable as one of the entries of the array. This variable is subtituted based on the value of the `bandit.interpreter` setting.

## Commands

| Command                | Description                       |
| ---------------------- | --------------------------------- |
| Bandit: Restart Server | Force re-start the linter server. |

## Logging

From the Command Palette (**View** > **Command Palette ...**), run the **Developer: Set Log Level...** command. Select **Bandit** from the **Extension logs** group. Then select the log level you want to set.

To open the logs, click on the language status icon (`{}`) on the bottom right of the Status bar, next to the Python language mode. Locate the **Bandit** entry and select **Open logs**.

## Troubleshooting

In this section, you will find some common issues you might encounter and how to resolve them. If you are experiencing any issues that are not covered here, please [file an issue](https://github.com/PyCQA/vscode-bandit/issues).
