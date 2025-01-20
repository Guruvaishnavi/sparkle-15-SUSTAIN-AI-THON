## Mental health monitoring AI
This project is about implementing a pet AI which understands the human feelings and emotions by their own and gives suggestions and relaxing messages based on our data.
## Brief Intro
Developing a mental health monitoring system integrated with AI. It is a virtual pet AI which tracks and monitors the user's daily activities like eating food, water monitoring, step count, sleep monitoring etc. It will analyse the user's actions and emotions by interacting with the user's emotional state.
## Workflow diagram
<ul>
<li>FIGMA - frontend</li>
<li>Data sets </li>
<li>NLP</li>

## App features
<ul>
<li>Emotional Tracking and Analysis</li>
<li>Personalized Feedback and Support</li>
<li>Activity and Routine Monitoring</li>
<li>Health Monitoring</li>
<li>Social Interaction Insights</li>
<li> Productivity and Time Management Support</li>
<li> Daily Reflection and Goal Setting</li>
<li> Mindfulness and Relaxation Exercises</li>
<li> Personalized Pet Interactions</li> 
<li>Customizable User Experience</li> 
</ul>

## Novelty

## Work flow 
<li>1. Front-End Development</li>
<ul>
  <li>UI Design:Figma or Adobe XD (for design and prototyping)</li>
<li>HTML</li>
<li>CSS</li>
<li>JavaScript</li>
</li>
  </ul>
<li>2. Back-End Development</li>
<ul>
  <li>Django/Flask (Python frameworks)</li>
  </ul>
<li>3. Voice and Text Interaction</li>
<ul>
  <li>TensorFlow or PyTorch </li>
  </ul>
<li>4.Code Editor</li>
<ul>
<li>
  Visual Studio Code (VS Code)
</li>
                   

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
