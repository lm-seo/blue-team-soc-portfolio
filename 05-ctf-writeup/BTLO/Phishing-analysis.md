# Lab Preparation BTL1 - [Phishing Analysis](https://blueteamlabs.online/achievement/share/challenge/133015/16)
A user has received a phishing email and forwarded it to the SOC. Can you investigate the email and attachment to collect useful artifacts?

First of all, following my workflow and as the room requests, we will detect the artifacts. For this, i used thunderbir to open the mail, I view the source and i copied the header en [https://mxtoolbox.com/EmailHeaders.aspx](https://mxtoolbox.com/EmailHeaders.aspx). Now, i have the info more readable.

## Who is the primary recipient of this email? 

First question: unlike other typical phishing emails in CTFs, we don't have the “from” field. So we're going to take a close look for elements that refer to recipients, and we find an email: 

## What is the subject of this email?

Look the email subject, but be carefull, it maybe have a trap.

## What is the date and time the email was sent? 

We cannot look at the date when the email was received; we have to look at the date and time when it was created.

## What is the Originating IP? 

Look the originating-IP.

## Perform reverse DNS on this IP address, what is the resolved host? (whois.domaintools.com) 

Search for the IP in Whois Tool and it will give you the host.

## What is the name of the attached file?

Look the atteched file in thunderbird.

## What is the URL found inside the attachment? 

Open the file and it have a url.

## What service is this webpage hosted on? 

Looking at the url, you should know what service is it.

##  Using URL2PNG, what is the heading text on this page? (Doesn't matter if the page has been taken down!) 

For exmaple, i used urlscan.io, the tool is not important.
