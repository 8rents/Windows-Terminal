# ![Scoop Icon](https://raw.githubusercontent.com/8rents/_/i/h1/bash.png) Msys2 ZSH / Bash Shells

### in Windows Terminal

> ***Finally, being able to effectively use ZSH / bash in Windows without WSL installed.***

---

***This article is part 3** in the [Windows Terminal Docs](..README.md)*

**Previous Article:** [Part 2: Package Management & Scoop](02-scoop-and-package-managers)

---

## Subjects in this Document

- Installing Msys2 with Scoop
- Understanding the different environments of msys2
- Creating profiles for a msys2 environment in Windows Terminal

----

## Installing Msys2 with Scoop

```powershell
scoop install msys2
```

> *By Default this installs msys2 to `~\scoop\apps\msys2`*

## Understanding the different environments of msys2

- `msys` and `msys2` (same thing now) - the base MSYS2 tool; all other environments below inherit from this one; contains the GCC 64-bit compiler and Cygwin C library
- `mingw32` - Minimalist GNU for Windows 32-bit; contains GCC 32-bit compiler
- `mingw64` - Minimalist GNU for Windows 64-bit; contains GCC 64-bit compiler
- `ucrt64 - UCRT` (Universal C Runtime) 64-bit; contains GCC 64-bit compiler; MSYS2 says: "If you are unsure, go with UCRT64 [this one]." See this comment too. Works by default only on Windows 10 or later.
- `clang64` - contains the LLVM/Clang 64-bit compiler
- `clang32` - contains the LLVM/Clang 32-bit compiler
- `clangarm64` - contains the LLVM/Clang 64-bit ARM (AArch64) compiler

## Creating profiles for a msys2 environment in Windows Terminal

### Adding a Bash Profile to Windows Terminal

In windows terminal open settings and then `open JSON File` (In the Lower Right Corner)

Add the following to the top of the Profiles section but just below  right below the `list` array:

```json
"list": 
        [
```

Below the `[`

```json

           {
		"name": "MSYS Bash",
		"guid": "{6f0ee3d1-ac4f-48ca-bcf5-a9795f9942d2}",
                "commandline": "%USERPROFILE%\\scoop\\apps\\msys2\\current\\msys2_shell.cmd -defterm -here -no-start -msys2 -shell bash",
		"icon": "ms-appx:///settings/icons/bash.png"
		
            },
```

#### Adding a custom icon to the bash profile

First Create a new icon file (PNG is good) and save it into the `windows-terminal/settings/icon/bash.png`						

1. At the end of the `"commandline"` line, after the last double quote, type a comma `,`
2. Make a new line with 2 tabs and then enter
3. ```json
"icon": "ms-appx:///settings/icons/bash.png"
```

*`ms-appx:///` means from within the app folder itself*

### Editing your bash `.profile` file

Your profile file is 

Within your default (Home) folder for the shell, the first time that you run it, it will create several profile files.

To get to your user home folder, run the following:

```bash
cd ~ && ls -1a
```

You should see the following output:

```bash
.
..
.bash_history
.bash_logout
.bash_profile
.bashrc
.profile
```

- `.bash_history` - Log of each command sent to the Bash shell
- `.bash_logout` - This file is run when you log out of the shell
em
- `.bash_profile` - Used to set up environment and configurations when logging in to the system. Global to all Bash shell sessions.
- `.bashrc` - Used to set up and configure the Bash shell and run when the user logs into the shell (or creates a new shell window). Specific to the current shell session.
- `.profile` - Used to set up environment and configurations when logging in to the system. Global to all shells.

### Creating an alias to a command with `.bashrc`

Lets create a simple alias to a common command.

Open `.bashrc`

```bash
nano .bashrc
```

Add the following to the file:

```bash
cd () {
    builtin cd "$@" || return

    case $PWD in
        "$HOME"|"$HOME"/*) ls -1
    esac
}
```

‎
---

**🤍 2023 [Brenton Holiday](https://brenton.holiday)**