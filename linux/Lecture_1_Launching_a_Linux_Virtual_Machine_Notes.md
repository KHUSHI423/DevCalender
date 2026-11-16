# Lecture 1 – Launching a Linux Virtual Machine

> **Source:** Lecture transcript, “Lecture 1 - Launching a Linux Virtual Machine”  
> **Purpose:** Set up a Linux command-line environment on a Windows computer, and explore alternatives such as WSL, cloud terminals, and a mobile terminal app.

---

## 1. Why Use a Linux Virtual Machine?

A virtual machine (VM) lets you run Linux on a computer that already has another operating system, such as Windows.

### Why might you need one?

- Your laptop came with Windows pre-installed and you do not want to remove it.
- You have already paid for the Windows installation and want to keep it.
- Dual booting may not be possible because the BIOS/UEFI configuration is restricted by the original equipment manufacturer (OEM).
- You want to experience Linux almost like a native operating system.
- You want a separate environment for learning Linux commands and practicing shell work.

### Main idea

A Linux VM runs on top of the existing host operating system. You can use Linux without replacing or disturbing Windows.

---

## 2. Requirements for Running a Linux VM

The lecture recommends the following components.

| Requirement | Purpose / Details |
|---|---|
| Linux ISO image | Installation media used to install Linux inside the VM. |
| Hypervisor | Software that creates and runs virtual machines. |
| Disk space | Space allocated to the virtual machine's virtual hard disk. |
| RAM | Memory allocated to the VM while it is running. |

### 2.1 Linux ISO image

- Download an ISO image of the Linux distribution.
- The lecture uses **Ubuntu 20.04 LTS** as its example.
- It recommends the `x86_64` platform for Intel- or AMD-based laptops.
- The transcript describes the ISO as approximately 3 GB at the time of the lecture.
- The lecture directs users to the Ubuntu website to obtain the ISO.

> **Version note:** Ubuntu 20.04 and the download-size details are the versions and figures used in this lecture. They describe the tutorial at the time it was recorded, not necessarily the latest Ubuntu release today.

### 2.2 Hypervisor

A hypervisor is software that creates and manages virtual machines.

The lecture demonstrates two options:

1. Oracle VM VirtualBox
2. VMware Workstation Player

Both are presented in the lecture as options with free versions/usage available.

### 2.3 Hardware requirements mentioned

| Resource | Lecture's guidance |
|---|---|
| Disk space | About 20 GB is sufficient to get started. |
| RAM | A system with 4 GB RAM may not be a good choice for running a VM. |
| RAM | A system with 8 GB or more should work reasonably well for the VM. |

**Important:** The VM uses part of the host computer's RAM and disk space. The host operating system continues to run while the VM is active.

---

## 3. Overall Process: From Windows to Linux

The general process is:

1. Download the Ubuntu ISO image.
2. Download a hypervisor such as VirtualBox or VMware Workstation Player.
3. Install the hypervisor on Windows.
4. Open the hypervisor.
5. Create a new virtual machine.
6. Allocate RAM and virtual disk space.
7. Attach the Ubuntu ISO image to the VM.
8. Start the VM and install Ubuntu.
9. Create the first Linux user account and password.
10. Log in and open the Linux terminal.
11. Use Linux commands inside the VM.
12. Shut down the VM when finished.

---

# PART A – INSTALLING UBUNTU USING ORACLE VIRTUALBOX

## 4. Downloading and Installing VirtualBox

### 4.1 Download the required files

- Download the Ubuntu ISO image from the Ubuntu website.
- Download Oracle VirtualBox from `virtualbox.org`.
- Since Windows is the host operating system, select the **Windows host** installer.

### 4.2 Install VirtualBox

1. Locate the downloaded VirtualBox installer.
2. Right-click the installer.
3. Choose **Run as administrator**.
4. If Windows displays an alert, review it and proceed only if you trust the installer.
5. Complete the installation.
6. A VirtualBox icon/shortcut is created.
7. Open **Oracle VM VirtualBox Manager**.

---

## 5. Creating a New Virtual Machine in VirtualBox

### Step 1: Start VM creation

- Open VirtualBox Manager.
- Click **New**.
- Enter a name for the VM.
- In the demonstration, the name is `Ubuntu 20.04`.

### Step 2: Allocate memory (RAM)

- Assign RAM to the virtual machine.
- The demonstration allocates **2048 MB (2 GB)**.
- The amount allocated to the VM is reserved for its use while it runs, so consider the RAM available on the host.

### Step 3: Create a virtual hard disk

- Create a virtual hard disk for the Linux installation.
- The lecture mentions 10 GB as an initial suggested size.
- In the demonstration, the size is increased to **20 GB**.

### Step 4: Attach the Ubuntu ISO

1. Open the VM's **Settings**.
2. Go to **Storage**.
3. Select the optical/IDE drive.
4. Add a CD/DVD image.
5. Choose the downloaded Ubuntu ISO file.
6. Confirm that the ISO is attached.

The ISO acts as the installation medium from which the VM boots.

---

## 6. Installing Ubuntu Inside VirtualBox

Once the VM is configured:

1. Start/power on the VM.
2. The VM opens in a window on the Windows desktop.
3. It boots from the attached Ubuntu installation medium.
4. The installation medium is checked.
5. The Ubuntu installer appears.

### Installation choices shown in the lecture

1. Select **Install Ubuntu**.
2. Choose the language (English is selected in the demonstration).
3. Select **Normal installation**.
4. The demonstration skips downloading updates during installation to make the process finish sooner.
5. Select the option to erase the disk and install Ubuntu.

### Important warning about disk erasure

The lecture explains that the erase operation applies to the **virtual disk created for the VM**, not the physical hard disk containing the Windows host installation.

Be certain that you are working with the VM's virtual disk and not a real disk belonging to the host computer.

### Finish the installation

1. Confirm the installation.
2. Choose the time zone (India is selected in the demonstration).
3. Create the first user account.
4. Set a password for the account.
5. Keep the credentials safe so that you do not forget them.
6. Wait while Ubuntu installs and writes data to the virtual disk.
7. When installation finishes, restart the virtual machine.
8. Log in using the password created during installation.
9. Complete or skip the initial welcome settings as appropriate.
10. Open the terminal.

### Installation activity indicators

During installation, the lecture points out activity indicators:

- Disk activity may be shown while data is being written to the virtual disk.
- Network activity may be shown when network operations are taking place.

The installation can take a few minutes, depending on the computer.

---

## 7. Verifying and Using Ubuntu in VirtualBox

After logging in:

- Open the terminal application.
- The demonstration shows Ubuntu 20.04 LTS running with kernel version **5.11**.
- Linux is now running as a guest operating system inside Windows.

### VM lifecycle

The normal usage cycle is:

1. Open VirtualBox Manager.
2. Start the Ubuntu VM.
3. Log in to Ubuntu.
4. Open the terminal.
5. Practice Linux commands.
6. Shut down Ubuntu when finished.
7. Return to VirtualBox Manager.

You can repeat this cycle whenever you need the Linux environment.

### Changing VM settings

After shutting down the VM, VirtualBox Manager lets you change its settings. The lecture demonstrates or mentions:

- Allocating more memory (RAM).
- Deciding which additional devices should be attached.
- Keeping only the hard disk attached if that is sufficient for the work.
- Increasing display memory if needed.
- Adjusting the VM window size.

**Key point:** The Windows host operating system is not replaced by the VM. You can start and stop the Linux environment when needed.

---

# PART B – INSTALLING UBUNTU USING VMWARE WORKSTATION PLAYER

## 8. Installing VMware Workstation Player

The lecture demonstrates a second hypervisor option.

### Steps

1. Download VMware Workstation Player for Windows.
2. Locate the installer.
3. Right-click it and choose **Run as administrator**.
4. Review the Windows alert and proceed if the installer is trusted.
5. Accept the license agreement.
6. Continue with the standard installation options.
7. Wait for installation to finish.
8. Launch VMware Workstation Player from its desktop shortcut.
9. In the demonstration, the software is selected for non-commercial use.

The lecture uses **VMware Workstation Player version 16** in its demonstration.

---

## 9. Creating a VM in VMware Workstation Player

1. Launch VMware Workstation Player.
2. Choose **Create a New Virtual Machine**.
3. Select the installer disc/image option.
4. Browse to the Ubuntu ISO file, which is already available in the Downloads folder in the demonstration.
5. Continue with the VM setup.
6. Enter the first user's credentials.
7. Choose the virtual disk size.
8. The demonstration allocates **20 GB**.
9. The lecture leaves the option to store the virtual disk as multiple files at its default setting.
10. Finish creating the VM.

### User credentials

- The first account is created as part of the setup.
- Remember the username and password because they are needed to log in to the installed operating system.

---

## 10. Installing and Starting Ubuntu in VMware

1. Start the newly created virtual machine.
2. VMware connects the VM to the Ubuntu ISO.
3. The VM boots from the installation medium.
4. The installer checks the installation medium.
5. Ubuntu begins installing to the virtual disk.
6. The lecture shows installation progress and background text output.
7. The installer may check for updates and download packages.
8. The bootloader is installed as part of the process shown.
9. Wait until installation completes.
10. The VM restarts.
11. Log in using the credentials created during setup.
12. Find and open the Terminal application.
13. The lecture suggests adding Terminal to Favorites for easier access.

At this point, Ubuntu 20.04 is running as a guest operating system on the Windows host through VMware Workstation Player.

### When finished

- Close or shut down the guest operating system when the work is complete.
- The lecture also mentions moving important content to another location for safety.
- The VM can be started again later to continue practicing.

---

## 11. VirtualBox vs VMware Workstation Player

Both tools are used in the lecture to run Ubuntu on Windows.

| VirtualBox | VMware Workstation Player |
|---|---|
| Download the Windows host installer. | Download the Windows version. |
| Create a VM using **New**. | Create a VM using **Create a New Virtual Machine**. |
| Configure RAM and virtual disk. | Configure the virtual disk and user details through the wizard. |
| Attach the Ubuntu ISO through Storage settings. | Select the Ubuntu ISO as the installer image. |
| Start the VM and install Ubuntu. | Start the VM and install Ubuntu. |
| Change VM settings through VirtualBox Manager. | Manage and launch the VM through VMware Workstation Player. |

**Common concept:** Both use a hypervisor and a Linux ISO to install a guest operating system inside a virtual machine.

---

# PART C – WINDOWS SUBSYSTEM FOR LINUX (WSL)

## 12. What Is WSL?

**Windows Subsystem for Linux (WSL)** provides a way to run a Linux environment on Windows.

The lecture presents WSL as another way to get a Linux command-line environment without using the VirtualBox or VMware VM setup demonstrated earlier.

### Why use WSL?

- It provides access to a Linux command-line environment from Windows.
- It is supported by Microsoft.
- It can be used to practice Linux commands and shell scripting.
- It gives another option when you do not want to set up a traditional VM.

---

## 13. Installing WSL

The lecture demonstrates the following process:

1. Search for **Windows Subsystem for Linux**.
2. Open the Microsoft website/documentation.
3. Open **PowerShell as Administrator**.
4. Run the installation command:

```powershell
wsl --install
```

5. Allow the installation process to complete.
6. Restart the computer if requested.
7. Continue with the Ubuntu subsystem installation.
8. Create the Linux user account when prompted.
9. Set and safely retain the password.
10. Open WSL to access the Linux terminal.

### Important command

```powershell
wsl --install
```

This is the command shown in the lecture to install WSL.

### Checking the environment

The lecture checks the kernel version after installation and shows kernel version **5.10** in its demonstration.

### User account

- WSL asks you to create a Linux user.
- Keep the credentials safe.
- The lecture describes this account as having administrative ability to install utilities in the subsystem.

---

## 14. Opening and Using WSL

1. Open the WSL/Ubuntu application from Windows.
2. A terminal window appears.
3. You can now practice Linux commands in that environment.

The lecture demonstrates that WSL and a VM can both be running on the same Windows computer.

### Two environments at the same time

The demonstration shows:

- Ubuntu running inside VMware Workstation Player.
- A separate Linux terminal running through WSL.

These are two distinct Linux command-line environments available on top of Windows.

---

# PART D – CLOUD-BASED LINUX TERMINALS

## 15. Why Use a Cloud-Based Environment?

The lecture also suggests using a cloud environment to practice command-line exercises.

This can be useful when:

- You do not want to install a Linux environment locally.
- You want to access a terminal through a browser.
- You want to save scripts and return to them later.
- You want a convenient environment for course exercises and shell scripting.

Two services demonstrated are:

1. Replit
2. CoCalc

---

## 16. Using Replit

### 16.1 Sign in

- Open `replit.com`.
- Sign up for an account or log in.
- The lecture mentions Google, Facebook and GitHub as sign-in options.

### 16.2 Create a project

1. Open the Replit dashboard.
2. Create a new project.
3. Enter a project name.
4. Select **Bash** as the project type.
5. The demonstration names the project `Bsc demo`.

### 16.3 Open the shell

1. Wait for the project to launch.
2. Expand the terminal area.
3. Select the **Shell** tab.
4. A shell environment is available in the browser.

### 16.4 Understand the environment

The lecture demonstrates:

- Kernel version: **5.11**.
- Home directory: `/home/runner`.
- The created project is stored under the cloud user's home directory.

Files and scripts created in the project folder can be revisited later for further editing and practice.

### 16.5 Exit

- Use the available logout option to leave the environment.

---

## 17. Using CoCalc

The lecture also demonstrates `cocalc.com` as a browser-based environment for command-line practice and Bash scripting.

### 17.1 Sign in

The lecture lists these sign-in options:

- Facebook
- GitHub
- Google
- Twitter
- Creating a separate account

The demonstration signs in using a Google account.

### 17.2 Create a project

1. Open the CoCalc dashboard.
2. Create a new project.
3. Give the project a name.
4. The demonstration uses `command line practice`.
5. Create the project.

### 17.3 Start a terminal environment

1. Open the project.
2. Start the project if it is not already running.
3. Create a terminal environment.
4. Give the terminal a name.
5. The demonstration uses `cmd practice`.
6. Open the terminal/shell.

### 17.4 Understand the environment

The lecture shows:

- Home directory: `/home/user`.
- Kernel version: **5.11**.
- Several mount points are present.
- Files created in the project folder remain available when you return to the project.

### 17.5 Stop and close the project

When finished:

1. Close the terminal environment.
2. Stop the running project.
3. Log out.
4. The project remains on the dashboard and can be opened again later.
5. The lecture notes that a paid license may be needed if you want the environment to run faster.

---

## 18. Replit vs CoCalc

| Replit | CoCalc |
|---|---|
| Create a Bash project. | Create a project and then a terminal environment. |
| Open the Shell tab. | Start the project and open a terminal. |
| Demonstration home directory: `/home/runner`. | Demonstration home directory: `/home/user`. |
| Demonstration kernel: 5.11. | Demonstration kernel: 5.11. |
| Project files can be revisited. | Project files can be revisited. |
| Log out when finished. | Close the environment, stop the project and log out. |

---

# PART E – USING A MOBILE PHONE

## 19. Running a Command-Line Environment on Android

The lecture demonstrates using a mobile terminal app to practice command-line operations.

### App mentioned

- **Termux** (the transcript's speech-to-text rendering contains variations of the app name).
- The lecture attributes the app to Fredrik Fornwall.
- It demonstrates installing the app through the Google Play Store as it existed at the time of recording.

### Steps shown

1. Open the Google Play Store.
2. Search for Termux.
3. Find the app attributed in the lecture to Fredrik Fornwall.
4. Install the app.
5. Open it.
6. Use the on-screen keyboard to enter terminal commands.

### Environment details shown

- The home directory is inside the Termux environment.
- The demonstration reports kernel version **4.14**.
- The environment uses Bash.
- Several mount points are visible.
- The lecture notes that phone storage can also be used.

**Key point:** A mobile terminal can provide a small command-line environment for basic practice.

---

# PART F – COMPARISON AND REVISION

## 20. All Linux Practice Options Covered in the Lecture

| Option | Where it runs | Main idea |
|---|---|---|
| VirtualBox | On Windows as a hypervisor | Runs Ubuntu in a VM window. |
| VMware Workstation Player | On Windows as a hypervisor | Runs Ubuntu in a VM window. |
| WSL | Integrated with Windows | Provides a Linux environment and terminal on Windows. |
| Replit | In a web browser | Provides a cloud-based Bash project and shell. |
| CoCalc | In a web browser | Provides cloud projects and terminal environments. |
| Termux | On an Android phone | Provides a small terminal environment on mobile. |

### Which option should you choose?

Based on the options presented in the lecture:

- **VirtualBox or VMware:** Choose one if you want to practice using Ubuntu as a separate guest operating system.
- **WSL:** Choose it if you want a Linux command-line environment available directly from Windows.
- **Replit or CoCalc:** Choose one if you prefer browser-based command-line practice.
- **Termux:** Choose it if you want to experiment with a terminal on your phone.

The lecture's overall goal is to make sure learners have access to a Linux command-line environment for the course.

---

## 21. Important Values and Commands to Remember

### Values used in the demonstrations

| Item | Value shown in the lecture |
|---|---|
| Ubuntu version | Ubuntu 20.04 LTS |
| ISO architecture | `x86_64` |
| ISO size (at recording time) | Approximately 3 GB |
| Suggested VM disk space | About 20 GB |
| VirtualBox demonstration RAM | 2048 MB (2 GB) |
| VirtualBox demonstration disk | 20 GB |
| VMware demonstration disk | 20 GB |
| VirtualBox Ubuntu kernel shown | 5.11 |
| WSL kernel shown | 5.10 |
| Replit kernel shown | 5.11 |
| CoCalc kernel shown | 5.11 |
| Termux kernel shown | 4.14 |

### Important command

Run this in an elevated Windows PowerShell:

```powershell
wsl --install
```

---

## 22. Practical Checklist

Use this checklist to verify that you can access a Linux command-line environment.

- [ ] Choose a method: VM, WSL, cloud terminal or mobile terminal.
- [ ] If using a VM, download a Linux ISO.
- [ ] If using a VM, install VirtualBox or VMware.
- [ ] Create the VM.
- [ ] Allocate RAM and virtual disk space.
- [ ] Attach the ISO image.
- [ ] Install Ubuntu.
- [ ] Create and retain your Linux login credentials.
- [ ] Log in successfully.
- [ ] Open the terminal.
- [ ] Run basic Linux commands.
- [ ] Shut down or stop the environment safely when finished.

---

## 23. Final Takeaways

1. A virtual machine allows Linux to run on top of an existing operating system such as Windows.
2. A VM requires a Linux ISO, a hypervisor, disk space and RAM.
3. VirtualBox and VMware Workstation Player are the two VM tools demonstrated.
4. The VM's virtual disk is separate from the host computer's physical disk.
5. Ubuntu installation involves booting from the ISO, installing to the virtual disk and creating a user account.
6. After installation, open the Ubuntu terminal to practice Linux commands.
7. WSL is another way to access a Linux environment from Windows.
8. The lecture uses `wsl --install` in an administrator PowerShell.
9. Replit and CoCalc provide browser-based environments for shell practice.
10. Termux provides a small terminal environment on Android.
11. The learner can choose the environment that best suits their system and practice needs.
12. The objective is to have a working Linux command-line environment for the rest of the course.

---

## 24. Quick One-Minute Revision

- **VM:** Runs a guest operating system on top of a host operating system.
- **ISO:** Installation image used to boot and install Linux.
- **Hypervisor:** Software used to create and run VMs.
- **VirtualBox / VMware:** Hypervisors demonstrated in the lecture.
- **Virtual disk:** Disk allocated to the VM; distinct from the host's physical disk.
- **WSL:** Linux environment available on Windows.
- **Replit / CoCalc:** Browser-based command-line practice environments.
- **Termux:** Mobile terminal environment.
- **WSL installation command:** `wsl --install`.

**End of Lecture 1 – Launching a Linux Virtual Machine.**
