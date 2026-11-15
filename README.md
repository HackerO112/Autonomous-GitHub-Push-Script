

# Autonomous GitHub Push Script

<p align="center">
  <img src="https://img.shields.io/badge/Shell-Bash-blue?style=for-the-badge&logo=gnu-bash&logoColor=white" alt="Shell Script">
  <img src="https://img.shields.io/badge/GitHub-CLI-black?style=for-the-badge&logo=github" alt="GitHub CLI">
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" alt="MIT License">
</p>

<p align="center">
  A fully autonomous bash script that prepares your local project and pushes it to a new or existing GitHub repository.
</p>

## 📋 Table of Contents

- [About](#about)
- [✨ Features](#features)
- [🚀 Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Usage](#usage)
- [⚙️ How It Works](#how-it-works)
- [🤝 Contributing](#contributing)
- [📜 License](#license)

## About

`githubcommit.sh` is an interactive helper for preparing a local Git repository and pushing it to GitHub. It checks prerequisites and authentication, asks for a repository name, stages changes, and creates or pushes to the selected repository. Review the target and staged files before running it.

## ✨ Features

| Feature | Description |
|---------|-------------|
| **Interactive workflow** | Confirms repository details and visibility before creating a repository. |
| **Dependency Checks** | Automatically verifies if git and the GitHub CLI (gh) are installed. |
| **Auto-Installation** | If the GitHub CLI (gh) is not found, it attempts to install it using the system's package manager (supports macOS via Homebrew, and Debian/Ubuntu/Fedora/CentOS on Linux). |
| **Authentication Handling** | Checks if you're logged into GitHub and prompts you to log in if you aren't. |
| **Git Identity Setup** | If your local Git user.name and user.email are not configured, it will ask for them and set them for the current repository. |
| **Safe repository handling** | New repositories default to private; existing repositories are pushed without force. |
| **Effortless Commits** | Automatically adds all project files and creates an initial commit. |
| **User-Friendly** | Provides clear, colored output for each step of the process. |

## 🚀 Getting Started

Getting started is as simple as running the script in your project's root directory.

### Prerequisites

- A terminal or command-line interface.
- A GitHub account.
- `sudo` or administrative privileges may be required for the one-time installation of the GitHub CLI.

### Usage

1. **Download the Script**:
   Save the script in your project's root directory as `githubcommit.sh`.

2. **Make it Executable**:
   Open your terminal, navigate to your project directory, and run the following command to give the script execution permissions:
   ```bash
   chmod +x push_to_github.sh
   ```

3. **Run the Script**:
   Execute the script from your project's root directory. Do not use `sudo`.
   ```bash
   ./githubcommit.sh
   ```

The script uses the account already authenticated in GitHub CLI, asks for a repository name and Git identity if needed, and asks whether a new repository should be private or public (private is the default).

## ⚙️ How It Works

The script performs the following steps in order:

1. **Checks for Git and GitHub CLI (gh)**: Ensures the necessary tools are available.
2. **Authenticates with GitHub**: Uses `gh auth status` to verify your login session.
3. **Collects Repository Info**: Reads the authenticated GitHub username and prompts for a repository name.
4. **Initializes Git**: Runs `git init` if the project is not already a Git repository.
5. **Configures Git Identity**: Checks `git config` and prompts for your name and email if they are not set.
6. **Commits Files**: Stages all files with `git add .` and creates a commit.
7. **Creates & Pushes to GitHub**: Uses `gh repo create` to make a new repository and push your code, or updates the remote and pushes if the repository already exists.

## 🤝 Contributing

Contributions are welcome! If you have ideas for improvements or find a bug, please feel free to open an issue or submit a pull request.

1. Fork the repository.
2. Create a new branch: `git checkout -b feature/your-feature-name`
3. Make your changes.
4. Commit your changes: `git commit -m "Add some great feature"`
5. Push to the branch: `git push origin feature/your-feature-name`
6. Open a pull request.

## 📜 License

This project is open source and available under the [MIT License](LICENSE).

---

<p align="center">
  Made with ❤️ by developers, for developers
</p>
