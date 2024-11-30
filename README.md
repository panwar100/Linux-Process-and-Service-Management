# Linux-Process-and-Service-Management
This guide provides essential Linux commands to manage processes, monitor system performance, and work with services.

# Process Management
## View Processes
### ps

Displays active processes running for the current user in the terminal.

![Screenshot from 2024-11-30 22-04-26](https://github.com/user-attachments/assets/db441ab5-2cf5-40e6-a659-8901dc69866b)

**Fields**:
- PID: Process ID.

- TTY: Terminal associated with the process.

- TIME: CPU time consumed by the process.

- CMD: Command used to run the process (e.g., bash, su).

### ps aux

Lists all processes in the system, including system and background tasks.

![Screenshot from 2024-11-30 22-07-20](https://github.com/user-attachments/assets/93a1be46-3e7d-4e32-9d37-e20ea009e9dc)

a: Shows processes of all users.

u: Includes user-related information.

x: Displays processes not attached to a terminal.

![Screenshot from 2024-11-30 22-17-38](https://github.com/user-attachments/assets/26ea5103-81de-4375-946b-5198deeadc36)

**Task Status**:
- S: Sleeping.
- I: Idle.

### ps lax

provides a detailed view of the currently running processes on the system

![Screenshot from 2024-11-30 22-12-02](https://github.com/user-attachments/assets/7f6dfc27-c331-4d82-b926-b52717891a02)

l: This option tells ps to display the processes in "long format". The long format includes additional fields such as priority, parent process ID (PPID), and more.

a: This option shows processes of all users (not just the current user).

x: This option shows processes without a controlling terminal (background processes or daemons).

![Screenshot from 2024-11-30 22-14-52](https://github.com/user-attachments/assets/9258e67e-1723-4892-a277-332585010d18)

## Delay Execution
### `sleep <seconds>`
Pauses the terminal for the specified number of seconds.
Example: sleep 5 pauses for 5 seconds.

![Screenshot from 2024-11-30 22-20-36](https://github.com/user-attachments/assets/ae15ebaa-4101-49a1-a97c-7db89f50ddf5)
![Screenshot from 2024-11-30 22-20-43](https://github.com/user-attachments/assets/4a1b4328-96ee-40cc-8543-7adc34876c65)


## Run in Background
### `sleep <seconds> &`
When combined with the & operator, it runs in the background, allowing the terminal or script to continue with other tasks without waiting for the sleep duration to finish.
Example: sleep 10000 &.

![Screenshot from 2024-11-30 22-31-28](https://github.com/user-attachments/assets/373d8c8b-8725-43b2-a9be-f3294606d98e)

**jobs**:
Lists active jobs in the background.

## Control Foreground and Background Jobs
### fg %<job_number>
Brings a background job to the foreground.

![Screenshot from 2024-11-30 22-34-08](https://github.com/user-attachments/assets/32b4bd04-aa3e-486a-9baf-a63e22ee747e)

**ctrl+z**
Suspends a foreground process.

### bg %<job_number>
Resumes a suspended job in the background.

![Screenshot from 2024-11-30 22-36-00](https://github.com/user-attachments/assets/6e754f31-176f-4af4-bda0-804d3f3094c5)


## Manipulate Background Jobs
### kill -<signal> %<job_number>
Sends a signal to a process to terminate or control it.

![Screenshot from 2024-11-30 22-38-45](https://github.com/user-attachments/assets/3d121a5e-3732-4614-bfdc-534e0104f485)

**Some Signals**:

-15: Terminate gracefully.

![Screenshot from 2024-11-30 22-41-47](https://github.com/user-attachments/assets/b8346557-6cd0-487b-a61f-b94f860f5fbd)

-19: Stop the process.

![Screenshot from 2024-11-30 22-43-20](https://github.com/user-attachments/assets/2d8eb38d-51ae-4283-8e99-b95c3be130bc)

-18: Restart a stopped process.

![Screenshot from 2024-11-30 22-44-25](https://github.com/user-attachments/assets/45f2db40-93c4-4fee-a842-65dde6539409)

-9: Forcefully kill.

![Screenshot from 2024-11-30 22-45-26](https://github.com/user-attachments/assets/c5951fb4-a5f3-463f-9af0-3d7df5ec7435)

-2: Interrupt (Ctrl+C equivalent).

![Screenshot from 2024-11-30 22-47-08](https://github.com/user-attachments/assets/9742526d-e067-405e-8bfa-d8754ffd93e3)

-3: Quit.

![Screenshot from 2024-11-30 22-48-15](https://github.com/user-attachments/assets/6d4ab699-0b6d-4355-9211-0fcbae0a4d69)

killall -9 <command>

Forcefully terminates all processes of the specified command. Example: killall -9 sleep.

![Screenshot from 2024-11-30 22-50-59](https://github.com/user-attachments/assets/0381c18d-04df-44ce-83a0-155e0f239d29)



# System Monitoring
## System Uptime
### uptime

Displays how long the system has been running, along with the load average.

![Screenshot from 2024-11-30 22-59-31](https://github.com/user-attachments/assets/65b2e970-53ba-4e53-9c6a-b3a9a5714098)


**Explanation of Each Component**:

- **22:54:42**:

  - The current system time in 24-hour format.

- **up 1:05**:

  - The system uptime, i.e., how long the system has been running since the last boot.
  - In this case, the system has been running for 1 hour and 5 minutes.

- **2 users**:

  - The number of users currently logged into the system (via terminal or remote sessions).

- **load average: 0.19, 0.39, 0.24**:

  - The system's load averages over the last 1, 5, and 15 minutes.
  - Load average represents the average number of processes that are in the runnable or waiting state.


## Real-Time Task Monitoring
### top
Shows real-time information about running processes, including CPU and memory usage.

![Screenshot from 2024-11-30 23-02-49](https://github.com/user-attachments/assets/01cf986c-9e69-42ae-ac72-76c728aaffab)


### gnome-system-monitor
Graphical interface for monitoring processes and system performance.

![Screenshot from 2024-11-30 23-04-27](https://github.com/user-attachments/assets/a062235a-943f-4dbe-bd3e-d5600f0d7072)

# Managing Services
## Systemctl Commands
Systemctl is a command-line utility in Linux used to interact with and manage the systemd system and service manager. It allows you to control services, manage system states, and configure system settings

![Screenshot from 2024-11-30 23-08-48](https://github.com/user-attachments/assets/0bd85b3c-c4e7-4009-a094-fae153bfb57a)

### systemctl status `<service>`
Displays the status of the service (e.g., httpd,sshd).

![Screenshot from 2024-11-30 23-33-54](https://github.com/user-attachments/assets/7ffb6324-aa73-4c3c-aec2-6a20bedc5093)

**Explanation of Component**:

- **Loaded**: Indicates that the sshd.service file is loaded, meaning the system has successfully located and read the service unit file for the SSH daemon (sshd).
- **/usr/lib/systemd/system/sshd.service**: This is the path to the unit file for the sshd service, which defines how the SSH daemon should be started and managed.
- **enabled**: This means that the SSH service is set to start automatically when the system boots.
- **preset: ena**: Indicates that the service has been enabled by default according to the system's preset configuration.
- **Active**: The service is currently running. In this case, SSH is actively serving connections.
- **active (running)**: This means that the SSH service is actively running without any issues.
- **since Sat 2024-11-30 21:49:43 IST**: This is the timestamp of when the SSH service was started.
- **1h 42min ago**: This indicates that the SSH service has been running for 1 hour and 42 minutes since it was started.

### systemctl stop/start `<service>`
Stops or starts the service.

![Screenshot from 2024-12-01 00-02-33](https://github.com/user-attachments/assets/ae1350c3-3d4e-4c27-9221-ced61fe65c1f)

![Screenshot from 2024-12-01 00-03-42](https://github.com/user-attachments/assets/18a6c621-7619-473d-80f5-7ed1cb1e1910)

### systemctl enable/disable `<service>`
Configures the service to start automatically on boot or not.

![Screenshot from 2024-12-01 00-06-11](https://github.com/user-attachments/assets/5d6b1865-608d-4261-b837-8459567dca47)

![Screenshot from 2024-12-01 00-05-11](https://github.com/user-attachments/assets/18f475a6-59b4-4cb7-89df-d1cf312ff748)

### systemctl restart `<service>`
Restarts the service.

### systemctl reload `<service>`
Reloads the service configuration without restarting.

### systemctl -t slice
The systemctl -t slice command in Linux is used to list all slice units managed by systemd. In systemd, a slice is a concept used to group system resources and organize services into hierarchies for better resource management and control

![Screenshot from 2024-11-30 23-40-27](https://github.com/user-attachments/assets/615deb12-8ee1-44a5-b389-dd6db465a746)


### systemctl is-active `<service>`
Checks if the service is active.

![Screenshot from 2024-11-30 23-45-06](https://github.com/user-attachments/assets/190a2596-d913-42df-9332-9dd0d24abc51)

### systemctl is-enabled `<service>`
Checks if the service is enabled on boot.

![Screenshot from 2024-11-30 23-44-00](https://github.com/user-attachments/assets/42dae816-7e5a-4698-8ab3-b1a2a85c5429)

### systemctl list-dependencies `<service>`
Displays the dependencies of the service.

![Screenshot from 2024-11-30 23-46-30](https://github.com/user-attachments/assets/c6471107-3e52-4f3d-ae05-6869ec111cf9)


### systemctl --failed
Lists all failed services.

![Screenshot from 2024-11-30 23-29-27](https://github.com/user-attachments/assets/4a979fd5-57dd-41b5-9082-e4b9087c179a)


### systemctl mask/unmask `<service>`
Prevents or allows the service from being started manually or automatically

![Screenshot from 2024-11-30 23-50-11](https://github.com/user-attachments/assets/ca6f44be-2a19-4d6f-80de-83b5c2a1d11a)
