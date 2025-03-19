# Bandit extension for Visual Studio Code

A Visual Studio Code extension with support for the Bandit static analysis tool.

## Programming Languages and Frameworks

This extension has two parts, the extension part and language server part. The extension part is written in TypeScript, and language server part is written in Python over the [_pygls_][pygls] (Python language server) library.

See [Language Server Protocol](https://microsoft.github.io/language-server-protocol). [_pygls_][pygls] currently works on the [version 3.16 of LSP](https://microsoft.github.io/language-server-protocol/specifications/specification-3-16/).

The TypeScript part handles working with VS Code and its UI.

## Requirements

1. VS Code 1.64.0 or greater
1. Python 3.9 or greater
1. node >= 18.17.0
1. npm >= 8.19.0 (`npm` is installed with node, check npm version, use `npm install -g npm@8.3.0` to update)
1. Python extension for VS Code

You should know to create and work with python virtual environments.

## Features of this Template

After finishing the getting started part, this template would have added the following. Assume `<pytool-module>` was replaced with `mytool`, and `<pytool-display-name>` with`My Tool`:

## Building and Running the extension

Run the `Debug Extension and Python` configuration form VS Code. That should build and debug the extension in host window.

Note: if you just want to build you can run the build task in VS Code (`ctrl`+`shift`+`B`)

## Debugging

To debug both TypeScript and Python code use `Debug Extension and Python` debug config. This is the recommended way. Also, when stopping, be sure to stop both the Typescript, and Python debug sessions. Otherwise, it may not reconnect to the python session.

To debug only TypeScript code, use `Debug Extension` debug config.

To debug a already running server or in production server, use `Python Attach`, and select the process that is running `lsp_server.py`.

## Logging and Logs

The template creates a logging Output channel that can be found under `Output` > `Bandit` panel. You can control the log level running the `Developer: Set Log Level...` command from the Command Palette, and selecting your extension from the list. It should be listed using the display name for your tool. You can also set the global log level, and that will apply to all extensions and the editor.

If you need logs that involve messages between the Language Client and Language Server, you can set `"bandit.server.trace": "verbose"`, to get the messaging logs. These logs are also available `Output` > `Bandit` panel.

## Linting

Run `nox --session lint` to run linting on both Python and TypeScript code. Please update the nox file if you want to use a different linter and formatter.

## Packaging and Publishing

1. Build package using `nox --session build_package`.
1. Take the generated `.vsix` file and upload it to your extension management page <https://marketplace.visualstudio.com/manage>.

To do this from the command line see here <https://code.visualstudio.com/api/working-with-extensions/publishing-extension>

## Upgrading Dependencies

Dependabot yml is provided to make it easy to setup upgrading dependencies in this extension. Be sure to add the labels used in the dependabot to your repo.

To manually upgrade your local project:

1. Create a new branch
1. Run `npm update` to update node modules.
1. Run `nox --session setup` to upgrade python packages.

## Troubleshooting

### Changing path or name of `lsp_server.py` something else

If you want to change the name of `lsp_server.py` to something else, you can. Be sure to update `constants.ts` and `src/test/python_tests/lsp_test_client/session.py`.

Also make sure that the inserted paths in `lsp_server.py` are pointing to the right folders to pick up the dependent packages.

### Module not found errors

This can occurs if `bundled/libs` is empty. That is the folder where we put your tool and other dependencies. Be sure to follow the build steps need for creating and bundling the required libs.

Common one is [_pygls_][pygls] module not found.

[pygls]: https://github.com/openlawlibrary/pygls
