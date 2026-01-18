# autogit

A secure Git + SSH manager for shared/lab PCs that helps you work safely on public computers without leaving credentials behind.

## Overview

autogit is a bash script that simplifies the process of setting up temporary SSH keys, cloning repositories, and ensuring all work is committed and pushed before cleaning up all traces of your session.

## Features

- Generate temporary SSH keys for secure authentication
- Configure Git with your credentials
- Clone and set up repositories quickly
- Check status of uncommitted/unpushed work
- Auto-commit and push changes before cleanup
- Securely remove all SSH keys and repositories after session

## Installation

1. Download the autogit script:
```bash
wget https://raw.githubusercontent.com/aniketkarkhelikar/autogit/main/autogit
```

2. Make it executable:
```bash
chmod +x autogit
```

3. (Optional) Move to a directory in your PATH:
```bash
sudo mv autogit /usr/local/bin/
```

## Usage

### Setup

Initialize Git and SSH configuration:

```bash
autogit setup
```

This will:
- Prompt you for GitHub username, repository name, Git username, and email
- Generate a temporary SSH key
- Display the public key for you to add to GitHub
- Clone your repository to `~/dev/`
- Configure Git with your credentials

### Check Status

Check your SSH setup and uncommitted/unpushed changes:

```bash
autogit status
```

### Cleanup

Commit, push, and remove all traces:

```bash
autogit cleanup
```

This will:
- Detect any uncommitted or unpushed work
- Prompt you to commit and push changes
- Remove SSH keys from `~/.ssh/`
- Remove work directory `~/dev/`
- Kill SSH agent processes

## Workflow Example

```bash
# Start your session
autogit setup

# Work on your code
cd ~/dev/your-repo
# ... make changes ...

# Check status anytime
autogit status

# When done, cleanup everything
autogit cleanup
```

## Security

This tool is designed for shared/public computers where you don't want to leave:
- SSH keys
- Git configurations
- Repository data

Always run `autogit cleanup` when you're done to ensure no sensitive data remains on the machine.

## Requirements

- bash
- git
- ssh-keygen
- ssh-agent

## Author

Aniket

## License

This project is open source and available for anyone to use and modify.