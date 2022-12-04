---
title: Set up on Linux
parent: Resources
---

**Important**: the following instructions apply to **Ubuntu 20.04.03** and later. These instructions may also apply to Debian, Linux Mint, and ChromeOS with Linux.

# 1. Fast install

- Open Terminal
- Copy the following block of commands (this assumes you are using ``bash``)
  - ```bash
    sudo apt install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev git
    
    git clone https://github.com/pyenv/pyenv.git ~/.pyenv
    echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
    echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
    echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n eval "$(pyenv init -)"\nfi' >> ~/.bashrc
    ~/.pyenv install 3.10:latest
    ~/.pyenv global 3.10:latest
    pip -m install pytest pyside6

    wget -q "https://go.microsoft.com/fwlink/?LinkID=760868" -O "vscode.deb"
    dpkg -i ./vscode.deb

    code --install-extension OnslowCollege.onslow-college-dit-extensions
    code
    
    wget "https://ftp.yz.yamagata-u.ac.jp/pub/qtproject/official_releases/qtcreator/8.0/8.0.1/qt-creator-opensource-linux-x86_64-8.0.1.run"
    chmod a+x ./qt-creator-opensource-linux-x86_64-8.0.1.run
    ./qt-creator-opensource-linux-x86_64-8.0.1.run
    ```
- Paste the commands into Terminal
- Press Enter
- You may be asked to enter your user password or press a key at certain points

# 2. Step-by-step instructions

## 2.1 Install developer tools

- Open Terminal
- Copy and paste the following commands (dependant on your distribution) and press Enter after each:
  - Ubuntu, Debian, ChromeOS with Linux Beta
    - ```bash
      sudo apt install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev git
      ```
  - Fedora, RedHat
    - ```bash
      sudo dnf groupinstall "Development Tools" -y
      ```
    - ```bash
      sudo dnf install zlib-devel bzip2 bzip2-devel readline-devel sqlite sqlite-devel openssl-devel xz xz-devel libffi-devel findutils -y
      ```

## 2.2 Install pyenv

- If it is not open already, open Terminal
- Copy and paste the following commands and press Enter after each:
  - ```bash
    git clone https://github.com/pyenv/pyenv.git ~/.pyenv
    ```
  - ```bash
    echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
    ```
  - ```bash
    echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
    ```
  - ```bash
    echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n eval "$(pyenv init -)"\nfi' >> ~/.bashrc
    ```
  - ```bash
    exec "$SHELL"
    ```

## 2.3 Install Python

- If it is not open already, open Terminal
- Copy and paste the following commands and press Enter after each:
  - ```bash
    pyenv install 3.10:latest
    ```
  - ```bash
    pyenv global 3.10:latest
    ```
  - ```bash
    python3 -m pip install pytest
    ```

## 2.4 Install Visual Studio Code

- If it is not open already, open Terminal
- Copy and paste the following commands and press Enter after each:
  - ```bash
    wget -q "https://go.microsoft.com/fwlink/?LinkID=760868" -O "vscode.deb"
    ```
  - ```bash
    dpkg -i ./vscode.deb
    ```

## 2.5 Install the Visual Studio Code extensions

- If it not open already, open Terminal
- Copy the following command:
  - ```bash
    code --install-extension OnslowCollege.onslow-college-dit-extensions
    ```
- Paste the command in to the Terminal
- Press Enter

## 2.6 Set up Settings Sync in Visual Studio Code

- Open Visual Studio Code
- Click on the Accounts tab
- Click "Turn on Settings Sync"
  - Click to sign in with your Microsoft account
    - Use your school email address and password to log in
    - Do **NOT** use your personal email address

If you use Visual Studio Code on a different computer, you will be able to repeat this process on it to use the same settings for all your computers.
