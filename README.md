# Honeypot-Lab-T-Pot-Deployment-and-Cyber-Threat-Monitoring.

## Objective

This project aimed to deploy a cloud-based honeypot environment using T-Pot and Amazon Web Services (AWS) to observe and analyze potentially malicious network activity. The project involved configuring an Ubuntu server on an AWS EC2 instance, setting up network security rules, and deploying multiple containerized honeypots that mimic commonly targeted network services. Using Kibana and T-Pot's Attack Map, I set up a monitoring environment to collect and visualize suspicious network activity. This hands-on experience deepened my understanding of cloud security, deception technology, network reconnaissance, and cyber threat intelligence.

## Skills Learned

- Deployment and configuration of cloud-based cybersecurity infrastructure.
- Understanding of honeypots and their role in cybersecurity.
- Configuration of AWS EC2 instances and security groups.
- Understanding of network ports, protocols, and firewall rules.
- Remote Linux server administration using SSH.
- Deployment and management of Docker containers.
- Familiarity with Elasticsearch, Logstash, and Kibana.
- Understanding of threat intelligence and attack visualization.
- Identification of commonly targeted network services.
- Troubleshooting cloud infrastructure and application services.
- Understanding of network exposure and access control.

## Tools Used

- **T-Pot:** Open-source multi-honeypot platform designed to collect and visualize potentially malicious network activity.
- **Amazon Web Services (AWS):** Cloud computing platform used to host the honeypot environment.
- **Amazon EC2:** Virtual cloud server used to deploy and operate T-Pot.
- **AWS Security Groups:** Cloud-based firewall controls used to manage inbound network traffic.
- **Ubuntu Linux:** Operating system used to host the honeypot platform.
- **Kali Linux:** Operating system used to remotely administer the cloud server.
- **Secure Shell (SSH):** Protocol used to securely access and manage the remote server.
- **Docker:** Containerization platform used to deploy and manage individual honeypots and supporting services.
- **Git and GitHub:** Used to download the T-Pot source repository and installation files.
- **Elasticsearch:** Search and analytics engine used to store and query collected security data.
- **Logstash:** Data processing tool used to ingest and process honeypot logs.
- **Kibana:** Data visualization platform used to monitor and analyze honeypot activity.
- **T-Pot Attack Map:** Visualization tool designed to display incoming attack activity and geographic information.

## Steps

### Step 1: Establishing a Remote Connection to the AWS EC2 Instance

I began by deploying an Ubuntu Linux server through Amazon EC2. Once the instance was running, I used my Kali Linux virtual machine to establish a remote SSH connection with key-based authentication.

After successfully connecting, I verified the server's operating system, available storage, memory usage, and network information before proceeding with the installation.

<img width="815" height="631" alt="Screenshot 2026-11-24 184419" src="https://github.com/user-attachments/assets/b88ab90d-16cf-46e4-94ba-0486695457bc" />

### Step 2: Downloading the T-Pot Repository

After connecting to the server, I navigated to the /opt directory and used Git to clone the official T-Pot repository from GitHub.

Once the download was complete, I navigated into the T-Pot directory and verified that the necessary installation scripts, configuration files, and Docker-related files were available.

<img width="807" height="608" alt="Screenshot 2026-11-24 184813" src="https://github.com/user-attachments/assets/e15b72c8-0e1a-49b4-80f4-8e4040a1c3d6" />

### Step 3: Installing the T-Pot Honeypot Platform

I executed the T-Pot installation script from the downloaded repository. The installer checked for conflicting network services, identified available ports, and began installing the necessary software packages and dependencies.

This process prepared the Ubuntu server to run the containerized honeypots and their supporting monitoring services.

<img width="788" height="611" alt="Screenshot 2026-11-24 185022" src="https://github.com/user-attachments/assets/77b71460-b886-4b04-ae55-e407f2249327" />

### Step 4: Selecting the T-Pot Hive Installation

After the initial configuration process completed successfully, I selected the standard T-Pot Hive installation.

The Hive installation provides a centralized honeypot environment that includes multiple honeypots, data collection services, and web-based visualization tools. I selected this configuration because it allowed me to operate multiple honeypots and their supporting analytics services within a single cloud instance.

<img width="790" height="605" alt="Screenshot 2026-11-24 185046" src="https://github.com/user-attachments/assets/2c5ef2f6-a95c-4785-8217-97ae56c388c1" />

### Step 5: Configuring Administrative SSH Access

During the deployment process, I modified the AWS EC2 security group's inbound rules to accommodate T-Pot's administrative SSH port.

T-Pot uses TCP port 64295 for administrative SSH access. Configuring this port separately from the standard SSH port helped distinguish administrative access from services intended for honeypot monitoring.

<img width="1246" height="437" alt="Screenshot 2026-11-24 185625" src="https://github.com/user-attachments/assets/60812632-776d-41d9-a32d-2bd9f6c6f5ce" />

<img width="1255" height="430" alt="Screenshot 2026-11-24 185634" src="https://github.com/user-attachments/assets/bb488004-0299-4ddd-bfbb-0891a394b8ce" />

### Step 6: Verifying Docker Container Deployment

After completing the installation and reconnecting to the server, I used Docker commands to verify that the T-Pot containers were running.

I reviewed the status of the individual honeypots and supporting services, including Elasticsearch, Logstash, Kibana, and Nginx. Several containers were still completing their initialization while others had already reported a healthy status.

Some of the deployed honeypots included:

- **Cowrie:** Designed to monitor SSH and Telnet activity.
- **Dionaea:** Designed to capture malware and interactions with emulated network services.
- **Conpot:** Designed to imitate industrial control systems.
- **Heralding:** Designed to collect authentication attempts across multiple protocols.
- **RDPHoneypot:** Designed to monitor Remote Desktop Protocol interactions.
- **Wordpot:** Designed to imitate WordPress environments.
- **Mailoney:** Designed to imitate SMTP mail services.
- **Adbhoney:** Designed to monitor Android Debug Bridge activity.

This step helped me understand how Docker lets multiple security applications and honeypots run on a single server.

*Figure 7: Reviewing running Docker containers, individual honeypots, and supporting service health statuses.*

### Step 7: Configuring AWS Security Groups and Honeypot Ports

To allow the honeypot environment to receive external network traffic, I configured additional inbound rules within the AWS EC2 security group.

I configured rules to monitor several commonly targeted network service ports, while using separate rules for administrative access.

These included:

| Port | Protocol/Service |
|---|---|
| 23 | Telnet |
| 80 | HTTP |
| 443 | HTTPS |
| 445 | SMB |
| 3389 | Remote Desktop Protocol |
| 3306 | MySQL – custom source rule |
| 64295 | T-Pot administrative SSH |
| 64297 | T-Pot web interface |

This configuration helped me better understand how network exposure, firewall rules, and access control influence the traffic that reaches a cloud-hosted system.

<img width="1235" height="747" alt="Screenshot 2026-11-24 191538" src="https://github.com/user-attachments/assets/bdc826f4-cf5a-4cad-aac0-1c50bb3f68a2" />

<img width="1857" height="616" alt="Screenshot 2026-11-24 191557" src="https://github.com/user-attachments/assets/c0b85cdc-2cc2-4357-929d-27badd1e5ae3" />

### Step 8: Accessing the T-Pot Web Interface

After configuring the required network access, I accessed the T-Pot web interface through a browser.

The interface confirmed that T-Pot version 24.04.1 was accessible and provided access to its integrated security monitoring and analysis tools, including the Attack Map, Kibana, CyberChef, Elasticvue, and SpiderFoot.

<img width="1907" height="721" alt="Screenshot 2026-11-24 192107" src="https://github.com/user-attachments/assets/633c316e-5317-4667-be8c-0ae3b64a0ccd" />

### Step 9: Exploring the Kibana Dashboard

I accessed Kibana to explore the dashboards available for analyzing honeypot activity.

The dashboard provided several visualizations designed to categorize incoming network activity, including:

- Attacks by honeypot.
- Attacks by destination port.
- Attacks by country.
- Attack frequency over time.
- Geographic visualization of network activity.

At the time of the initial review, the honeypot had not yet accumulated sufficient event data to populate the main attack statistics.

This step allowed me to become familiar with the monitoring interface and understand how incoming security events could be organized and analyzed.

<img width="1903" height="717" alt="Screenshot 2026-11-24 192247" src="https://github.com/user-attachments/assets/c84d69c0-19a2-41fe-8b08-e33f4d21475e" />

### Step 10: Accessing the Live Attack Map

Finally, I accessed the T-Pot Attack Map and verified that it displayed an active connection.

The Attack Map is designed to visualize incoming honeypot activity and provide information such as source IP addresses, IP reputation, estimated geographic location, targeted honeypots, network protocols, and destination ports.

Although no attacks had been recorded at the time of the screenshot, the monitoring interface was accessible and ready for further observation.

<img width="1907" height="795" alt="Screenshot 2026-11-24 192507" src="https://github.com/user-attachments/assets/a6a35dd2-86c6-4093-814e-2dc8e07fd5b7" />
## Conclusion

This project provided hands-on experience deploying a cloud-based honeypot environment and configuring the infrastructure necessary to monitor potentially malicious network activity. By using AWS EC2, Ubuntu Linux, Docker, and T-Pot, I gained a better understanding of how honeypots can be used to collect threat intelligence and observe interactions with commonly targeted network services.

The project also strengthened my knowledge of cloud infrastructure, remote server administration, network security, firewall configurations, and security monitoring tools.

This deployment established a foundation for future threat analysis, including investigating unauthorized authentication attempts, identifying commonly targeted services, analyzing suspicious IP addresses, and studying attack patterns through real-world honeypot telemetry.
