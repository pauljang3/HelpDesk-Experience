# Corrupt Windows User Profile

## Issue Overview
- The user was reporting that they were unable to use the Windows search bar and other Windows services were not responding, such as settings.  
- Personalized features such as the background wallpaper and mouse settings also changed.

---

## My Approach

### Initial Assessment
- Based on the given information, I determined that this problem was likely due to a corrupted Windows user profile.  
- Prior to making major changes such as deleting the user profile, I wanted to see if there was a possible solution that was less disruptive.  
- I confirmed the problem was user-specific by logging into another user account, which worked as expected.  
- Before changing anything, I began by backing up the user's documents.

### Steps Taken
1. I started by backing up files from the corrupted user to a new and working user.  
2. After running `sfc /scannow`, the problem persisted.  
3. I then tried to revert to a previous state using System Restore.  

    ![restore](https://github.com/user-attachments/assets/c48015f7-4fab-4a48-b3bf-25c664217029)

      After restoring to the earlier state, the problem continued.  
4. Next, I tried an in-place installation using the Windows Installation Media tool. While some features returned to normal, there were still several issues.  
5. I opened regedit and navigated to the path:  

    `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\ProfileList`

    ![ssid](https://github.com/user-attachments/assets/c2237150-7fca-4f2b-a6c8-63478b1224a0)

6. I identified the corrupt user profile, then deleted the SID of that profile.  
7. I finished the deletion of the corrupt user by removing the corrupt user profile folder:  

    `C:\Users\<CorruptedProfileName>`

8. Finally, I logged in with an administrator account to create a new user account, transferring the user's files to this newly created account.



### Challenges Faced
- It was a bit scary deleting user profiles, but I felt more confident having the backup ready in case anything went wrong, which reassured me.

### Decisions Made
- I decided to go ahead and resolve the problem by deleting the user profile. I came to this decision after several attempts to fix the issue in a less disruptive manner, such as using `sfc /scannow` and System Restore.

## Resolution

### Solution
- The issue was solved by deleting the corrupt user SID and transferring the user's files to a newly created user profile.

### Testing
- It was determined that Windows functions such as the settings app and search bar were functional on the new user profile.

### Outcome
- The user was able to use the new user profile and could continue their work without further issues.

## Reflection
### What Went Well
- I did not get too frustrated when my initial attempts at troubleshooting did not go as planned.
- I persisted and found a way to resolve the issue

## Areas for Improvement
- I believe I could have been more thorough and exhaust all options before proceeding to delete the user profile.

## Lessons Learned
- When troubleshooting a problem, it is important to keep an open mind and be flexible in my approach.
