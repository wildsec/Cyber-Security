  
**Alert Details:**

- **Alert Name:** Potential Task Scheduler Identified
- **Time:** 30/08/2025 10:06:07 AM
- **Host:** WIN-H015
- **User:** oliver.thompson
- **Task Name:** AssessmentTaskOne

Query the task name `**AssessmentTaskOne**` along with event ID `**4698**`, which indicates that a scheduled task was created. Since we also know the exact time of the activity, we can filter by timestamp to speed up the search. 
**Note:** For now, we won’t filter by host. This way, we can check whether the activity is isolated to a single machine or present across multiple hosts.
```
index="win-alert" EventCode=4698 AssessmentTaskOne  
| table _time EventCode user_name host Task_Name Message
```
![[Pasted image 20260317155910.png]]![[Pasted image 20260317155914.png]]