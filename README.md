# Osquery-ATT&CK

The goal of this repository is to try to map the MITRE ATT&CK with the Osquery for enterprise threat hunting.

Each conf file is a Query Pack that can be used enterprise threat hunting wit osquery. 

Mapping the MITRE ATT&CK Matrix with Osquery


I try to create Osquery pack that can cover some elements of the ATT&CK
## Windows Query Pack Descriprion

- **windows-registry-monitoring.conf** : Track all the change in the **registry** for malware persistency. The registry path are the path that can be find here:
    https://attack.mitre.org/wiki/Persistence. A second article that explain some presistency method https://www.countercept.com/our-thinking/hunting-for-application-shim-databases
- **windows-incorrect_parent_process.conf** : This check verify if some attackers or malware try to execute a legitim process in a malicious way
- **windows-incorrect_path_process.conf** : This check verify if some attackers or malware try to execute a legitim process in a wrong path.. so it looks suspicious :)
- **windows-process_no_disk_binary.conf** : This check retrieve events related to prcesso that do not have binary file on disk.
- **windows_powershell_events.conf** : This check retrieve events generated by PowerShell from the powershell_events table. Osquery reads the Microsoft-Windows-PowerShell eventlog channel, so you need to enable (http://bit.ly/2LvjSXn) Script block logging. 
- **windows_system_running_processes.conf** : This check retrieve the running progess on the system.
- **windows_persistence-startup_items.conf** : This check retrieve the programm that start when the OS start.
- **windows_service-persistence.conf** : This check retrive the service that start automatically
- **windows_critical_service_status.conf** : This check retrive critical service status change. So is possible to catch the attackers that stop a critical service like Windows Firewall Service. 
- **windows_scheduled_tasks.conf** : This check retrive scheduled tasks of the system
- **network_connection_listening.conf** : This check retrive the network connection of the system and the listening port
- **windows_anomaly_process-execution.conf** : This Check try to catch anomaly process execution in the Enterprise environment.
- **windows_generic_detection.conf** : This is a generic detection query pack.
- **windows_browsere-extensions.conf** : This check retrive the IExplorer and Chrome Browser browsere extensions.

## Windows ATT&CK MAPPING
- **windows-registry-monitoring.conf**
    - ATT&CK: T1015,T1138,T1131,T1037,T1128,T1060,T1180,T1004,T1058,T1103,T1112
- **windows-incorrect_parent_process.conf**
    - ATT&CK: T1173,T1086,T1204,T1183
- **windows_powershell_events.conf**
    - ATT&CK: T1086,T1064
- **windows_system_running_processes.conf**   
    - ATT&CK: T1034,T1121,T1117,T1085
- **windows_persistence-startup_items.conf**
    - ATT&CK: T1060
- **windows_service-persistence.conf** : This check retrive the service that start automatically
    - ATT&CK: T1050
- **windows_critical_service_status.conf** : This check retrive critical service status change. So is possible to catch the attackers that stop a critical service like Windows Firewall Service. 
    - ATT&CK: T1089
- **windows_scheduled_tasks.conf** : This check retrive scheduled tasks of the system
    - ATT&CK: T1053
- **network_connection_listening.conf** : This check retrive the network connection of the system and the listening port
    - ATT&CK: T1086,T1093,T1020,T1041,T1011,T1029,T1043,T1090,T1094,T1024,T1008,T1219,T1105,T1065
- **windows_anomaly_process-execution.conf** : This Check try to catch the anomaly process execution in the Enterprise environment. **THIS IS EXPERIMENTAL** because the queries can miss some process execution.
    - ATT&CK: T1191,T1118,T1059,T1170,T1086,T1117,T1053,T1035,T1197,T1128,T1134,T1126,T1087,T1201,T1069,T1057,T1012,T1018,T1063,T1082,T1049,T1007,T1124,T1076
- **windows_generic_detection.conf** : This is a generic detection query pack.
    - ATT&CK: T1136,T1078,T1116,T1075,T1097
- **windows_browsere-extensions.conf** : This check retrive the IExplorer and Chrome Browser browsere extensions.
    - ATT&CK: T1176


## Notes

* The query interval of each conf file is not tuned, so please test it in a test enviroments (suggestions are welcome)
* Suggestions and improvements are welcome for each query pack conf file.
* All the query output must sent to sistme like ELK or Splunk that correlate and alert.
* The project has just started, so stick around ;)
