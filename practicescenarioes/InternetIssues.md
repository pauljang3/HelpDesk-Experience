# Internet Connectivity Issues (DHCP)

## Full Ticket Conversation
- If you'd like to take a look at the whole ticket from start to resolution click [here!](https://github.com/pauljang3/HelpDesk-Experience/blob/main/practicescenarioes/InternetIssuesFullTicket.md)
  
## Issue Overview
![internetissuedhcp](https://github.com/user-attachments/assets/94a89f00-3794-4e82-9f0f-65549c2096b2)
- From the initial support request, we can see the user is reporting issues with their internet connectivity through an ethernet cable.
- The user took some steps to try and troubleshoot by rebooting their computer and verifying that other devices are able to access the internet.


## My Approach
### Initial Assessment
- The user claims to have rebooted their computer and confirmed that other devices can access the internet. While I cannot verify the accuracy of these steps, I will keep them in mind as I troubleshoot the issue.
- Based on the ticket details, it appeared the problem was isolated to the client’s computer.
- I prioritized troubleshooting the physical connection (Ethernet) first, as the client had already 'ruled out' Wi-Fi and other devices working.

### Steps Taken
- To rule out physical connection issues, I first asked the user to test the Ethernet cable with a different device, try a new cable, and use a different Ethernet port.
- Since the Ethernet connection worked with a different device but the issue persisted with a new cable, I concluded that the problem was likely with the user's computer.
  
![step1](https://github.com/user-attachments/assets/861bf877-0cbd-4c71-8087-9e6f4d43ee58)
- I then requested an identifier from the user for remote access and connected to the computer.

![step2](https://github.com/user-attachments/assets/ca01a8b0-50c4-489a-b237-5455828b432a)
- After running the `ipconfig` command, the IP address displayed in the **169.254.x.x** range, which indicated a failure to obtain an IP address from the DHCP server.

![step3](https://github.com/user-attachments/assets/785a387f-6d31-4b8d-93a4-b82323237045)


### Challenges Faced
- The issue required remote troubleshooting, which delayed the process as I had to rely on the client’s actions to test physical connections.

### Decisions Made
- I decided to renew the client’s IP address using `ipconfig /release` and `ipconfig /renew` since the issue was related to the computer not receiving a valid IP address from the DHCP server.

---

## Resolution
### Solution
- Ran `ipconfig /release` and `ipconfig /renew` on the client’s computer, which successfully retrieved a valid IP address from the DHCP server, restoring internet access.
  
![step4](https://github.com/user-attachments/assets/21ea01b8-68f7-4eb0-85cb-99d86fd2762f)

### Testing
- After running `ipconfig /renew`, the user's device received a valid IP address (not one from the APIPA range).
- I asked the client to verify that they could browse the internet and access other network resources.
- The client confirmed that everything was working properly.

### Outcome
- The client’s internet connectivity issue was resolved, and they confirmed everything was working fine.
- The ticket was closed after confirming that the issue was no longer present.
---

## Reflection
### What Went Well
- Directing the client to try different physical connections (Ethernet cable and port) helped rule out potential hardware problems before focusing on the software side.

### Areas for Improvement
- I could have been more proactive by asking for the client's device identifier earlier in the process. This would have allowed me to begin remote troubleshooting while the user checked the physical connections, potentially leading to a quicker resolution time.

### Lessons Learned
- A systematic approach to testing both physical and network configurations (cable, port, IP address) can effectively pinpoint issues.
- When dealing with client-facing troubleshooting, it’s helpful to provide clear instructions for each step to avoid confusion.

---


