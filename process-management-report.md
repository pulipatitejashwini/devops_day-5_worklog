# Process Management Report – Linux

## 1. Objective
The objective of this task is to understand Linux process management, including monitoring, controlling, and managing system processes and services.            

## 2. Listing Running Processes
`ps -ef`                  
Displays all running processes along with PID, user, and command details.                

`top`             
Provides real-time monitoring of CPU usage, memory usage, and running processes.                

## 3. Understanding Process States
Common process states observed:           
- **R** – Running            
- **S** – Sleeping               
- **Z** – Zombie            
- **T** – Stopped             

These states help in identifying system performance and stuck processes.              

## 4. Killing Processes               
`kill <PID>`            
- Gracefully terminates a process.            
- Allows the process to: Save data, Close files, Clean up resources                      
- Preferred and safe method             

`kill -9 <PID>`              
- Forcefully terminates.             
- Immediately stops the process            
- Process cannot ignore or handle this signal, No cleanup or data saving                  
- Use only if the process is stuck or unresponsive           
  
## 5. Managing Services Using systemctl
Check Service Status:           
`sudo systemctl status ssh`             
Start a Service:            
`sudo systemctl start ssh`             
Stop a Service:            
`sudo systemctl stop ssh`            
restart a service:            
`sudo systemctl restart ssh`                
Enable Service at Boot:            
`sudo systemctl enable ssh`               
Disable Service at Boot:              
`sudo systemctl disable ssh`            

### Sample Service: Nginx
As part of this task, **Nginx was installed and used as a sample service** to observe real-time process and service behavior.
Check Service Status:
- systemctl status nginx               
- systemctl start nginx                 
- systemctl stop nginx               
- systemctl restart nginx              
- systemctl enable nginx   # Enable service at Boot           
- systemctl disable nginx  # Disable service at Boot - Nginx will not start automatically after reboot, we must start it manually `systemctl start nginx`          

## 6. Monitoring Resource Usage
Commands Used:             
`top`           # CPU Utilization            
`free -m`       # Memory Usage            
`uptime`        # Check system runtime and load average               

## 7. Port & Process Verification Using ss
To validate service behavior, port listening status was verified using `ss`.
Command Used:
`ss -ntpl`
Observations:
- When Nginx was running, port 80 was in LISTEN state           
- After stopping or killing the Nginx process, port 80 was released             
- This confirmed successful process termination and service control
    
## 8. Findings & Observations
- High CPU usage can be detected easily using `top`        
- Zombie processes indicate improper process termination             
- `systemctl` provides efficient service management
- `ss -ntpl` helps verify active network ports and running services       
- Force killing processes should be avoided unless necessary          

## 9. Conclusion
This task improved my understanding of Linux process lifecycle management and service control, which are essential for DevOps, SRE, and Cloud operations roles.         
