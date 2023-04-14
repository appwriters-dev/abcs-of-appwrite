---
id: ls01-introduction-and-installation
slug: introduction-and-installation
title: Introduction and Installation
---

Appwrite's CLI can be very helpful for developers who want to automate their workflow. It can be used to create and manage projects, manage teams, manage users, and much more. In this chapter, we will learn how to install the Appwrite CLI and how to use it.

## Installation

The Appwrite CLI is available for Linux, macOS, and Windows. You can download the latest version from the [Appwrite CLI GitHub repository](https://github.com/appwrite/sdk-for-cli/releases). If you have `npm` you can easily install using the following command:

```bash
npm install -g appwrite-cli
```

You can also install pre-built binaries for different platforms.

### Linux / MacOS Terminal

```bash
wget -q https://appwrite.io/cli/install.sh  -O - | /bin/bash
```

### MacOS via Homebrew

```bash
brew tap appwrite/sdk-for-cli https://github.com/appwrite/sdk-for-cli
brew update
brew install --HEAD appwrite 
```

### Windows

```powershell
iwr -useb https://appwrite.io/cli/install.ps1 | iex
```