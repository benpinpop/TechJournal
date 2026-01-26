# Module 2: Intro to VMs/Kali

Lecture Slides: [Presentation](https://docs.google.com/presentation/d/1HUuHtDBeXX5UtGbsvw9fqGOSnfLkkZ7l-QBUa7ESJow/edit?slide=id.g33ae9e42749_1_17#slide=id.g33ae9e42749_1_17)

### Vocabulary & Key Terms

Define important terms and acronyms related to the topic of the module.

#### Virtual Machine (VM)

* A digital replica of an operating system.

#### Hypervisor

* Software that allows you to create and run multiple VMs.

#### Operating System (OS)

* The Operating System is the primary application running your computer, managing all software, hardware, processes, and memory.

#### &#x20;Graphical User Interface (GUI)

* A graphical user interface is a visual interface that you can interact with, allowing you to press buttons to open processes.

#### &#x20;Command Line Interface (CLI)

* A command-line interface allows you to type in commands to execute processes. It provides you with the same functionality as a GUI, but at a lower and more direct level.

#### &#x20;Linux

* A free, open-source operating system alternative to Windows with a much more useful terminal. (From personal experience)

#### Linux Distribution

* A version of Linux that another user has modified to contain more (or fewer) features based on specific needs.

#### Scripting

* Scripting is the process of writing code that the computer can execute automatically. This is used to automate any tasks that would be too verbose to write normally

#### Bash

* Bash is the native scripting language for Linux, allowing you to run code in the terminal without typing it out yourself.

### Main Ideas and Takeaways

Bullet points for notes that aren’t definitions, but explain how things work or why things are important. Feel free to bold/highlight the most important information.

* Scripting is extremely important for automation because you don’t want to hand-type everything.
* There are a variety of scripting languages, from high to low level, with a variety of use cases.&#x20;
* Linux and its distributions are extremely versatile, allowing you to perform a variety of tasks like server hosting, hacking, etc.

### Diagrams and Visuals

Include images from the slides or from the internet that are useful and/or good references.

![](<../../.gitbook/assets/unknown (12).png>)

![](<../../.gitbook/assets/unknown (13).png>)

\
\
<br>

### Commands, Tools, or Techniques

Particularly from activities or labs, it can be helpful to document the steps or tools used. Include useful links (ex., manual pages for commands).

* pwd - Prints working directory
  * pwd → “home/benp”
* mkdir - Makes a directory
  * mkdir testdirectory
* cd - Changes the directory
  * cd home&#x20;
* ls - Displays all files and subdirectories in the directory
* clear - Clears the terminal screen
* touch - Creates a text file
* mv - Moves a file to a designated directory
  * mv 123.txt home/desktop
* cp - Copies a file to a new location
  * cp 123.txt 456.txt
* rm - Deletes a file or directory
  * rm -rf / (hehe)
* whoami - Tells you what user you’re logged in as
* cat - Prints out specified arguments
  * cat file.txt → “This is the file text!”
* sudo - Runs a command as administrator
  * sudo rm -rf /
* chmod - Modifies a file's permission set
  * sudo chmod +x [name-of-script.sh](http://name-of-script.sh)
* nano - Opens a text editor
* ./filename - runs a file
* useradd - Creates a new user
  * useradd -m username
* passwd - Modifies a password for a user, or changes your current password (if not root)
  * passwd user
* man - Allows you to access the manual and see command information
  * man passwd → Opens the manual page for the passwd command.<br>

\
\
<br>
