Recommended personal files backup process:
---
1. connect Matt's Elements external HD
2. create folder "Matt's Elements/backups/matt's macbook pro backup 2023-04-15" or similar
3. open Carbon Copy Cloner.app
4. choose select files and folders as origin. Select home folder, then get ready to exclude some subfiles / subfolders...
5. use commands like below to identify files and folders that take up too much space and are not important to you
  * sudo du -sh /Users/Matthew/programming/* | grep G
  * sudo du -hs .[^.]* | grep G
6. deselect those files in CCC
7. disconnect from internet
8. close all non-essential applications
9. start the CCC job
  * CCC will tell you how much file space is identified
  * if the amount of free space on the external HD is not enough, you need to delete old backups or something

