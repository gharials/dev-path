# Operating System Basics

A computer consists of these fundamental components: CPUs or processors, memory (aka RAM), and storage (aka disk). Besides these a computer may have many other peripheral devices. An operating system controls and coordinates all _resources_ (e.g. processor, memory, disk, devices, etc.) of a computer. It also controls all programs (_processes_ in OS terminology) running on a computer.

## Command line interfaces (CLIs)

The early operating systems used to have only command line interfaces: users had to perform all tasks by typing in commands. It was inconvenient for many reasons. All modern OSs are graphical user interface (GUI) based. It may sound strange at first, however, the old command line interfaces (CLI) have some benefits too. That is why the modern OSs provide command line interfaces besides the graphical interface. The window where users input commands is called a _terminal._

Many operations usually done from GUI has CLI equivalents too. For example, we usually download files through a browser, but it can done from CLI too. The following command downloads the `install.sh` file from the specified URL: `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh`

### Benefits of CLI

CLIs are particularly helpful when you want to automate a _batch of tasks_ (that is a number of tasks to be executed one after another). Say, you want to download and install a few programs one after another. In such situations in a graphical interface, you have to be in front of the computer during the entire process. But if all the download and install commands were written down in a script, as is done in this [example](https://gist.github.com/brettjrea/e566a998d102ea2c2b8220c9c585e438), the commands would execute one after another on their own until they are finished.

### CLIs provided by various OSs

The Windows operating system provides two CLIs: the _Command Prompt_ (the old one) and _Power Shell_ (the new and more capable one). Search for command prompt and power shell from start menu if you want to run them. The Linux OSs provide the _Shell_ CLI and its derivative _Bash_.

Commands vary from CLI to CLI: the same command may work on one but not on the other. The `ls` command, for example, is available in Power Shell but not in Command Prompt.

???+ info
    **Windows Subsystem for Linux (WSL)**

    Linux Shell is the de-facto standard for CLIs, much convenient and more widely used than Windows Command Prompt and Power Shell. Lately, the [Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/en-us/windows/wsl/about) feature in Windows enables running Linux commands from Windows OS. WSL is effectively a Linux OS without GUI within the Windows OS. You can run Linux commands by running WSL on Windows.
    
    Getting handy with Linux commands is a big plus for any developer, even if you are a Windows user. See this [video](https://youtu.be/gd7BXuUQ91w?si=wF0gyBJdxJo0IZpV) for an overview of the most frequently used Linux commands.

## 32-bit and 64-bit OS

Often when you want to download an application, you find that two versions (_builds_) are available: 32-bit and 64-bit (for example, the FileZilla FTP client: [64-bit](https://filezilla-project.org/download.php) and [32-bit](https://filezilla-project.org/download.php?platform=win32)). The two builds provide the same functionality, but they differ on the _type of CPU_ they are targeted for.

CPUs fetch a small amount of data at a time, required for executing only one instruction, from a much larger memory. The fetching happens with _memory addresses_; each memory location has its address, which is a number. Now, 64-bit CPUs use 64-bit wide addresses, therefore can access a larger memory space (2<sup>64</sup> bits, that is 17,179,869,184 GB) than a 32-bit one can (2<sup>32</sup> bits, that is 4 GB). Just like cell phone numbers, more digits mean more phones. In summary, 64-bit CPUs are more capable than the 32-bit ones: a 32-bit CPU cannot use a memory larger than 4 GB even if it is available.

Operating systems are targeted according to CPU types: there are 64-bit OSs and 32-bit OSs as well. These days, most CPUs and OSs are 64-bit, and as a result, many applications don't provide a 32-bit build at all (like [Postman](https://www.postman.com/downloads/)).

For further details, consult this resource: [Difference Between 32-bit and 64-bit Operating Systems.](https://www.geeksforgeeks.org/32-bit-vs-64-bit-operating-systems/)
