Виконала самостійно Слобожан Софія РПЗ-23А

 **Лабораторна робота №4**
**Тема: “Команди Linux для управління процесами”**

**Мета роботи:**
Отримання практичних навиків роботи з командною оболонкою Bash.
Знайомство з базовими командами для управління процесами.

**Матеріальне забезпечення занять:**
1. ЕОМ типу IBM PC.
2. ОС сімейства Windows та віртуальна машина Virtual Box (Oracle).
3. ОС GNU/Linux (будь-який дистрибутив).
4. Сайт мережевої академії Cisco netacad.com та його онлайн курси по Linux
**Оформлення звіту:**
Титульний аркуш
Тема та мета роботи
Завдання попередньої підготовки
Основні позиції ходу роботи
Відповіді на контрольні запитання
Висновки за результатами роботи (обов’язково!!!)

### Answers to Questions

#### 2.1. What commands do you know for monitoring the state of processes? How can you view their possible parameters?
- **Commands for monitoring process states:**
  - **`top`**: Displays active processes in real-time, updating information every few seconds.
  - **`htop`**: An enhanced version of `top` with a graphical interface, allowing scrolling through the list of processes and providing more management options.
  - **`ps`**: Shows a list of processes currently running in the system. Various options can be used to obtain detailed information.
  - **`pgrep`**: Searches for processes by name or other criteria.
  - **`pstree`**: Displays a tree of processes, showing the hierarchy of parent and child processes.

- **Viewing possible parameters:**
  - To get information about command parameters, you can use the `man` command, for example:
	- `man ps` to view documentation for `ps`.
	- `man top` to view documentation for `top`.
	- `man htop` to view documentation for `htop`.

#### 2.2. Can the `ps` command track the state of processes in real-time?
- No, the `ps` command cannot track the state of processes in real-time. It provides a snapshot of the state of processes at the moment the command is executed. For real-time monitoring, you should use `top` or `htop`, which continuously update information about processes.

#### 2.3. By which parameters can processes be sorted in the `top` command? How can you switch between them?
- In the `top` command, processes can be sorted by various parameters, such as:
  - **%CPU**: Percentage of CPU usage.
  - **%MEM**: Percentage of memory usage.
  - **TIME+**: Total CPU time spent on the process.
  - **PID**: Process ID.
  - **USER**: The user who started the process.

- **Switching between parameters:**
  - To change the sorting parameter in `top`, press `Shift` + `F` to open the sorting menu. Use the arrow keys to select the parameter you want to sort by, and press `Enter` to confirm your choice.

#### 2.4. What commands do you know for terminating processes?
- **Commands for terminating processes:**
  - **`kill <PID>`**: Terminates the process by its unique identifier (PID).
  - **`killall <process_name>`**: Terminates all processes with the specified name.
  - **`pkill <pattern>`**: Terminates processes that match the given pattern (partial names can be used).
  - **`xkill`**: Allows you to close graphical windows by clicking on them (used in graphical environments).
  - **`fuser -k <file>`**: Terminates all processes using the specified file.
### Work Procedure

**Initial Work in CLI Mode in Linux OS:**
1. Start the Linux Ubuntu operating system. Log in and open the terminal (if you are performing the lab work in room 401).
2. Launch the Ubuntu_PC virtual machine (if you are completing the lab tasks through the NetAcad academy).
3. Start your Linux operating system (if you are working on your own PC and have it installed) and open the terminal.

### Questions and Answers

1. **How to display the contents of the /proc directory? Where is it located and what is its purpose? Describe the information contained within it.**
   - To display the contents of the `/proc` directory, use the command:
 	```bash
 	ls /proc
 	```
   - The `/proc` directory is a virtual filesystem located in the root directory of the Linux filesystem. It provides a mechanism for the kernel to communicate with user space. It contains information about system processes, kernel parameters, and system information.
   - The contents include:
 	- **Process directories**: Each process has a directory named by its PID (Process ID), containing information about the process (e.g., memory usage, status).
 	- **System information files**: Files like `cpuinfo`, `meminfo`, and `version` provide details about the CPU, memory, and kernel version.

2. **How to display information about current user sessions? Which command can be used for this?**
   - To display information about current user sessions, you can use the command:
 	```bash
 	who
 	```
   - Alternatively, the command `w` can also be used to show who is logged in and what they are doing.

3. **What actions can be performed in the terminal using the combinations Ctrl + C, Ctrl + D, and Ctrl + Z?**
   - **Ctrl + C**: Terminates the currently running foreground process.
   - **Ctrl + D**: Sends an EOF (End of File) signal, which can be used to exit the terminal or end input for commands that read from standard input.
   - **Ctrl + Z**: Suspends the currently running foreground process and puts it in the background.

4. **What is the difference between a background process and a foreground process? Where are they used?**
   - A **foreground process** runs in the terminal and can interact with the user, while a **background process** runs without user interaction and does not occupy the terminal.
   - Background processes are used for tasks that do not require immediate user input, allowing users to continue using the terminal for other commands.

5. **Describe the following commands and explain what they do: jobs, bg, fg.**
   - **`jobs`**: Lists all background and suspended jobs in the current terminal session, showing their job numbers and statuses.
   - **`bg`**: Resumes a suspended job in the background, allowing it to continue running without occupying the terminal.
   - **`fg`**: Brings a background job to the foreground, allowing it to interact with the user.

6. **Which command can be used to view information about running background processes and tasks?**
   - The command `jobs` can be used to view information about running background processes and tasks in the current terminal session.

7. **How to suspend a background process, how to resume it, and how to restart it if necessary?**
   - To suspend a background process, you can use:
 	```bash
 	kill -STOP <PID>
 	```
   - To resume it in the foreground, use:
 	```bash
 	fg %<job_number>
 	```
   - To resume it in the background, use:
 	```bash
 	bg %<job_number>
 	```
   - If you need to restart a suspended process, you can use the `fg` or `bg` commands as needed.

8. **Run the terminal and execute the following actions to familiarize yourself with process management:**
   - Start the `top` command to analyze the results and describe the most active processes in the system.
   - To suspend the `top` command, use the keyboard combination `Ctrl + C`.
   - Display information about processes using the `ps` command:
 	```bash
 	ps aux
 	```

9. **Provide 5 examples using different parameters of the `ps` command (e.g., display only system processes, display processes of a specific user, display process tree, etc.). Describe what each parameter does.**
   - **`ps aux`**: Displays all running processes with detailed information (user, PID, CPU and memory usage, etc.).
   - **`ps -u <username>`**: Displays processes for a specific user.
   - **`ps -e --forest`**: Displays all processes in a tree format, showing the parent-child relationship.
   - **`ps -p <PID>`**: Displays information about a specific process identified by its PID.
   - **`ps -l`**: Displays a long format listing of processes, including additional details like priority and state.

10. **Check if you have any running background processes. Which ones?**
	- Use the command:
  	```bash
  	jobs
  	```
	- This will list any background processes currently running in the terminal session.

11. **Resume the execution of a suspended background process first in the foreground, then suspend it again, and finally resume it in the background.**
	- To resume in the foreground:
  	```bash
  	fg %<job_number>
  	```
	- To suspend it again:
  	```bash
  	Ctrl + Z
  	```
	- To resume in the background:
  	```bash
  	bg %<job_number>
  	```

12. **Terminate the background process.**
	- Use the command:
  	```bash
  	kill <PID>
  	```
	- Or if you know the job number:
  	```bash
  	kill %<job_number>
  	```

### Control Questions

1. **What is the purpose of the /proc directory in Linux systems? What information does it store?**
   - The `/proc` directory serves as a virtual filesystem that provides information about running processes, kernel parameters, and system information. It contains files that represent system and process information, such as CPU usage, memory statistics, and process details.

2. **How to dynamically determine which of three processes is currently using the most memory? What percentage of memory does it consume from the total?**
   - You can use the command:
 	```bash
 	ps aux --sort=-%mem | head -n 4
 	```
   - This command sorts processes by memory usage in descending order and displays the top three processes. The output will show the percentage of memory each process is using.

3. **How to obtain the hierarchy of parent processes in Linux systems? Provide its structure and describe it.**
   - You can use the command:
 	```bash
 	pstree
 	```
   - This command displays the process tree, showing the parent-child relationships between processes. The structure typically starts with the `init` or `systemd` process at the top, with other processes branching out below it.

4. **What is the difference between the top and ps commands?**
   - The `top` command provides a dynamic, real-time view of running processes, continuously updating the display. In contrast, the `ps` command provides a static snapshot of processes at the moment it is executed.

5. **What additional features does htop provide compared to top?**
   - `htop` offers a more user-friendly interface with color coding, the ability to scroll through the process list, and interactive process management (e.g., sending signals to processes) without needing to enter their PID.

6. **Describe the components of your mobile OS for monitoring running processes in the system.**
   - Mobile operating systems like Android or iOS have built-in task managers or settings that allow users to view running applications and processes. These components provide information about resource usage and allow users to close applications.

7. **Does your mobile OS support terminal control of process management? Describe how.**
   - Some mobile operating systems, like Android, support terminal emulators that allow users to execute shell commands, including process management commands similar to those in Linux.

8. **Is it possible to install third-party software that allows for process management and monitoring on your mobile phone? Briefly describe them.**
   - Yes, there are third-party applications available for mobile devices, such as "System Monitor" or "Task Manager," which provide users with the ability to view and manage running processes, monitor resource usage, and optimize performance. These apps often offer features like process killing, memory management, and system statistics.

### Conclusion


In this practical work, we explored process management in Linux, focusing on the Ubuntu operating system. We examined the `/proc` directory, which provides real-time information about system processes and hardware. We learned to use commands like `who`, `jobs`, `bg`, and `fg` to manage user sessions and process states. Additionally, we utilized `top` and `ps` to monitor active processes and their resource usage. Overall, this exercise enhanced our understanding of how to effectively control and monitor processes in a Linux environment, which is essential for system administration and performance optimization.

