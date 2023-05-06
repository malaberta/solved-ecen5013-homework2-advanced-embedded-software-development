Download Link: https://assignmentchef.com/product/solved-ecen5013-homework2-advanced-embedded-software-development
<br>
For this homework, both Canvas and Github online materials need to be submitted. <strong>Turn in a *.pdf for your report to this assignment to Canvas. Please neatly format submissions with your name, date, homework # at the top, and enumerator your answers using headings indicating each problem number. </strong><strong> </strong>

And please format your answers – provide headings to the problems, context with captured data and descriptions for images and screenshots.

<h1>2         Reading &amp; Resources</h1>

These are reading assignments that are good to complete the homework for the week as well as review materials to prepare for the upcoming content in the class.

<ul>

 <li>(MELP) Mastering Embedded Linux Programming (Second Edition) – Simmonds o Chapter 6 – Focus is on Buildroot and Adding your Own Code (Overlay)</li>

 <li>Linux Kernel Development – Love o Chapter 5 – System Calls (all) oChapter 17 – Devices and Modules</li>

 <li>Linux Device Drivers – Corbet (skim/reference) <a href="https://lwn.net/Kernel/LDD3/">https://lwn.net/Kernel/LDD3/</a> o Chapters 1 &amp; 2 Resources:</li>

</ul>

These are useful documents that will assist your work with the Buildroot toolchain and is an accompaniment to the MELP book, above.

<ul>

 <li>Buildroot o Buildroot Practical Labs – <a href="https://bootlin.com/doc/training/buildroot/buildroot-labs.pdf">https://bootlin.com/doc/training/buildroot/buildroot</a><a href="https://bootlin.com/doc/training/buildroot/buildroot-labs.pdf">–</a><a href="https://bootlin.com/doc/training/buildroot/buildroot-labs.pdf">pdf</a> o Buildroot Manual – <a href="https://buildroot.org/downloads/manual/manual.pdf">https://buildroot.org/downloads/manual/manual.pdf</a></li>

</ul>




These sections are not required but may help with doing the homework assignments.

<ul>

 <li>MELP – Chapter 3 – All about Bootloaders</li>

 <li>Ubuntu Linux Boot Procedure: https://wiki.ubuntu.com/Booting</li>

</ul>







<h1>3         Problem Set</h1>

<h2>[Problem 1] Record your Repository</h2>

Provide us a Github link to your repositories. Include a link to the repository on the top of your assignment to turn in.




<h2>[Problem 2 – 20 Pts] Track system calls and library calls with File IO</h2>

Let’ refresh your file operations skills, as this will be important as we move towards implementing a device driver and writing programs that require user interaction. Additionally, you’ll familiarize yourself with and use tools to support your program’s development. Specifically, you’ll use perf, ltrace and strace to collect information on your program that reads and writes to a file on your development host machine. Your goal is to write a program that can:

<ul>

 <li>Print to standard out an interesting string using printf</li>

 <li>Create a file</li>

 <li>Modify the permissions of the file to be read/write</li>

 <li>Open the file (for writing)</li>

 <li>Write a character to the file</li>

 <li>Close the file</li>

 <li>Open the file (in append mode)</li>

 <li>Dynamically allocate an array of memory</li>

 <li>Read an input string from the command line and write to the string to the allocated array</li>

 <li>Write the string to the file</li>

 <li>Flush file output</li>

 <li>Close the file</li>

 <li>Open the file (for reading)</li>

 <li>Read a single character (getc)</li>

 <li>Read a string of characters (gets)</li>

 <li>Close the file</li>

 <li>Free the memory</li>

</ul>

After writing this, run the ltrace and strace command line applications and collect the output of the system calls and library calls that were used to interact with your file. Additionally, use the “perf stat &lt;your program&gt;” command to collect some performance statistics of your program. <strong>Show all 3 outputs (ltrace, strace, perf)  in your report. </strong>

<strong> </strong>

<h2>[Problem 3 – 30 Pts] Setup Buildroot, then build and boot a Beaglebone Green (BBG) Linux image</h2>

In this exercise you’re building an micro SD memory card with everything to boot and run embedded Linux on a BBG. The  images (uBoot, MLO, kernel, rootfs) for the BBG will be built using the Buildroot toolchain with MELP Chapter 6 as your guide.

(<strong><em>Note</em></strong>: We’re moving on from Crosstools-NG to use the Buildroot Linux toolchain/development environment. As you begin, you’ll want to make sure your Ubuntu (host) Linux VM has plenty of disk space (&gt;100 GB). Secondly, over time, as you use install and setup the Buildroot tools, you’ll want to adjust your dev environment (.bashrc, $PATH, $HOME/bin, etc) to access and use Buildroot’s bin, etc.) The process will involve:

<ul>

 <li>Setting up Buildroot along with the corresponding Linux source files (these are different files from your host Linux sources)</li>

 <li>configuring and building Buildroot toolchain</li>

 <li>making/configuring a target BBG Linux configuration (e.g. beaglebone_defconfig) building the Linux image</li>

 <li>burn the image files to your microSD memory card as a bootable file system</li>

 <li>set up your BBG HW</li>

 <li>connect your dev host to BBG using a serial console cable for console interaction – With FTDI/USB serial port cable connected to your host and the other end to the BBG J1 connector (Black wire on cable is pin 1)</li>

</ul>







<ul>

 <li>Download ‘minicom’ or ‘screen’ or ‘gtkterm”  or your favorite term emulator to your host.</li>

 <li>$ sudo screen /dev/ttyUSB0 115200</li>

</ul>

Or

<ul>

 <li>$ sudo apt-get install minicom</li>

 <li>$ sudo minicom /dev/ttyUSB0 115200</li>

</ul>

Or

<ul>

 <li>$ sudo apt-get install gtkterm</li>

 <li>$ sudo gtkterm -s 115200 -p /dev/ttyUSB0</li>

 <li>(Note: If you are using a guest Linux Virtual Machine (VM) for development on your host, there may be some configuration (mapping) needed of the FTDI/USB serial port from your host computer port through to your guest VM environment.)</li>

</ul>




<ul>

 <li>Install the micro SD memory card, and then apply power to the BBG . You may need to interrupt/change to normal BBG manufactured boot sequence to boot your image through the use of BBG buttons or console interaction …</li>

</ul>




<ul>

 <li>Change the BBG login greeting to include your name using make menuconfig and rebuild your image. Burn your new image to the microSD memory card. Congratulations, you’ve just build your own Linux embedded system!</li>

</ul>




Keep in mind the version of tools, kernel, etc of software mentioned in the book are newer now, so you’ll have to be attentive to versions, paths, etc.

We’re not going for any fancy functionality, but are just getting the tools set up, oriented to the location of files, and learning how to burn a micro SD memory card and get it to boot on the BBG. Please to not overwrite the eMMc memory that ships on the BBG <strong>– you should only boot from your micro SD memory card</strong>. (Hint: Maintaining the original manufacturers code on the BBG allows you to boot from the manufacturer’s original image, by removing the micro SD memory card with your image, and see that the BBG is still functional. Good to know when you’re wondering if it’s a problem with your code or the HW!)

Boot your BBG, login to root, and try some commands on the console.

<strong>Report a screen capture of the last 20 lines of console boot sequence, as well as you logging in and executing your favorite commands at the console (e.g. ps -aux, lsmod, ls /). </strong>

<h2>[Problem 4 – 10 Pts] Port Your File IO program to BBG</h2>

Now that you have a cross development environment setup, let’s port your program from Problem 1 to the BBG. The simplest way to do this is to cross-compile your program “out-of-tree” in some project directory outside of the Buildroot directories. (e.g. ~/projects/myProblem4).

Then create an overlay directory inside the Buildroot directory –

(e.g. ~/buildroot/board/beaglebone_rick/root-overlay/usr/bin) and copy your “arm compiled” executable there. Next configure Buildroot (make menuconfig) to add an overlay directory that will deliver your file (add to) the rootfs in next complete image you build and burn to the micro SD memory. This will put your executable in a good location is in the (target) BBG filesystem’s /usr/bin directory.

Additionally, configure Buildroot to build/add to your BBG image the strace, ltrace, and perf executables using “make menuconfig”  to include the correct packages (e.g. for ltrace search for “ltrace” then set symbol: BR2_PACKAGE_LTRACE [=y]).

Remake, burn a new complete micro SD memory card image, install and boot/run your new Linux image.

<strong>From a BBG console command line, run your program and collect the BBG version of ltrace, strace and perf stat  of the interesting stats that you collected from Problem 1. </strong>




<h2>Implement Your Own System Call on BBG</h2>

You are to create your own system call that can sort an array of numbers in kernel mode. This is more for practice of implementing a call than for making something for its utility. This system call needs to support the following features:

<ul>

 <li>A set of input parameters from user space including o Pointer to a buffer (input) o Size of that buffer (entries or bytes) o Pointer to a sorted buffer</li>

 <li>Validation of all input parameters</li>

 <li>Print information to the kernel buffer (log) o Log the input (user space) buffer contents when your syscall enters, exits, the size of the buffer,</li>

</ul>

o Log the output buffer at start/completion of the sort (details provided below)

<ul>

 <li>Your system call needs to allocate dynamic memory to copy data in from user space o The user space array needs to be copied into kernel space presort o The array needs to be copied back to user space post sort.</li>

</ul>




Your syscall should be defined appropriately using the SYSCALL_DEFINE macro given your argument list size. The input buffer should be at least 256 int32_t data items. The buffer needs to be copied into kernel space. Your syscall will need to sort the data in an order from largest to smallest. Once sorted, it needs to pass the sorted data back to the calling user application in a sorted buffer array.




Review the System Call lecture for additional guidance on where to add/how to add your code. In other words, add your syscall code to the kernel image built by Buildroot’s make. Keep in mind, we’re building a Beaglebone (arm-based) image, so some source modifications will be in the Buildroot kernel source directory (e.g. ~/buildroot/output/build/linux-&lt;something&gt;/kernel) while other source code modifications will be in architecture specific directories (e.g.  ~/buildroot/output/build/linux&lt;something&gt;/arch/arm…).




Show that your kernel module works by writing a user space application that calls your system call numerous times. You can randomly generate this buffer of data elements using random() and time(). This application can be built “out-of-tree” from Buildroot but you should use (include) Buildroot Linux directories of source files (i.e. ~/buildroot/output/build/linux-headers-&lt;xxx&gt; and ~/buildroot/output/build/linux-&lt;xxx&gt;” used to compile the BBG kernel.




You should show that:

<ul>

 <li>System call works correctly (all input parameters valid and correct) o Print information showing that the sort worked correctly</li>

</ul>




<ul>

 <li>System call fails (input parameters are not valid and/or correct) o BONUS: All errors should return appropriate error values (defined in errno.h and errnobase.h )</li>

 <li>Bonus: use a sort algorithm with O(nLogn) performance</li>

</ul>




<strong> </strong>

<strong>Your report should include screenshots of example output of your multiple program runs, including both successful and failure cases (annotated with the “use-case” comments), appropriate BBG kernel logs with printk comments noting the use-cases. Report the time it takes to perform your syscall using timestamps from the log files. </strong>

<h2> Create a CRON/Systemd task on BBG</h2>

Write a C-program that uses your system call from problem 5 along with a few other system calls listed below. This program should run every 10 minutes and it should run to completion. Your program should collect the following information using system call APIs and print its output to a file (either write to the file or just redirect the output):

<ul>

 <li>Current Process ID</li>

 <li>Current User ID</li>

 <li>Current date and time</li>

 <li>Output of your system call</li>

</ul>