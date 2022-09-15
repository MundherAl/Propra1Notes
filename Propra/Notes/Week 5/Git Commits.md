# Git Commits
- New commands:
	- `git log` shows the change history of the repository.
	- `git blame` shows change history of file lines and who changed them.
		- `git blame filename.txt` shows who changed which lines on the file filename.txt.
	- `git diff` shows all changes since the last commit.
		- `git diff ecc54380 4fb4322c` shows the changes between two given commits.
---
## Sensible commits
When commiting, it's a very good idea to add a useful commit message. The message should answer the following questions:
- Why was the change made?
- What was changed?
- How will this commit affect other parts of the project?
- If the commit is linked to any issues, mention them.
---
## .gitignore
- the .gitignore file contains files that do not get pushed to the remote repository.
- Projects are often structured for a specific IDE or operating system. A .gitignore can be very useful for collaberating and teamwork as many use different IDEs and operating systems.