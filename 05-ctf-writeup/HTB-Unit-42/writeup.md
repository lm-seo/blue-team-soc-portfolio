# Sherlock Scenario - [Unit 42](https://labs.hackthebox.com/achievement/sherlock/2221424/632)
In this Sherlock, you will familiarize yourself with Sysmon logs and various useful EventIDs for identifying and analyzing malicious activities on a Windows system. Palo Alto's Unit42 recently conducted research on an UltraVNC campaign, wherein attackers utilized a backdoored version of UltraVNC to maintain access to systems. This lab is inspired by that campaign and guides participants through the initial access stage of the campaign.

### Task 1 How many Event logs are there with Event ID 11?
It is important to start by managing the information provided by evtx. I like to process the information using Eric Zimmerman's tool [EvtxCmd.exe](https://github.com/EricZimmerman/evtx), export it to CSV, and use [CSV Quick Viewer](https://sourceforge.net/projects/csvquickviewer/) to manage the information.
This answer is simple. All I did to obtain this information was filter it by event ID.

- **Solution**: Filter by EventID --> 56
### Task 2: Whenever a process is created in memory, an event with Event ID 1 is recorded with details such as command line, hashes, process path, parent process path, etc. This information is very useful for an analyst because it allows us to see all programs executed on a system, which means we can spot any malicious processes being executed. What is the malicious process that infected the victim's system?
For this question, it is important to know and be able to recognize, among all the information presented, which file is potentially strange.
We continue with event ID 11. Remember that Sysmon Event ID 11, also known as “FileCreate,” logs file creation or overwrite operations on a system.
Capture

### Task 3 Which Cloud drive was used to distribute the malware
For this question, we will look at what the cloud service tells us. The trail I have followed is to search for DNS events, which will indicate the cloud service that was used to download the malware.
Captura
### Task 4 For many of the files it wrote to disk, the initial malicious file used a defense evasion technique called Time Stomping, where the file creation date is changed to make it appear older and blend in with other files. What was the timestamp changed to for the PDF file?
Throughout the exercise, if we know which ID to check, we will quickly find the answer. In this case, I focus mainly on ID 2 - File creation time changed.
By pressing CTRL + F, we search for PDF and there we have the information:
### Task 5 The malicious file dropped a few files on disk. Where was "once.cmd" created on disk? Please answer with the full path along with the filename.
Let's look for the file in the CSV; this will give us the full path.
CAPTURA
### Task 6 The malicious file attempted to reach a dummy domain, most likely to check the internet connection status. What domain name did it try to connect to?
We continue with the next question. Here we are going to use an ID that we have already seen before, since they are asking us about a domain. So let's check EventID 22, which is related to DNS.
Easy. If they ask us about a domain, we are going to check what has the objective of translating IPs into something readable.

### Task 7 Which IP address did the malicious process try to reach out to?
As has been the case so far, if we know the ID to search for what we need, finding information becomes much simpler. In this case, we will filter by EventID 3. This will give us the detected network connections. In this case, it is simple, as there is only one log. We look at the destination IP to get the answer.
### Task 8 The malicious process terminated itself after infecting the PC with a backdoored variant of UltraVNC. When did the process terminate itself?
We are going to filter by event ID 5, which indicates that a process has ended.


