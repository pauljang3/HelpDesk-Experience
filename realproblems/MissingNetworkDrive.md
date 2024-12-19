# Missing Network Drive

## Issue Overview
- A newly configured user account was unable to find/access a couple of network drives.

---

## My Approach

### Initial Assessment
- I determined that this was a simple fix that required mapping the missing network drives.
- I started by identifying which network drives the user was unable to access (the H: and Z: drives).

### Steps Taken
1. I first looked for a way to map the network drive using the GUI in File Explorer but was initially unable to locate it.
2. I then opened the Command Prompt, and mapped the drives manually using the following commands:

   ```cmd
   net use Z: \\[ServerName]\[SharedFolderName]
   net use H: \\[ServerName]\[SharedFolderName]\[SubfolderPath]

### Challenges Faced
- Initially, I couldn't locate the GUI method for mapping network drives, which added a bit of time to the troubleshooting process.
- Despite this, I was able to efficiently use the Command Prompt as an alternative.

  ![gui](https://github.com/user-attachments/assets/3654fcba-1b07-4009-bc84-7c4305828fa3)

### Decisions Made
- Since I couldn't quickly find the GUI method during troubleshooting, I opted to proceed with the Command Prompt to save time and ensure the drives were mapped promptly.

## Resolution
### Solution
- The issue was resolved by manually mapping the required network drives, as the office did not have a script to automatically map drives for new users.

### Testing
- After mapping the drives, I verified their functionality by accessing files stored on both drives.

### Outcome
- The new user was able to access the H: and Z: drives successfully and could perform their work without further issues.


## Reflection
### What Went Well
- I adapted quickly to the situation by using the Command Prompt instead of being stuck trying to locate the GUI option.
- I effectively resolved the issue in a timely manner and documented the alternative method for future reference.

### Areas for Improvement
- I could improve by familiarizing myself further with the GUI tools in advance, which might have allowed me to map the drives even faster.

### Lessons Learned
- Command-line tools can serve as a powerful and time-saving alternative when GUI methods are not immediately apparent.
