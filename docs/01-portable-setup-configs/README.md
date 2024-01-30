# ![Windows Terminal Icon](https://raw.githubusercontent.com/8rents/_/i/h1/windows-terminal.png) Portable Set Up & Configurations 

### in Windows  Terminal

> ***How to set up Windows Terminal in Portable Mode & back up all settings.***

---

[Windows Terminal --**Table of Contents**](../README.md)

---

## Subjects within this document

1. Installing Windows Terminal as a portable app & Cloning Settings from GitHub

2. Understanding Settings in Windows Terminal


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

### GitHub with SSH Keys

https://github.com/ScoopInstaller/Scoop/wiki/GitHub-with-SSH-Key

---

### Essential Apps

---

## Next  Article

[Part 2: Package Management & Scoop ](02-scoop-and-package-managers)



---

**🤍 2023 [Brenton Holiday](https://brenton.holiday)**