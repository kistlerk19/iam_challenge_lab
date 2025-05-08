# IAM Challenge - Linux User and Group Management

This repository contains automation scripts for Linux Identity and Access Management (IAM) tasks. The tools provide a streamlined way to handle user and group creation, management, and cleanup through CSV-based configurations.

Screenshots demonstrating the commands running can be found in the `screenshots/` folder.

## Contents

- `iam_challenge` - Script for creating users and groups with specific settings
- `iam_cleanup` - Script for safely removing users and groups
- `users.csv` - Sample CSV file containing user data

## Requirements

- Linux operating system
- Root/sudo privileges
- Basic mail utilities (for email notifications) -- mailutils

## iam_challenge

### Overview

The `iam_challenge` script automates the creation of users and groups in Linux systems based on data from a CSV file. It includes features for:

- Creating users with home directories
- Setting temporary passwords with expiration
- Enforcing password complexity
- Assigning users to groups
- Setting appropriate home directory permissions
- Sending email notifications

### Usage

```bash
chmod +x iam_challenge
```
```bash
sudo ./iam_challenge [OPTIONS]
```
To create users & groups as well as add sending email

```bash
sudo ./iam_challenge -e
```

### Options

- `-f, --file FILE` - Specify input CSV file (default: users.csv)
- `-l, --log FILE` - Specify log file (default: iam_setup.log)
- `-p, --password PWD` - Set temporary password (default: AmalitechGTP@Accra123)
- `-e, --email` - Enable email notifications
- `-c, --config FILE` - Specify config file (default: .iam_config.env)
- `-h, --help` - Display help message

### Example

```bash
sudo ./iam_challenge -f custom_users.csv -e -l setup.log
```

## iam_cleanup

### Overview

The `iam_cleanup` script safely removes users and optionally their home directories and groups, based on the same CSV file used for creation.

### Usage
```bash
chmod +x iam_cleanup
```
```bash
sudo ./iam_cleanup [OPTIONS]
```
To delete the groups as well 

```bash
sudo ./iam_cleanup -g
```

### Options

- `-f, --file FILE` - Specify input CSV file (default: users.csv)
- `-l, --log FILE` - Specify log file (default: cleanup.log)
- `-g, --groups` - Also remove groups after removing users (default: false)
- `-k, --keep-home` - Keep home directories (default: home dirs are removed)
- `-b, --backup` - Backup home directories before removal
- `-i, --interactive` - Ask for confirmation before each deletion
- `-h, --help` - Display help message

### Example

```bash
sudo ./iam_cleanup -f users.csv -b -i -g
```

## CSV File Format

The `users.csv` file should follow this format:

```
username,fullname,group,email
```

### Sample Content

```
jdoe,John Doe,engineering,john.doe@example.com
asmith,Alice Smith,engineering,alice.smith@example.com
mjones,Mike Jones,design,mike.jones@example.com
```

## Features

- **Automated User Management**: Streamlines the creation and deletion of multiple users
- **Group Management**: Creates and manages groups as needed
- **Password Policies**: Enforces secure password policies with expiration
- **Notification System**: Optional email notifications on account creation
- **Backup System**: Option to backup home directories before removal
- **Interactive Mode**: Confirmation prompts for critical operations
- **Detailed Logging**: Comprehensive logging of all operations

## Author

Ishmael Gyamfi (May 2025)