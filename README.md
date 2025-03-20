# Bandit extension for Visual Studio Code

A Visual Studio Code extension with support for the Bandit static analysis tool.

This extension supports all [actively supported versions](https://devguide.python.org/#status-of-python-branches) of the Python language.

For more information on Bandit, see https://bandit.readthedocs.io/

## Settings

There are several settings you can configure to customize the behavior of this extension.

| Settings | Default | Description |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| bandit.args | `[]` | Arguments passed to Bandit for linting Python files. Each argument should be provided as a separate string in the array. <br> Examples: <br>- `"bandit.args": ["--severity-level=high"]` <br> - `"bandit.args": ["--skip=B603", "--confidence-level=high"]` |
| bandit.cwd | `${workspaceFolder}` | Sets the current working directory used to lint Python files with Bandit. By default, it uses the root directory of the workspace `${workspaceFolder}`. You can set it to `${fileDirname}` to use the parent folder of the file being linted as the working directory for Bandit. |
| bandit.enabled | `true` | Enable/disable linting Python files with Bandit. This setting can be applied globally or at the workspace level. If disabled, the linting server itself will continue to be active and monitor read and write events, but it won't perform linting or expose code actions. |
| bandit.path | `[]` | "Path or command to be used by the extension to lint Python files with Bandit. Accepts an array of a single or multiple strings. If passing a command, each argument should be provided as a separate string in the array. If set to `["Bandit"]`, it will use the version of Bandit available in the `PATH` environment variable. Note: Using this option may slowdown linting. <br>Examples: <br>- `"bandit.path" : ["~/global_env/bandit"]` <br>- `"bandit.path" : ["bandit"]` <br>- `"bandit.path" : ["${interpreter}", "-m", "bandit"]` |
| bandit.interpreter | `[]` | Path to a Python executable or a command that will be used to launch the Bandit server and any subprocess. Accepts an array of a single or multiple strings. When set to `[]`, the extension will use the path to the selected Python interpreter. If passing a command, each argument should be provided as a separate string in the array. |
| bandit.importStrategy   | `useBundled` | Defines which Bandit binary to be used to lint Python files. When set to `useBundled`, the extension will use the Bandit binary that is shipped with the extension. When set to `fromEnvironment`, the extension will attempt to use the Bandit binary and all dependencies that are available in the currently selected environment. Note: If the extension can't find a valid Bandit binary in the selected environment, it will fallback to using the Bandit binary that is shipped with the extension. This setting will be overriden if `bandit.path` is set. |
| bandit.showNotification | `off` | Controls when notifications are shown by this extension. Accepted values are `onError`, `onWarning`, `always` and `off`. |

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
