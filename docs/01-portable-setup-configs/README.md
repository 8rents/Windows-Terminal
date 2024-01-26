# Portable Set Up & Configurations

### *For Windows Terminal*

---

> ***How to set up Windows Terminal in Portable Mode & back up all settings.***

---

![](https://raw.githubusercontent.com/8rents/_/i/win-terminal.png)

## Subjects within this document

1. Installing Windows Terminal as a portable app & Cloning Settings from GitHub
2. Understanding Settings in Windows Terminal
3. Understanding Cascading Package Management

---

## Installing Windows Terminal as a portable app & Cloning Settings from GitHub

1. [**[Download the x86 image](https://aka.ms/terminal-canary-zip-x64)**]
2. [Clone settings from GitHub](https://github.com/8rents/Windows-Terminal)

**Name the downloaded folder `settings` and place it in the same directory as the exe and `.portable` file.**

All Changes I make to settings for Windows Terminal should go into the `settings` folder and be pushed to GitHub.

---

## Understanding Settings in Windows Terminal

All settings are modified in the `settings/settings.json` file  in the Windows Terminal Folder. There is a nice interface within Windows Terminal to modify settings, however using the JSON file is going to be the quickest and most direct way to modify these settings.

### The `state.json` file

The other file that is default in the `settings` folder is `state.json`. This file is not worked with directly as often as `settings.json`. The state file handles things like:

- Dialogs the user has chosen to hide with a [ ] Do not ask again checkbox, as proposed in issue 6641
- Which dynamic profiles have been generated, as a way to resolve user dissatisfaction around profiles "coming back"
- On-screen position of the window, active session state, layout, etc. for eventual restoration

---

## Understanding Cascading Package Management

I will be using a number of different package managers with and for different purposes.

| Name              | For                  | Installed By               | Description                                                  |
| ----------------- | -------------------- | -------------------------- | ------------------------------------------------------------ |
| **Windows Store** | Windows              | Windows                    | Installs Windows GUI apps.                                   |
| **Scoop**         | Windows / PowerShell | PowerShell                 | Scoop aims to install all Windows packages in portable / Limited Mode. |
| **Chocolatey**    | Windows / PowerShell | PowerShell                 | Choco is a bit more diverse than scoop. Sadly not as organized or portable. |
| **Pacman**        | Bash, ZSH            | Msys2 (Installed by Scoop) | Pacman installs apps for bash / zsh                          |
| **NPM**           | node.js              | Pacman                     | Node Package Manager installs packages for node.js           |
| **PIP**           | Python               | Pacman                     | Package Installer for Python programming language.           |

### Note that there is a cascading chain of installations going on here...

- **Windows Store** *(installs)* **Windows terminal** (Usual Route)
  - **Windows Terminal** (installs) **Scoop**
    - **Scoop** *(installs)* Msys2 **Bash**
      - Msys2 **Bash** *(installs)* **Pacman**
        - **Pacman** *(installs)* node.js & **NPM**
          - **NPM** *(installs)* **Express** (Node MVC Framework) 

**Wtf!?!?!  That's so many package managers and shells!?!?!** 

Each one has a different purpose. I could install node through PowerShell, but we all know PowerShell sucks and something would likely go wrong.

## My Daily Driver: ZSH

For the most part ZSH is going to be my shell of choice for most development purposes. If I need Windows Apps I'll be installing them through Scoop or Choco. If I need a node package I'll use NPM  *(or possibly PNPM or yarn, these are comparable to NPM and are designed to replace it)*

I'll want to keep package installs minimal that are not for the ZSH or Bash Shell.

I'm going to attempt to not install Git For PowerShell or Windows and instead use the msys2 bash version. I know with this version I can use `ssh-add` and store SSH keys to push and pull from GitHub via the command line. `ssh-add` does not work for PowerShell.

---

## Using Scoop package manager

Scoop will be my primary package manager for Windows and PowerShell. It differs from WinGet and Chocolatey in that it is clean, doesn't pollute your path, focuses on Open source software and application installs local to the user.

### Optional: Setting a custom directory for scoop installs 

1. Fix the PowerShell script execution policy

   ```powershell
   Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
   ```

2. Save a copy of the scoop installer (so that it can be run with parameters)

   ```powershell
   irm get.scoop.sh -outfile 'install-scoop.ps1'
   ```

3. Now run the installer locally and pass a custom parameter to name a different directory to install to

   ```
   
   ```

---

### GitHub with SSH Keys

https://github.com/ScoopInstaller/Scoop/wiki/GitHub-with-SSH-Key

---

### Essential Apps

---





---

**🤍 2023 [Brenton Holiday](https://brenton.holiday)**