# Flutter Web VSCode `.devcontainer`

This project is an environment for the development of a Flutter web application with [VSCode `.devcontainer`](https://code.visualstudio.com/docs/remote/containers).

[Flutter](https://flutter.dev) is a great toolkit for developing applications. However, it does come with quite some environment requirements. This project provides a complete, dockerized environment setup for VSCode and its [remote-containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) extension.

## Requirements

* [Docker](https://www.docker.com/get-started)
* [VSCode](https://code.visualstudio.com)
* [VSCode remote-containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) `ms-vscode-remote.remote-containers`

## Setup

1. Open this repository in a container using VSCode and its remote-containers extension.
2. Done. Now you have a fully working Flutter environmetn setup.

## Getting started with Flutter

Create a new Flutter project by executing the following command inside the container:

```bash
flutter create .
```

To run the new Flutter project execute:

```bash
flutter run
```

Additional information can be found in the official [Flutter documentation](https://flutter.dev)

## References
* This setup is based on [microsoft dart/.devcontainer](https://github.com/microsoft/vscode-dev-containers/tree/e36c62789da541bf80c8910ad59645e5777d4516/containers/dart/.devcontainer) which is licensed under the MIT License. See https://go.microsoft.com/fwlink/?linkid=2090316 for its license information.
* [Flutter](https://flutter.dev)
