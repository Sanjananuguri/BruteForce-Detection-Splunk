Brute Force Login Detection Using Splunk
Project Title
Detecting Simulated Brute Force Attacks Using Splunk on Windows
Objective
To simulate failed login attempts (brute-force attack behavior) on a Windows system, ingest the logs into Splunk, and set up a detection alert.
Tools Used
•	Splunk Enterprise (Free Trial)
•	Windows OS
•	Notepad (for log creation)
Project Structure
BruteForce-Detection-Splunk/
├── auth_simulation.log
├── screenshots/
│   ├── upload-log.png
│   ├── splunk-search-results.png
│   ├── alert-configuration.png
│   └── triggered-alert.png
└── README.md (this file)
Steps Performed
1. Created a Log File with Fake Login Failures
Created a simulated log file:
[2025-06-06 10:22:01] Failed login for user: admin from IP 192.168.0.5
[2025-06-06 10:22:02] Failed login for user: admin from IP 192.168.0.5
[2025-06-06 10:22:03] Failed login for user: admin from IP 192.168.0.5
[2025-06-06 10:22:04] Failed login for user: admin from IP 192.168.0.5
[2025-06-06 10:22:05] Failed login for user: admin from IP 192.168.0.5
[2025-06-06 10:22:06] Successful login for user: admin from IP 192.168.0.5
Saved as C:\logs\auth_simulation.log
2. Ingested Log File into Splunk
•	Opened Splunk at http://localhost:8000
•	Navigated to Settings > Add Data
•	Uploaded the .log file
•	Indexed into the main index
3. Ran Search Query in Splunk
Searched for brute-force style patterns:
index=* "Failed login" | stats count by host, _time | where count > 4
4. Created an Alert in Splunk
•	Triggered when the number of failed logins exceeded 4
•	Alert name: Windows Brute Force Simulation
•	Configured action to log and optionally email when triggered
Screenshots
Will be added soon for the following:
•	Log upload screen
 
•	Query results
 
•	Alert setup
 
•	Triggered alert log

 
What I Learned
•	Basics of Splunk setup on Windows
•	How to simulate log data
•	How to ingest data into Splunk
•	Writing basic SPL (Search Processing Language)
•	Creating alerts for suspicious behavior
Future Improvements
•	Use real-time Windows Event Logs instead of static .log files
•	Ingest logs from PowerShell or Sysmon
•	Add dashboards for visualization

