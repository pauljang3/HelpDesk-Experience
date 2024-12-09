# Scan To Email Printer / SMTP Authentication Fix
## Summary
- In this real-world problem I encountered, I was working in a SOHO (Small Office/Home Office) network for a law firm.
- This was one of my first problems I've troubleshooted (handled it on my second day of the job!), as such I was a little lost at first, but learned some valuable lessons.
- If you'd like a more in depth look at the steps taken to how I fixed this problem, I wrote a [guide](https://docs.google.com/document/d/e/2PACX-1vSwEgmaSTG0ZnqFp8BNE_Y-vO3FpDXdbM8p3SWTnTgnNSdTcl69RgLNMOOVktDZgG6pUZIX9z76v64f/pub) as I couldn't find much documentation for this problem!
## Issue Overview
- The scan-to-email function had stopped working on two printers:  
  - **Xerox AltaLink C8155**  
  - **Brother MFC-L8900CDW**  
- Additionally, the **Windows Server 2012** was unable to send health report emails. (Although this was unknown to me until after fixing the printers)
- According to my supervisor, these issues had occurred several months ago without any known changes to the configuration or network setup.

## My Approach

### Initial Assessment
- To begin troubleshooting, I logged into the printer admin console for the Xerox printer by accessing its IP address in a web browser.
- I navigated to **Properties > Scan To Email**, where I found several SMTP configuration options, including the ability to send a test email to check if the configuration was working.
- Without changing any configurations, I attempted to send a test email to myself to observe any error messages or issues.
- Upon receiving an error message with an error code, I focused too much on the specific error codes and tried to resolve them by following the manufacturer’s documentation, even though I should have recognized that the issue was larger than just the printer, as multiple devices were affected.
- After several frustrating attempts to troubleshoot the printer and following the manufacturer's steps for resolving the error codes, I took a step back and reassessed what I knew:
  - The issue was affecting multiple devices.
  - The problem had been ongoing for several months.
  - Some of the printer error messages pointed towards SMTP authentication issues.
  
  ![printererrormessage2](https://github.com/user-attachments/assets/2454e067-f726-4b60-a11d-f013e266c1b4)


### Steps Taken
- I began by researching similar issues online and found that many public SMTP servers, including Bell and Google, had stopped supporting "less secure apps," which impacted older printers lacking OAuth support.
- After discovering that Google App Passwords could resolve this, I switched the SMTP server to `smtp.gmail.com`.
- I created a Google App Password for the printer, stored it securely, and configured the printer to use port 587 for TLS authentication with my Google account.
- Although it didn’t work initially, some minor adjustments to the settings allowed the test email to send successfully.

For more detailed steps you can refer to the guide I created [here.](https://docs.google.com/document/d/e/2PACX-1vSwEgmaSTG0ZnqFp8BNE_Y-vO3FpDXdbM8p3SWTnTgnNSdTcl69RgLNMOOVktDZgG6pUZIX9z76v64f/pub)
  
![smtp](https://github.com/user-attachments/assets/b28cfd28-a414-4c7d-b2ac-a8f3f225ef99)

### Challenges Faced
- I initially spent too much time focusing on the printer's error codes and tried to resolve them without considering the larger issue affecting multiple devices.
- It wasn’t immediately obvious that the issue was tied to SMTP authentication, which led to some frustration and wasted time troubleshooting the wrong areas.
- The research into recent changes in SMTP server security took longer than I had anticipated, and I had to adjust my approach to work with Google's SMTP server.

### Decisions Made
- I decided to shift my focus from the printer’s specific error codes to the broader issue of SMTP authentication affecting multiple devices.
- After discovering that Google’s SMTP server would be more compatible, I chose to make the switch and use Google App Passwords to work around the "less secure apps" restrictions.
- To ensure the solution worked, I tweaked the printer's SMTP settings, adjusted the ports, and reconfigured authentication until I saw success.



---

## Resolution
### Solution
- The solution to the scan-to-email issue involved switching from the Bell SMTP server to Google's `smtp.gmail.com` server. This change was necessary due to the phasing out of support for "less secure apps" by public SMTP servers, including Bell.
- After switching the server, I used 2 different Google App Password to authenticate both the printers and reconfigured the printer's SMTP settings to use port 587 for TLS.
  
### Testing
- After implementing the solution, I tested the scan-to-email function on both printers. I was able to send a test email successfully from the Xerox and Brother printers, confirming that the issue had been resolved.
- Additionally, I tested the health report emails from the Windows Server 2012 machine, and these were successfully sent as well.
  
### Outcome
- Both printers regained their scan-to-email functionality, and the server was able to send its health report emails.
- The issue was fully resolved, and the SOHO was able to continue using the printers without interruptions.

---

## Reflection
### What Went Well
- Once I shifted my focus from the specific error codes to the broader issue of SMTP authentication, the solution became clearer.
- The research into the recent changes to SMTP server security was time-consuming but ultimately led to the discovery of the Google App Password solution, which resolved the issue effectively.
- I was able to troubleshoot and implement the solution within several hours, which is a positive outcome for a complex issue.

### Areas for Improvement
- I could have been more proactive in recognizing that the issue was likely not limited to the printer but part of a larger authentication issue affecting multiple devices, which could have saved time during troubleshooting.
- Initially, I focused too much on the error codes, which led me down the wrong troubleshooting path. A broader perspective could have helped me identify the core issue sooner.

### Lessons Learned
- It’s important to take a step back and reassess the situation when stuck, especially when multiple devices are affected by the same issue.
- Taking your time to examine the information provided can save a great deal of time.
- Researching common solutions and considering potential external factors (such as SMTP server security changes) can save valuable time and lead to quicker resolutions.
- Staying flexible and adjusting the approach based on new insights is key to solving technical problems efficiently.

---
