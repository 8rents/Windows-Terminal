# ![Scoop Icon](https://raw.githubusercontent.com/8rents/_/i/h1/bash.png) Msys2 ZSH / Bash Shells

**in [Windows Terminal](../)**

> ***Finally, being able to effectively use ZSH / bash in Windows without WSL installed.***

---

This is **part 3** in [**Windows Terminal Docs**](../)

**◀ Previous** 
[**Part 2**: Package Management & Scoop](../02-scoop-and-package-managers/)

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

#### Adding a custom icon to the `bash` profile

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

## Alias `--noconfirm` for use with `	pacman`

Having to hit `Y` every single time you want to install something is super annoying. Set up an `alias` in your `.bashrc` file.

```bash
alias pacman="pacman --noconfirm"
```

> *Now you can skip the annoying confirmation*

## Adding `zsh` & the `Fish` Shell to Windows Terminal

In the `settings.json` file in the `settings` folder of Windows Terminal, there is an array `list` (*It opens and closes with square brackets*).

Within the `list` array. Add the following:

> **Important Note:** *Formatting is everything with `json` files. If there is an item following the preview one within an array or object context a comma is required. **Make sure to get the formatting correct otherwise the file is not going to be interpreted properly.***

### Adding the Bash Shell

The following snippet is for the bash shell. Note that the `commandline` path is only going to be as such if `msys2`was installed via **scoop**.

```bash
{
	"commandline": "%USERPROFILE%\\scoop\\apps\\msys2\\current\\msys2_shell.cmd -defterm -here -no-start -msys2 -shell bash",
	"guid": "{6f0ee3d1-ac4f-48ca-bcf5-a9795f9942d2}",
	"icon": "ms-appx:///settings/icons/bash.png",
	"name": "bash"
},
```

> **Note about icons:** *I simply photoshopped myself some icons that I liked for each shell and dropped the finished `.png` files of them into a `png`* folder within my `settings`folder. Then I referenced them out of there.
>
> ```
> ms-appx:///settings/icons/bash.png
> ```
>
> `ms-appx` simply means within the Microsoft app.

#### Adding the ZSH Shell

Same drill as above except with the zsh shell.

```bash
{
	"commandline": "%USERPROFILE%\\scoop\\apps\\msys2\\current\\msys2_shell.cmd -defterm -here -no-start -msys2 -shell zsh",
	"guid": "{9e554928-79f1-5996-b101-1b4e7acf32a6}",
	"icon": "ms-appx:///settings/icons/zsh.png",
	"name": "zsh"
},
```

### Adding the Fish Shell to Windows Terminal

Same as the 2 above. In the settings file add:

```bash
{
	"commandline": "%USERPROFILE%\\scoop\\apps\\msys2\\current\\msys2_shell.cmd -defterm -here -no-start -msys2 -shell fish",
	"guid": "{3e42746f-e723-54e2-ae37-47dedbfc871e}",
	"icon": "ms-appx:///settings/icons/fish.png",
	"name": "fish"
}
```



## ‎Installing and configuring Z Shell (aka ZSH)

First make sure that `git` is installed via `pacman`.

```bash
pacman -S git
```

From within the bash shell and pacman install `zsh`. 

```bash
pacman -S zsh
```

> ***Hopefully you took my advice and set an alias for `--noconfirm`***.

### Installing `oh-my-zsh`

Oh My ZSH is the best plugin manager / framework for any shell past, present or future.

First make sure that `wget` & `git` have been installed via `pacman`

```bash
pacman -S wget
```

> **NOTE:** *If for some reason you haven't installed `git` or `zsh`, make sure to install those at the same time.*

#### Then install `oh-my-zsh` via `wget`

```bash
sh -c "$(wget https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
```

---

**Next** ▶
[**Part 4:** Pacman Package Manager](../04-pacman-package-manager/)

---

**🤍 2023 [Brenton Holiday](https://brenton.holiday)**