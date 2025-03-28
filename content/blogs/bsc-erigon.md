---
title: "BSC Node Deployment with Erigon [Draft]"
slug: "bsc-erigon"
url: blogs/bsc-erigon/
date: 2023-05-30
draft: true
# link: "https://docs.ankr.com/nodes/binance-smart-chain/how-to-run-a-bsc-node-on-erigon"
author: "Corey Wooten"
tags:
  - Blockchain
  - Node Deployment
  - Linux Server
  - Erigon
  - BNB Chain
image: /images/projects/misc/bsc-erigon.png
description: "A step-by-step guide to deploying a full Binance Smart Chain node using the Erigon client on a remote Linux server."
toc: false
---

<details>
  <summary> Setup Instructions </summary>

```bash
# Enable admin privileges for the user.
sudo rm /var/lib/apt/lists/lock
sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/dpkg/lock*
sudo dpkg --configure -a

# Generate a new SSH key pair for enhanced security.
ssh-keygen -b 4096

# Update existing Linux packages.
sudo apt update && apt upgrade && apt automremove -y

# Use the 'apt' command to install or remove software.
sudo apt purge golang* # Removes existing GoLang version.
sudo apt install git && sudo apt install npm && sudo apt install axel

# Uninstall & reinstall GoLang.
go version
sudo apt purge golang*
sudo apt install snapd
sudo snap install go --classic
sudo tar -C /usr/local -xzf go0.00.00linux-amd64.tar.gz
# Replace [go0.00.00] with the updated version

# Create a new Go directory & set the $PATH location.
mkdir ~/.go
GOROOT=/usr/local/go
GOPATH=~/.go
PATH=$PATH:$GOROOT/bin:$GOPATH/bin

# Update GoLang command & set the location of /bin/go.
sudo update-alternatives --install "/usr/bin/go" "go" "/usr/local/go/bin/go" 0
sudo update-alternatives --set go /usr/local/go/bin/go

# Additional Installations
sudo apt install git && sudo apt install npm && sudo apt install axel
sudo apt-get install ntp -y && service ntp start && date

# Configure the node specifications.
sudo apt install mdadm
```
</details> 

<br>

<details>
  <summary> Roadblocks </summary>

```bash
init 6
:'This command closes the connection and
    termporarily locks user out of the server.'
```
</details> 

<br> 

### 00 Prerequisites 

#### 0.1 – System Requirements 

| Specification | Minimum Requirement | Used for Demo |
|----------|----------|----------|
| Hardware | Linux / Mac / Windows system running the latest OS version | MacBook Pro running MacOS Monterey 12.2 | 
| SSD / NVMe Storage | ≥ 2 TB | 7.68 TB | 
| RAM | ≥ 16 GB | 256 GB | 
| Server OS | Linux OS (64-bit) | Ubuntu Server 20.04.3 | 
| Network Settings | SSH enabled, TDP/UDP traffic enabled | 

#### 0.2 – Hardware and Software 

1. Linux, Mac, or Windows computer running the latest operating system (OS) version.
2. Terminal Emulator / SSH Client (Mac: Terminal || Windows: PuTTy || Linux: Ubuntu Server)
3. Login credentials for the server being accessed.

#### 0.3 - Enabling / Disabling Secure Shell (SSH) 

To access the server remotely, the user must enable Secure Shell (SSH) on their home system. 

1. Enter the following command(s) in Terminal to enable or disable SSH on the system:     
```bash
sudo systemsetup -setremotelogin on     # Enable SSH
sudo systemsetup -setremotelogin off    # Disable SSH
Password: [?]   # System password
```

### 01 SETTING UP THE REMOTE SERVER 

#### 1.1 — Connecting to the Remote Server 

1. To access the server with SSH, run the following commands (replacing the details inside the {brackets} with your provided credentials): 
```bash
ssh username@SERVER_IP_ADDRESS  # Server access login
Password: [?]   # Access password 

# Use [CTRL+D] at anytime to suspend the connection.
```

#### 1.2 — Optimize the Server for Node Operations 

Once you’re connected to the server with SSH, follow the steps below to setup and install the dependencies required for your node. 

1. Update the Ubuntu System and upgrade the OS components:
```bash
sudo apt update && apt upgrade && autoremove -y
```

2. Install the latest version of **[GoLang](https://go.dev/dl/)**:
```bash 
# Check and remove existing Go version 

go version  # Checks existing version
sudo apt purge golang*  # Removes existing version 
wget https://go.dev/dl/go1.XX.X.linux-amd64.tar.gz  # Installs latest version
sudo tar -C /usr/local -xzf go1.XX.X.linux-amd64.tar.gz     # Extracts Go in the local folder 
mkdir ~/.go 
```
```bash 
# Set ENV variables and $PATH location 

GOROOT=/usr/local/go
GOPATH=~/.go
PATH=$PATH:$GOROOT/bin:$GOPATH/bin
``` 
```bash 
# Update Go command 

sudo update-alternatives --install "/usr/bin/go" "go" "/usr/local/go/bin/go" 0
sudo update-alternatives --set go /usr/local/go/bin/go
```
```bash 
# Confirm update to latest version 

go version
```

<img src="/images/goversion.png" alt="Confirm Go Version" width="450" height="82" /> <br><br>

### 02 Installing Dependencies 

#### 2.1 – Viewing and Verifying the Server’s Components

Run the List Block command to view drives and partitions installed on the server. 
```bash
Isblk
```

```bash 
# Dependencies

sudo apt-get update 
sudo apt dist-upgrade -y
sudo apt autoremove -y 
sudo apt install git 
sudo apt install npm 
```

<br><br>

### Sources 
- *[Gnosis client development team Joins Erigon (formerly Turbo-Geth) to Release Next-Gen Ethereum Client](https://medium.com/openethereum/gnosis-joins-erigon-formerly-turbo-geth-to-release-next-gen-ethereum-client-c6708dd06dd#9031)* 
- *[BNB Chain > Full Node](https://docs.bnbchain.org/bnb-smart-chain/developers/node_operators/full_node/?h=full+node)*