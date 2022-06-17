# Active Directory Setup

This repository tree covers the steps used when following John Hammond's Active Directory setup playlist on his YouTube channel.


# Miscellaneous Notes:
    - Chocolatey (https://chocolately.org/install)
        - Follow the "Install Chocolately for Individual Use" instructions i.e., copy and run the PS command
        - Close & reopen the terminal
    - Git
        - `choco install git`
        - Close & reopen the terminal
        - Generate SSH keys and copy them to the clipboard so that they can be added to Git's settings 
            `ssh-keygen`
            `type c:\users\local_admin\.ssh\id_rsa.pub | clip`
            `git clone git@github.com:StevenBambrick/active_directory.git`
    - VSCode
        - `choco install vscode`

# Configuring git
    `git config --global user.email "you@gmail.com"`
    `git config --global user.name "Your Name"`

# First commit to the git repo
    `git add .`
    `git commit`
    `git push`