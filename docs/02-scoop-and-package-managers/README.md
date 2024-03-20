# ![Scoop Icon](https://raw.githubusercontent.com/8rents/_/i/h1/scoop.png) Package Management & Scoop 

### *within Windows Terminal*

>  ***Understanding package management for Windows and using Scoop as my primary Package manager***

---

***This article is part 2** in the [Windows Terminal Docs](..README.md)*

**Previous Article:** [Part 1:Portable Set Up & Configuration](01-portable-setup-configs)

---

## Subjects within this document

1. The Roles of different package managers
2. Picking a daily driver shell for most purposes
3. Using Scoop for Windows package management
   - Optionally set a custom application install directory for scoop
   - Managing SSH keys and passwords
   - Essential Apps to install with scoop

---

## The Roles of Different Package Managers

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

---

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



---

### Essential Apps

https://github.com/ScoopInstaller/Scoop/wiki/Example-Setup-Scripts

---

## Next Article

[Part Msys2 ZSH / Bash Shells](03-msys2-bash-zsh-shells)

---

**🤍 2023 [Brenton Holiday](https://brenton.holiday)**