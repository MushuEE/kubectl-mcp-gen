# `kubectl-mcp-gen` Plugin

A `kubectl` plugin designed to interact with and output information from your hypothetical MCP (Model Context Protocol) tool in a structured YAML format.

This plugin extends `kubectl`'s functionality, allowing you to quickly query and visualize MCP tool status and details directly from your command line.

## Table of Contents

* [Description](https://www.google.com/search?q=%23description)

* [Project Structure](https://www.google.com/search?q=%23project-structure)

* [Prerequisites](https://www.google.com/search?q=%23prerequisites)

* [Building the Plugin](https://www.google.com/search?q=%23building-the-plugin)

* [Installation](https://www.google.com/search?q=%23installation)

* [Usage](https://www.google.com/search?q=%23usage)

* [Development](https://www.google.com/search?q=%23development)

## Description

The `kubectl-mcp-gen` plugin provides a simple interface to retrieve and display diagnostic and status information from a conceptual MCP tool. It's built in Go and utilizes `cobra` for robust command-line parsing. The primary goal is to present this information in a clear, Kubernetes-native YAML format, making it easy to integrate with other `kubectl` workflows or `jq`/`yq` for further processing.

## Project Structure

The project follows a standard Go project layout for CLI tools:

your-kubectl-plugin/
├── cmd/
│   └── kubectl-mcp-gen/  # Contains the main entry point for the plugin
│       └── main.go       # The main application logic
├── go.mod                # Go module definition
├── go.sum                # Go module checksums
├── README.md             # This file
└── ...                   # Other potential files (pkg/, tests, etc.)

## Prerequisites

* [Go (Golang)](https://golang.org/doc/install) (version 1.16 or higher recommended)

* [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)

* A Git client (for cloning the repository)

## Building the Plugin

To build the executable binary for the plugin, navigate to the root of this repository in your terminal and run the following command:

```
go build -o kubectl-mcp_gen cmd/kubectl-mcp-gen/main.go
```

* **Note the underscore (`_`) in `kubectl-mcp_gen`**. This is crucial for `kubectl` to correctly interpret the plugin name as `mcp-gen` (with a hyphen) when invoked.

* This command will create an executable file named `kubectl-mcp_gen` in the root of your project directory.

## Installation

After building the plugin, you need to place the `kubectl-mcp_gen` executable in a directory that is included in your system's `PATH` environment variable. A common location for user-installed binaries is `/usr/local/bin/`.

```
sudo mv -f kubectl-mcp_gen /usr/local/bin/
```

* You might need `sudo` to move the file to `/usr/local/bin/`.

* The `-f` flag ensures any older version of the plugin is overwritten.

### Verify Installation

You can verify that `kubectl` recognizes your new plugin by running:

> kubectl plugin list

You should see `kubectl-mcp_gen` listed, pointing to its location in your `PATH`.

## Usage

Once installed, you can invoke the plugin directly through `kubectl`:

> kubectl mcp-gen
