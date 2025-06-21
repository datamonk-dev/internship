# Some Guidelines for doing this course
This Course is designed by practitioners who use this tools everyday on the job. Everyone of the employee who joins Datamonk, has linux installed on their machine. 

- This course is NOT only to be read, but practiced as the learner go through different chapters. They are expected to run the commands on the terminal, explore the concepts on the system. 
- This is not to be read linearly. The student can go on a brief excursion to try something out, if they want.
- The student should cultivate the "why mindset". They should ask "why" question whenever something new comes up in the course. They should maintain the questions in a notebook/pad as they go through the course. More questions they have in the chapter, Better will they learn and contribute to the project down the line. 

- The idea is to transition from "rote memorization" to "hands-on learning". The goal is to get to a level where you will feel comfortable approaching any new problem with confidence. To facilitate that we will also have projects intermingled with the lesson content wherever necessary. 

## Why Linux ?
We get asked a lot of questions on why installing linux is important. Here are a few reasons why this is very important. 
- Linux will save you time: Local first approach to learning: Our material and internship require that you install and run Free and open source software locally. Installing anything on windows is very difficult. Even though, it may take days to install the linux in dual boot mode, it will save months of time later on when you start working on the project. 

- Developer tools not available on windows: No good package manager to install dependencies. Limited editors available on windows. Limited support of programming languages outside most popular languages. New tooling even in python don't support windows. 

- Poor support for bash utilities on windows: Tools like find, grep are not available on windows.

- Using linux on your personal machine will build a solid foundation for your career in software development. 99% of the web servers use linux including Microsoft's servers. So, running linux will give you a solid foundation. 

- No git on windows: git is the standard for development. Unfortunately, it's not available in Command Line. It's available in powershell, but haven't been as battle tested. 



## Why not virtual machines ?
Virtual machines are slow. Running full-stack application or data intensive applications or things like docker will grind it to halt. Changing your setup in the middle of the course will be very difficult. 

## Why not WSL ?
WSL is good for some quick experimentation. But, for full blown projects, It can be problematic.

- Underpowered: On underpowered Devices (< i7 or <16 GB), less resources will be available to WSL making it slow specially for data intensive tasks 

- Networking can be tricky: Running backend in WSL and frontend in a browser requires a network bridge brtween host machine and WSL. If not configured properly, you will end wasting days to get a simple web server up and running. 

- No hardware acceleration: For ML or graphical intensive applications, accessing GPU can be tricky. 

- Slow containerization: Docker is the industry standard for deploying web application. running docker inside wsl will be painfully slow for large images. 

- Slows down the learning: As a developer, you are required to be hands-on with Linux. If you don't use linux daily, this will slow down your learning and growth as a software developer. 



