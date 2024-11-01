Git
------


Remove file from ENTIRE git history:
To remove file from git history, I recommend using the BFG approach referenced here:
https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository


Removing commits from a GitLab repo permanently:
https://docs.gitlab.com/ee/user/project/repository/reducing_the_repo_size_using_git.html#purge-files-from-repository-history



change a remote's url:
git remote set-url <remote-name> <remote-url>


Delete source branch on merge by default feature:
As of GitLab 12.5, this setting exists.  See:
https://docs.gitlab.com/ee/user/project/settings/index.html#merge-request-settings


Resources:
http://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository
http://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository


applying a diff to a repo:
https://stackoverflow.com/questions/12320863/how-do-you-take-a-git-diff-file-and-apply-it-to-a-local-branch-that-is-a-copy-o
git diff args > path/to/diff/output/file
git apply path/to/diff/input/file



editing an old commit message(s):
Let n be the number of commits ago of the older commit you want to edit.
git rebase -i HEAD~n
Change the word 'pick' to 'reword' for the commits you want to reword.
It will walk you through each commit message and you can modify it then.
reference:
https://stackoverflow.com/a/45302710/2203144


how to squash commits (combine multiple commits into one big commit):
https://github.com/todotxt/todo.txt-android/wiki/squash-all-commits-related-to-a-single-issue-into-a-single-commit


What is a remote-tracking branch?:
https://stackoverflow.com/questions/26125162/difference-between-origin-branch-name-and-branch-name


Setting any server as a remote:
(example)
git remote add jungle ssh://forgerock@jungle:/home/forgerock/programming/ar


Search a git repo:
git grep
Search across multiple commits or branches:
https://stackoverflow.com/questions/7151311/using-git-how-could-i-search-for-a-string-across-all-branches


Start a new branch that mirrors a branch on a remote:
git checkout --track origin/branch-name



SUBMODULES:
add submodule, but rename the dir:
https://chrisjean.com/git-submodules-adding-using-removing-and-updating/
https://github.com/supercollider/supercollider/wiki/git-cheat-sheet
updating & maintaining submodules:
http://www.vogella.com/tutorials/GitSubmodules/article.html#submodules


git flow, organizing branches, git development master, develop, release, feature organization:
https://nvie.com/posts/a-successful-git-branching-model/



git list all files being tracked in repo:
git ls-tree --full-tree -r HEAD

merge a branch with "this" or "our" branch being used and the other one completely forgotten:
git checkout branch-you-want-to-keep
git merge --strategy=ours other-branch


What do git HEAD^ HEAD^2 HEAD~ mean?
https://stackoverflow.com/questions/26785118/head-vs-head-vs-head-also-known-as-tilde-vs-caret-vs-at-sign


checking the newest changes to a file:
git diff HEAD~ path/to/file


merging conflicts!!!:
use git mergetool to walk through each conflict and resolve!, try git mergetool -y to go through ALL conflicted files.





Working Directory	Staging Area		Git Directory (repository)
Modified		Staged		Committed

COMMITING
git add path/to/file # for each file you changed
git commit --message "description of changes" (or -m instead of --message)
git push origin master
type "git status" # just to confirm it worked
*NOTE: ANYTIME BEFORE USING ORIGIN YOU MAY HAVE TO
 git remote add origin git@github.com:mareoraft/HelloWorld.git

STASHING.  You want to change branches but don't want to commit what you've been working on just yet!
see https://git-scm.com/book/en/v1/Git-Tools-Stashing

AMMEND A COMMIT
git commit --amend


CREATE OR CHANGE A REF
example:
git update-ref refs/prove-math-archive/pmdag refs/heads/pmdag



UNSTAGE SOMETHING
git reset HEAD path/to/file
or
git reset HEAD
for all files

MAKING NEW REPOSITORY
mkdir Test-Repository
cd Test-Repository/
git init
# Initialized empty Git repository in /Users/Matthew/Test-Repository/.git/


CREATE FILE OR GRANT FILE ACCESS
cd Test-Repository/
touch path/to/file
git add path/to/file
