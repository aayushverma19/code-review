# GoLang Code CI Checks | Code compilation

| **Author** | **Created on** | **Version** | **Last updated by**|**Last Edited On**|**Level** |**Reviewer** |
|------------|----------------|-------------|----------------|-----------------|-------------|-------------|
| Aayush Verma|   25-02-2025  | v1          | Aayush Verma   | 25-02-2025   |  Internal Reviewer | Komal Jaiswal |

## Table of Content

- [Introduction](#introduction)
- [Tool Identification](#tool-identification)
- [Why Use CI Checks and Automated Compilation for GoLang?](#why-use-ci-checks-and-automated-compilation-for-golang)
- [What is GoLang CI Code Compilation?](#what-is-golang-ci-code-compilation)
- [Different Tools for GoLang code Compilation](#different-tools-for-golang-code-compilation)
- [Comparison of different tools for GoLang code compilation](#comparison-of-different-tools-for-golang-code-compilation)
- [Best Practices](#best-practices)
- [Recommendations](#recommendations)
- [Contact](#contact)
- [References](#references)


## Introduction

In Go (Golang), code compilation is the process of converting source code into a binary executable file that can be run on a system. Go is a statically compiled language, meaning the entire program is compiled into a single binary, including all dependencies.

## Tool Identification

#### For Code Compilation:
**Go build:**
 - The standard compilation tool to build binaries.

 - Automatically detects dependencies and builds the project.


## Why Use CI Checks and Automated Compilation for GoLang?

Using CI checks and automated compilation in GoLang ensures code quality, early bug detection , etc. Tools like **go build** do the compilation and **go test** catch errors. CI pipelines provide real-time feedback and saving time .


## What is GoLang CI Code Compilation?

GoLang CI Code Compilation means automatically checking and building your Go code using a CI (Continuous Integration) system. it uses tool go build to compile the code .  This process happens automatically whenever you push new changes .



## Different Tools for GoLang code Compilation
|       Tools      |          Description               |
|:-----------------:|:-------------------------------------:|
| **go build** |  The built-in tool for compiling Go code into binary (0 or 1).
| **Bazel**  | A powerful build system that supports Go and other languages.
| **Make** | A build automation tool to define and manage compilation steps in a Makefile.
| **Taskfile** | A modern alternative to Makefiles, written in YAML.

## Comparison of different tools for GoLang code compilation

|       Tools     |      Key Features                |    Use Case | Example Command |
|:-----------------:|:-------------------------------------:|:------------------:|:--------------:|
| **go build** | Simple, fast, auto-detects dependencies. | Basic compilation tasks. | go build main.go
| **Bazel**  | Parallel builds, dependency management. | Large projects with complex workflows. | bazel build 
| **Make** | Automates repetitive tasks. | Projects needing task orchestration. | make build
| **Taskfile** | YAML-based task runner | Use for Small projects | task build

## Best Practices

| **Best Practice**                    | **Description**                                                                                                      |
|--------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| **Use Go Modules**                   | Always use Go Modules (`go mod`) to manage dependencies. This ensures that your project dependencies are consistent.    |
| **Automate Builds**                  | Automate your build process with scripts (e.g., Makefile or Taskfile) to handle compilation, testing, and other tasks.  |
| **Use go fmt for Code Formatting**   | Before compiling, run `go fmt` to automatically format your code. This ensures consistent style across your codebase.   |


## Recommendations

Using **go build** tool for compiling your code, as it's simple and fast .  This tool automatically handles the compilation of the code, allowing developers to focus more on writing features rather than dealing with build issues.

## Contact

For more information, feedback, or assistance, feel free to contact:
| **Name**       | **Email Address**        |
|----------------|--------------------------|
| Aayush Verma   | <aayush.verma@mygurukulam.co> |


## References

| **Link**             | **Description**                                    |
|-----------------------------------------------------------------------------|--------------------------------------------------|
| [Go build installation](https://www.geeksforgeeks.org/how-to-build-and-install-go-program/) | Go build installation  |
| [Go Build Documentation](https://www.digitalocean.com/community/tutorials/how-to-build-and-install-go-programs) | Go Build Documentation |
| [POC of GoLang code compilation](https://github.com/snaatak-Zero-Downtime-Crew/Documentation/blob/Aayush-SCRUM-81/Application%20CI%20Design/GoLang%20CI%20Checks/Code%20Compilation/POC/README.md) | POC of GoLang code compilation |
