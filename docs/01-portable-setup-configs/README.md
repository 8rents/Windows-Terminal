# ![Windows Terminal Icon](https://raw.githubusercontent.com/8rents/_/i/h1/windows-terminal.png)  Portable Set Up & Configurations 

**in [Windows Terminal](../)**

> ***How to set up Windows Terminal in Portable Mode & back up all settings.***

---

This is **Part 1** in [**Windows Terminal Docs**](../)

---

## Subjects within this document

1. Installing Windows Terminal as "Portable"
2. Understanding Settings in Windows Terminal
3. What I keep in the `settings` folder
4. Modifying Settings & Creating a Default Theme 
5. Using `ms-appx://` for Relative Paths 
6. Setting up a GitHub Repository to have settings backed up in the cloud
7. How to restore your Windows Terminal Settings from GitHub


---

## Installing Windows Terminal as "Portable"

1. **[Download the x86 image](https://aka.ms/terminal-canary-zip-x64)**
2. Unzip the archive
3. Make sure that there is a file called `.portable` inside the folder.
4. Create a folder called `settings`
5. Open Windows Terminal

---

## Understanding Settings in Windows Terminal

All settings are modified in the `settings/settings.json` file  in the Windows Terminal Folder. There is a nice interface within Windows Terminal to modify settings, however using the JSON file is going to be the quickest and most direct way to modify these settings.

### The `state.json` file

The other file that is default in the `settings` folder is `state.json`. This file is not worked with directly as often as `settings.json`. The state file handles things like:

- Dialogs the user has chosen to hide with a [ ] Do not ask again checkbox, as proposed in issue 6641
- Which dynamic profiles have been generated, as a way to resolve user dissatisfaction around profiles "coming back"
- On-screen position of the window, active session state, layout, etc. for eventual restoration

---

## What I keep in the `settings` folder

I store these "How to" Documents, Fonts, my settings and state .json files, some alternate themes, icons and images within this folder. Basically anything that I want backed up.

---

## Modifying Settings & Creating a Default Theme 

Open Settings and adjust the following:

### Start Up Tab

1. Select which should be your Default Profile

### Interaction Tab

1. Enable automatically copy text to clipboard
2. Set plain text as the format that will be copied

### Appearance Tab

1. Use Acrylic Material: to Yes
2. Tab Width mode to Title Length

### Color Schemes Tab

1. Choose your desired default color scheme
2. Click Save on the Bottom

### Set up the Default Profile

Under Profiles, Select Defaults

1. Set up a default starting directory
   Keep in mind you can use a relative link here like this:

   ```powershell
   # This points to the same drive that 
   # Windows Terminal is running on
   \Devices\WPL
   ```

### Under Defaults > Additional Settings > Appearance

1. Choose the **default color scheme**
   **I chose "One Half Dark"**
2. Run the Hack fonts windows installer
3. Select Hack Font

## "*Cascade*" Default Settings into Shell Specific Settings

Under *Profiles* in the *Settings* View, There is the *Defaults* tab. Configure the *defaults* tab first and foremost. Settings here will "cascade" down to each additional shell you configure."

For example: if you want multiple shells to have the same starting directory, set it in defaults,m rather than setting it ion several places at once on a per shell basis.

 

---

## Using `ms-appx://` for Relative Paths 

I kep my icons in `settings > icons > shells > file.png`. When choosing an icon for a new profile, you can create a relative link from Windows Terminal root by using `ms-appx//:`

So my ZSH icon in the settings folder would be referenced at `ms-appx:///settings/icons/shells/zsh.png`

---

## Setting up a GitHub Repository to have settings backed up in the cloud

Within The Windows Terminal Folder, Open the `settings` folder. This folder will hold all configurations for Windows Terminal. 

### Creating a new Repository & Backing  up settings

The simplest way to create a GitHub Repository to hold these files is to: 

1. Download the [GitHub Desktop app for Windows](https://central.github.com/deployments/desktop/desktop/latest/win32).
2. [Sign up for a GitHub account](https://github.com/join) if you don't already have one.
3. Link the Desktop App and your account
4. In the Desktop app, create a new Repository and select the `settings` folder within the Windows Terminal directory. 
5. Add any more files that you want included in the Repository
6. In the desktop app, add all the files and commit them.
7. Push the repository to GitHub.

**Your settings are now backed up.!**

---

## How to restore your Windows Terminal Settings from GitHub

1. [Download the GitHub Desktop App](https://central.github.com/deployments/desktop/desktop/latest/win32) and get signed in
2. [Download Windows Terrminal](https://aka.ms/terminal-canary-zip-x64) & Unpack the .zip file
3. In the Unpacked folder delete the `settings` folder
4. Clone the Windows Terminal GitHub Repository to the Windows Terminal Folder you unzipped and make sure to name it `settings`. Make sure that it's placed in the same directory as the `.portable` file.
5. Open Windows Terminal

**Your Settings have been restored!**



---

## Links for Further Exploration

- [GitHub with SSH Keys](https://github.com/ScoopInstaller/Scoop/wiki/GitHub-with-SSH-Key)
- [GitHub Desktop for Windows - Download Link*](https://central.github.com/deployments/desktop/desktop/latest/win32)*

---

**Next** ▶
[**Part 2:** Package Management & Scoop ](02-scoop-and-package-managers)



---

**🤍 2023 [Brenton Holiday](https://brenton.holiday)**