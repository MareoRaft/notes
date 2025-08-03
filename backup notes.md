Recommended personal files backup process:
---
1. connect Matt's Elements external HD
2. create folder "Matt's Elements/backups/matt's macbook pro backup 2023-04-15" or similar
3. open Carbon Copy Cloner.app
1. choose destination as the folder you just made
4. choose select files and folders as origin. Select home folder, then get ready to exclude some subfiles / subfolders...
5. use commands like below to identify files and folders that take up too much space and are not important to you
  * sudo du -sh /Users/Matthew/programming/* | grep G
  * sudo du -hs .[^.]* | grep G
  * ACTUALLY, if you run the CCC PREVIEW RUN, then it will measure all the file sizes AND FOLDER SIZES.  It takes  long time to run the preview, but ultimately may be better to do it that way instead of trying to manually measure things a bit at a time.
    - You can THEN ORDER BY FILE/FOLDER SIZE which not only orders the top-level but orders all subtrees.  This is indespensable for finding things like ~/Library/Containers/Docker which is 65 GB.
    - I believe you can use the CUSTOM FILTERS / PERSONALIZED FILTERS option up-top to exclude files by name instead of having to hunt through the file hierarchy to find them.
6. deselect those files in CCC
  * potentially exclude ~/.Trash, empty the trash, or include it 
  * potentially delete all files in the Downloads folder
  * don't backup .elan or .lake folders
7. disconnect from internet
8. close all non-essential applications
9. start the CCC job
  * CCC will tell you how much file space is identified
  * if the amount of free space on the external HD is not enough, you need to delete old backups or something




Remarks:
  * it took me 60 minutes to delete old folders
