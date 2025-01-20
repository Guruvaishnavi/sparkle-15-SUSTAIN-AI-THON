## Face-recognition-using-SAMA5D27-WLSOM-EK1
This project is about doing AI Facial recognition using SAMA5D27 WLSOM-EK1 board. This board is ideal for evaluating and prototyping and used for industrial
purpose. This page will guide you to use the board without any issues as we discuss about the major issues that we encountered from the initial stage.

## Components needed
<ul>
<li>SAMA5D27 WLSOM-EK1 Board</li>
<li>SD Card</li>
<li>Card Reader</li>
<li>USB Camera</li>
<li>TTL to USB connector</li>
<li>Jumper wires</li>
<li>Power cable</li>
</ul>
## Booting
The OS that we used is Yocto project or Buildroot. The step-by-step guidance is as follows:

<ul>
<li>Install Balena Etcher software</li>
<p align=center>
<img src="balena etcher.PNG" width="500" height="300">
</p>
<li>install Yocto Project OS manually</li>
<li>Insert the SD Card reader with the SD Card to the laptop</li>
<li>Open Balena Etcher software and select 'Flash from file option'</li>
<li>Select the Yocto project file that you have dowloaded</li>
<li>Next, select the target USB Port</li>
<li>The file will start to flash automatically</li>
<li>After flashing open a software called Putty</li>
<li>Now connect the board to the laptop through TTL-USB converter, and connnect the power cable to the board</li>
<li>Insert the booted SD Card to the board</li>
<li>set up the putty and click open</li>
<li>A terminal will open, press start button and then the reset button on the board</li>
<li>Your board will start booting</li>
</ul>

Many a times you will face a lot of issues in booting your OS. And moreover you will not have an OS like Windows, instead you will have to work only with a terminal that
is supported with putty software.You are supposed to finish all your work with only the terminal.
You will also face a lot of issues where you get a kernel panic error and your kernel may get killed automatically. When you face such issues clear all the files, format it
from the begining and install the Yocto Project from the first. If you still face the same issue try installing Buildroot OS, it might be comfortable to use buildroot than
using Yocto Project as you won't encounter Kernel panic attack 

## Setting up Putty
<ul>
<li>Install the software</li>
<li>After installation, open the software</li>
<li>You will be directed to a putty configuration window</li>
<li>Enter the host name i.e the port that is used or connected to the board
<li>Set the port number to 115200</li>
<li>Change the connection type to serial connection</li>
<li>In the categorypanel, click serial and change the flow control to none</li>
<li>Finally click the open option and you will be directed to the terminal automatically</li>
</ul>

## Space partitioning for yocto
After setting up Putty, we encountered issues while attempting to install the essential packages in both Yocto & Builtroot environment. The major issues that we enountered
was, "No space left" so we were unable to install any packages due to inefficient storage.  We were using an 8GB SD card and 90% of it was unallocated. Despite, this the
error persisted. Later, we came to know about the partition spacing. In default partition only 500Mb was allotted, so the OS that was installed took all the space and left
the partition with only 63Mb.So then we were supposed to partition the unallocated space and mount it in the OS. 
The steps to be followed to partition the space is as followed: 

<ol>
<li> Open your Ubuntu</li>
<li> Search for "Disk Utility"</li>
<li> Select the SD card</li>
<li> Click on the root partition</li>
<li> Click settings icon and select resize</li>
<li> Enter the required space and click OK</li>
</ol>

Now the unallocated space will be allocated in root partition. This is the case with Yocto Project.to partition the space in Buildroot, you will encounter an error. It is
restricted to extend the root's space in buildroot. So as an alternative you have to create a new
partition and mount it separately. The steps to be folllowed are:

<ol>
<li>Open Ubuntu
<li>open Disk Utility 
<li>click on the sd card
<li>select the new partition
<li>Resize with the required disk space and press ok
</ol>

Be specific with the ubuntu version you use. Because only ubuntu's 18th or 21st version will bw supportive (lts version of ubuntu).
A lot of issues were faced to install few packages. 
The only way to do the installation is by Cross-Compilation, where the installation and dependencies are done in Ubuntu and the same files are transferred to the sd card and
it is booted on the board again. Now we will have all the files needed in the OS, and it an be used in the board.
