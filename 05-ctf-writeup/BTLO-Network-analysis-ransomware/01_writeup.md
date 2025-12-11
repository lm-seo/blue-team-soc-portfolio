# Lab preparation BTL1 - [Network Analysis Ransomware](https://blueteamlabs.online/achievement/share/challenge/133015/3)

ABC Industries worked day and night for a month to prepare a tender document for a prestigious project that would secure the company’s financial future. The company was hit by ransomware, believed to be conducted by a competitor, and the final version of the tender document was encrypted. Right now they are in need of an expert who can decrypt this critical document. All we have is the network traffic, the ransom note, and the encrypted ender document. Do your thing Defender!​

## Challenge Submission
### What is the operating system of the host from which the network traffic was captured? (Look at Capture File Properties, copy the details exactly) 
For this first question, let's start by analyzing the attached pcap with Wireshark. An easy way to obtain this information is in Wireshark > Statistics > Capture File Properties.

### What is the full URL from which the ransomware executable was downloaded? 
Since you are asking us for a URL, the first thing that came to mind was to filter by “http.” In this case, it's simple, because that simple filter already gives us the package that contains the complete path.
### Name the ransomware executable file? 
We have the route, so we have the file.
### What is the MD5 hash of the ransomware? 
To do this, we will use the Wireshark option to download the capture files. File > Export Objects > http. Select the only one available and you can now download the file. Now, using Linux, we will calculate the MD5.
In the console
md5sum file-name
### What is the name of the ransomware? 
We uploaded the file to VirusTotal to get more information. We can see that the name of the ransomware is TeslaCrypt.
### What is the encryption algorithm used by the ransomware, according to the ransom note? 
The document itself provides us with several formats, with the ransomware message, where they report which algorithm they have used.
### What is the domain beginning with ‘d’ that is related to ransomware traffic?
There are surely better ways, but I use the clue that it starts with d to search through all the packets (filtering by DNS in Wireshark) that start with d.
### Decrypt the Tender document and submit the flag 
For this one, I searched for "Teslacrypt decryptor" and used the Talos tool [Talos Universal TeslaDecrypter](https://www.talosintelligence.com/teslacrypt_tool) to decrypt the content of file.
