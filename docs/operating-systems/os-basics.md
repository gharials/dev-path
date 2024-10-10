# Operating System Basics

A computer consists of these fundamental components: CPUs or processors, memory (aka RAM), and storage (aka disk). Besides these a computer may have many other peripheral devices. An operating system controls and coordinates all _resources_ (e.g. processor, memory, disk, devices, etc.) of a computer. It also controls all programs (_processes_ in OS terminology) running on a computer.

## 32-bit and 64-bit OS

Often when you want to download an application, you find that two versions (_builds_) are available: 32-bit and 64-bit (for example, the FileZilla FTP client: [64-bit](https://filezilla-project.org/download.php) and [32-bit](https://filezilla-project.org/download.php?platform=win32)). The two builds provide the same functionality, but they differ on the _type of CPU_ they are targeted for.

CPUs fetch a small amount of data at a time, required for executing only one instruction, from a much larger memory. The fetching happens with _memory addresses_; each memory location has its address, which is a number. Now, 64-bit CPUs use 64-bit wide addresses, therefore can access a larger memory space than a 32-bit one can. Just like cell phone numbers, more digits mean more phones. In summary, 64-bit CPUs are more capable than the 32-bit ones. Operating systems are targeted according to CPU types: there are 64-bit OSs and 32-bit OSs as well. These days, most CPUs and OSs are 64-bit, and as a result, many applications don't provide a 32-bit build at all (like [Postman](https://www.postman.com/downloads/)).

For further details, consult this resource: [Difference Between 32-bit and 64-bit Operating Systems.](https://www.geeksforgeeks.org/32-bit-vs-64-bit-operating-systems/)
