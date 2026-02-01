# Day 04 – Linux Practice: Processes and Services

Today I practiced basic Linux commands on an AWS EC2 Ubuntu instance. The focus was on understanding processes, services, and logs.

I started by checking running processes.  
Command used:
```bash
ps
Observation: This command shows the processes running in the current terminal session.

To view detailed process information, I used:
ps aux | head
Observation: This displays the first few lines of the ps aux output, including the header and top running processes.

For live process monitoring, I used:
top
Observation: This command displays real-time running processes along with CPU and memory usage.

Next, I checked service-related commands. To verify the Docker service status, I used:
systemctl status docker
Observation: This command checks whether the Docker service is running, stopped, or failed and also shows recent logs and service details.

To list active Docker-related services, I used:
systemctl list-units | grep docker
Observation: This lists all active systemd units related to Docker and shows their current state.

Finally, I practiced log-related commands. To check Docker service logs, I used:
tail -n 50 /var/log/syslog
Observation: This shows the last 50 lines of the system log to identify recent system activity or errors.
