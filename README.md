# ELK-Lab

## Objective

Investigate an alert by IDS regarding a potential C2 communication.

During normal SOC monitoring, Analyst John observed an alert on an IDS solution indicating a potential C2 communication from a user Browne from the HR department. A suspicious file was accessed containing a malicious pattern. 
A week-long HTTP connection logs have been pulled to investigate. Due to limited resources, only the connection logs could be pulled out and are ingested into the connection_logs index in Kibana.

My task will be to examine the network connection logs of this user, find the link and the content of the file.

### Skills Learned

- ELK Stack Proficiency.
- Incident Investigation.
- SIEM (Security Information and Event Management) Skills.
- Indicator of Compromise (IOC) Detection.
- Development of critical thinking and problem-solving skills in cybersecurity.

### Tools Used

- ELK.


## Steps

~TASK 1: Determine the number of events returned for March 2022 and identify the IP associated with the suspected user in the logs.

First, I need to connect to the connection_logs and filter the time range to March 2022.


![image](https://github.com/user-attachments/assets/6ae61d35-5393-498b-b576-d3b7a65dba3c) ~connection_logs


![image](https://github.com/user-attachments/assets/0285c6e8-d84c-40ff-8228-db69c48264f2)


While reviewing the connection logs for the specified time frame, I observed that 1,482 alerts were generated. By clicking on the source_ip in the available fields section, I quickly identified the suspected user's IP address.


![image](https://github.com/user-attachments/assets/585630ec-04cb-4074-9342-34a91ce617ed)


~TASK 2: The user’s machine used a legit windows binary to download a file from the C2 server. Find the name of the binary.

I applied this filter to retrieve all relevant information on the alerts.


![image](https://github.com/user-attachments/assets/c245f2dc-6189-4e31-bcab-5126773c8a04)


After clicking on one of the alerts, I was able to view all the necessary information.

![image](https://github.com/user-attachments/assets/2258b82c-c878-4517-8651-8423419f8e5d)


-The name of the binary is the user_agent: bitsadmin. 

-The host 'pastebin.com' is a famous filesharing site, which also acts as a C2 server used by the malware authors to communicate. 

-The full URL of the C2 to which the infected host is connected to is the host and the uri: pastebin.com/yTg0Ah6a

Lastly, when accessing the filesharing site 'pastebin.com', I found the name of the file that was accessed!











