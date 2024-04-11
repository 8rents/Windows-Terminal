# ![Pacman Package Manager](https://raw.githubusercontent.com/8rents/_/i/h1/pacman.png)  Pacman Package Manager 

**in msys2 bash in [Windows Terminal](../)**

> ***Pacman is the default package manager for Arch Linux. It's available to use through msys2 installed on Windows.***

---

This is **part 4** in [**Windows Terminal Docs**](../)

**◀ Previous** 
[**Part 3**: Msys2 ZSH / Bash Shells](../03-msys2-bash-zsh-shells/)

---

## Getting Started

### Alias `--noconfirm` in your `.bashrc` file so you don't have to keep hitting `Y` with every install.

Having to hit `Y` every single time you want to install something is super annoying. Set up an `alias` in your `.bashrc` file.

```bash
alias pacman="pacman --noconfirm"
```

> *Now you can skip the annoying confirmation*

### Basic Pacman Commands

These are the basic Pacman command options. 

- **`-h` `--help`** - Display help for that command
- **`-V` `--version`** - display Pacman Version
- **`-D` `--database`** - Database info
- **`-F` `--files`** - Files info
- **`-Q` `--query`** - Search for a program
- **`-R` `--remove`** - uninstall a program
- **`-S` `--sync`** - install a program
- **`-T` `--deptest`** - test dependencies
- **`-U` `--upgrade`** - upgrade

Each command can be doubled up. So for example to see the help pages for the database command you would use either: 

```bash
# Shorthand
-Dh
# Longform
--database --help
```

## Common Commands

### Update all packages

Update the package database and update all packages on the system

```bash
pacman -Syu
```

### Searching for packages

To search the repositories for available packages you can use the command `pacman -Ss keyword`. **It will search both the package name and the description** for the keyword. For example, to search for packages containing the keyword `smplayer` you could use:

```bash
pacman -Ss smplayer
```

This will search the repositories. If you wanted to **search your installed packages** you could use:

```bash
pacman -Qs smplayer
```



---

## Interesting Links

- [Pacman Commands](https://itsfoss.com/pacman-command/)
- [Pacman Overview / Manjaro Linux Help Pages](https://wiki.manjaro.org/index.php/Pacman_Overview)

---

**Next** ▶
[**Part 5:** Node.js, NVM & NPM](../05-node-and-version-and-package-manager/)

---

**🤍 2024 [Brenton Holiday](https://brenton.holiday)**