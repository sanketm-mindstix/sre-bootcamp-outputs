## Assignment 3F — Cron
1. Schedule a cron job that appends "I am alive - [timestamp]" to ~/bootcamp/heartbeat.log every minute.
2. Wait 3 minutes. Verify the file has 3 entries.
3. Remove the cron job.
4. Exploration question: Where does cron send output if your script prints something? How would you capture that output to a file?
-> Cron sends output (STDOUT + STDERR) to the local system mail for the user who owns the cron job


```bash
* * * * * echo "I am alive - $(date)" >> ~/Desktop/Projects/sre-bootcamp-outputs/linux_and_networking/day3/assignment-3f/heartbeat.log
```