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

### Task 1: Identifying Events and Suspected User's IP for March 2022

Procedure:

1. Connect to the connection_logs and filter the time range to March 2022.
2. Analyze the logs to find all events during this period.
   
Outcome: A total of 1,482 alerts were generated during the specified time frame. Upon further inspection, the suspected user's IP address was identified by clicking on the source_ip in the available fields.

Visuals: Connection logs filtered for March 2022.

![image](https://github.com/user-attachments/assets/585630ec-04cb-4074-9342-34a91ce617ed)


### Task 2: Identifying the Legitimate Binary Used to Download a File from the C2 Server

Procedure:

1. Apply a filter to view alerts associated with the user’s machine and examine the logs for more details.
2. Investigate the user_agent field to determine the binary used.

Visuals: Log details showing the C2 server connection and the user_agent information.

![image](https://github.com/user-attachments/assets/c245f2dc-6189-4e31-bcab-5126773c8a04)

![image](https://github.com/user-attachments/assets/2258b82c-c878-4517-8651-8423419f8e5d)

   
Outcome: The binary used for the file download was identified as bitsadmin, a legitimate Windows utility often abused by malware authors for malicious activities. The infected host connected to the C2 server hosted on pastebin.com:

C2 URL: pastebin.com/yTg0Ah6a

Additionally, the name of the file accessed on pastebin.com was uncovered during the investigation.

## Conclusion

This project demonstrates effective detection of suspicious events, identification of malicious behavior involving legitimate Windows binaries, and tracking of C2 server communications. Through log analysis and connection tracking, we successfully identified both the suspected user's IP address and the malicious activity carried out via pastebin.com.













