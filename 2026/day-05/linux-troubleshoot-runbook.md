Linux Troubleshooting Notes - Day 05

Target Service/Process
 Service: SSH
 Process: sshd (listener)
 PID: 1300
 Host: AWS EC2 – Ubuntu 22.04 LTS
 Observation: SSH service running normally, no zombie or hung processes detected.

Enviornment Basics
 uname -a : The uname -a command displays complete information about the system’s kernel, operating system, architecture, and version.
 Observation : This is an AWS EC2 instance running Ubuntu 24.04.1 LTS with an AWS-optimized Linux kernel (6.14.x) on a 64-bit architecture, suitable for production workloads.

 cat /etc/os-release: Is used to view Linux OS distribution and version details.
 Observation : The system is running Ubuntu 24.04.3 LTS .

Filesystem Sanity
 mkdir /tmp/runbook-demo → directory created successfully
 Observation: Filesystem writable; no permission issues.

 cp /etc/hosts /tmp/runbook-demo/hosts-copy && ls -l /tmp/runbook-demo → file copy successful
 Observation: Basic file operations succeed; disk healthy.

 top → load average ~0.00, system healthy
 The system is idle with near-zero CPU usage, low load average, sufficient available memory, and no zombie processes.

 ps -o pid,pcpu,pmem,comm -p 1035 → sshd using negligible CPU/memory
 Observation: SSH process lightweight, not causing performance issues.

 free -h → sufficient free RAM, no swap usage
 Observation: Memory usage normal; no memory pressure.

Disk & I/O Snapshot 
 df -h :shows adequate free space on the root filesystem.
 Observation: Disk usage is within safe limits with no partitions nearing capacity.

iostat: command is used to monitor CPU utilization and disk I/O performance.
Observation: The system shows high CPU idle time and minimal disk read/write activity, indicating no I/O bottleneck.

Network Snapshot
ss -tulpn | grep sshd & ss -tulpn | grep :22 :The ss -tulpn command is used to display listening TCP/UDP ports along with the processes bound to them.
Observation:
SSH (sshd) is actively listening on port 22 on all IPv4 and IPv6 interfaces.

Logs Reviewed
journalctl -u ssh -n 50 → no SSH errors
Observation: SSH service starting and running cleanly.
tail -n 50 /var/log/auth.log → no failed logins
Observation: No suspicious authentication activity; system secure.




