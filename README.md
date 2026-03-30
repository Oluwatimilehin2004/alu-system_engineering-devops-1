# SSH - System Engineering & DevOps

## Description

This project covers the fundamentals of SSH (Secure Shell), including how to generate RSA key pairs, connect to remote servers securely, and configure the SSH client. It is part of the ALU System Engineering & DevOps curriculum.

---

## Concepts Covered

### What is a Server?
A server is a computer or program that provides services or resources to other computers (clients) over a network. Servers typically live in data centers — specialized facilities equipped with redundant power, cooling, and network infrastructure to ensure high availability.

### What is SSH?
SSH (Secure Shell) is a cryptographic network protocol used to securely connect to remote machines over an unsecured network. It replaces older, insecure protocols like Telnet and rsh by encrypting all communication between client and server.

### How to Create an SSH RSA Key Pair
```bash
ssh-keygen -t rsa -b 4096 -N "your_passphrase" -f ~/.ssh/your_key_name
```
This generates two files:
- `your_key_name` — the **private key** (keep this secret, never share it)
- `your_key_name.pub` — the **public key** (safe to share with remote servers)

### How to Connect Using an SSH RSA Key Pair
```bash
ssh -i ~/.ssh/school ubuntu@<server_ip>
```
The `-i` flag specifies the identity file (private key) to use for authentication.

### Why Use `#!/usr/bin/env bash` Instead of `/bin/bash`
- `#!/usr/bin/env bash` uses the `env` command to locate `bash` in the system's `PATH`, making scripts more **portable** across different environments and operating systems where `bash` may not be located at `/bin/bash`.
- `/bin/bash` is hardcoded and will fail if `bash` is installed elsewhere (e.g., on macOS or some Linux distros).

---

## Requirements

- Ubuntu 20.04 LTS
- All Bash scripts must be executable
- First line of all scripts: `#!/usr/bin/env bash`
- Second line must be a comment describing what the script does

---

## Files

| File | Description |
|------|-------------|
| `0-use_a_private_key` | Bash script that connects to a server using the private key `~/.ssh/school` with the user `ubuntu` |
| `1-create_ssh_key_pair` | Bash script that creates a 4096-bit RSA key pair named `school`, protected by the passphrase `betty` |
| `2-ssh_config` | SSH client configuration file that uses `~/.ssh/school` as the identity file and disables password authentication |

---

## Usage

### Task 0 — Connect using a private key
```bash
./0-use_a_private_key
```

### Task 1 — Create an RSA key pair
```bash
./1-create_ssh_key_pair
```
Generates `school` (private key) and `school.pub` (public key) in the current directory.

### Task 2 — SSH Client Configuration
Place the contents of `2-ssh_config` into `~/.ssh/config`:
```bash
cp 2-ssh_config ~/.ssh/config
```
After this, you can connect without specifying a key or password:
```bash
ssh ubuntu@<server_ip>
```

### Task 3 — Add a public key to the server
To allow another user to connect to your server, append their public key to `~/.ssh/authorized_keys` on the server:
```bash
echo "ssh-rsa AAAA..." >> ~/.ssh/authorized_keys
```

---

## Author

Built as part of the **ALU System Engineering & DevOps** program.

---
## 📦 Imported from [https://github.com/Kaylain7/alu-system_engineering-devops](https://github.com/Kaylain7/alu-system_engineering-devops)
*Imported using ForkYouToo - Learn, Adapt, Build*
