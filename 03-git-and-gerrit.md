# Training 701

### Git and Gerrit
Gerard Braad

gerard@unitedstack.com


## Why we use these tools

  * To encourage collaboration
  * To get improvements to users faster
    * Without sacrificing quality


## Overview
You will learn the basic usage of git as a source management tool.

  * branching
  * merging
  * rebasing
  * squashing

And the usage of Gerrit for the review process.


## What is version control
also known as Source Control Management

"The undo functionality for a developer"


## Available Open Source tools

  * CVS
  * Subversion
  * Mercurial
  * Bazaar
  * Git


## Git history
"As with many great things in life, Git began with a bit of creative destruction
and fiery controversy." -
[source](https://git-scm.com/book/en/v2/Getting-Started-A-Short-History-of-Git)

Linux kernel development is done as a large virtual global team

  * highly distributed


## I assume you have this installed

  * git
  * git-review

```
$ sudo yum install git git-review
```

```
$ sudo apt-get install git git-review
```


## Git basics
Nearly all operations are local, performed on a local repository

  * Fast and cheap actions
  * Full history


## Let's create a repository

```
$ mkdir awesome_project
$ cd awesome_project
$ git init
```

    Initialized empty Git repository in /home/gbraad/awesome_project/.git/


## What did just happen?
The command `git init` created a `.git` folder which represent the state of
your work directory and contains a local repository.


## The three states

  * Working directory
  * Staging area or index
  * Local repository (.git)


## Let's create our first change

```
$ echo "Hello, Git!" > hello
$ git add hello
$ git commit -m "Add hello file"
```

    [master (root-commit) ea80784] Add hello file
     1 file changed, 1 insertion(+)
     create mode 100644 hello


## What happened this time?
We stored our first change

```
$ git log
```

    commit ea8078459e0c569b0d055cc7d580a40ef36f5337
    Author: Gerard Braad <me@gbraad.nl>
    Date:   Tue Apr 19 07:47:56 2016 +0000
    
        Add hello file

Note: (root-commit)


## In more detail
Let's prepare a new commit.

```
$ echo "Goodbye, CVS!" >> hello
```

```
$ git status
```

    On branch master
    Changes not staged for commit:
      (use "git add <file>..." to update what will be committed)
      (use "git checkout -- <file>..." to discard changes in working directory)
    
            modified:   hello

Git tells you that there is a change that has not been staged yet.


## Verify changes
Always verify the changes you are going to commit

```
$ git diff
```

    diff --git a/hello b/hello
    index 670a245..4be5eec 100644
    --- a/hello
    +++ b/hello
    @@ -1 +1,2 @@
     Hello, Git!
    +Goodbye, CVS!


## Staging
Git has a convenient staging area, which allows you to prepare a commit from
changes you have.

```
$ git add hello
```


## Staged

```
$ git status
```
    On branch master
    Changes to be committed:
      (use "git reset HEAD <file>..." to unstage)
    
            modified:   hello


## Now make more changes

```
$ echo "Hello, Git! You rule!" > hello
```


## Now verify the changes

```
$ git status
```
    On branch master
    Changes to be committed:
      (use "git reset HEAD <file>..." to unstage)
    
            modified:   hello
    
    Changes not staged for commit:
      (use "git add <file>..." to update what will be committed)
      (use "git checkout -- <file>..." to discard changes in working directory)
    
            modified:   hello


## The diff compares staging and work directory

```
$ git diff
```
    diff --git a/hello b/hello
    index 4be5eec..d198fd6 100644
    --- a/hello
    +++ b/hello
    @@ -1,2 +1 @@
    -Hello, Git!
    -Goodbye, CVS!
    +Hello, Git! You rule!


## Choices

  1. I perform `git commit -m "Say goodbye to cvs"`
  2. I perform `git add hello; git commit -m "I declare my preference"`
  3. Perform two commits
  4. I undo my changes


## Choice 1

```
$ git commit -m "Say goodbye to cvs"
```

    [master bf5d3d8] Say goodbye to cvs
     1 file changed, 1 insertion(+)

```
$ git log
```

    commit bf5d3d87f4b354851ef5f41ec4bfba3673c326fa
    Author: Gerard Braad <me@gbraad.nl>
    Date:   Wed Apr 20 02:55:00 2016 +0000
    
        Say goodbye to cvs


## What happened

```
$ cat hello
```

    Hello, Git! You rule!

```
$ git show
```

    commit bf5d3d87f4b354851ef5f41ec4bfba3673c326fa
    Author: Gerard Braad <me@gbraad.nl>
    Date:   Wed Apr 20 02:55:00 2016 +0000
    
        Say goodbye to cvs
    
    diff --git a/hello b/hello
    index 670a245..4be5eec 100644
    --- a/hello
    +++ b/hello
    @@ -1 +1,2 @@
     Hello, Git!
    +Goodbye, CVS!


The last can be done manually  with `git diff master`


## Choice 2
```
$ git commit -m "I declare my preference"
```

    [master b8586e3] I declare my preference
     1 file changed, 1 insertion(+), 1 deletion(-)

```
$ git log
```

    commit b8586e361918fe8343b906706a1aa579badec64f
    Author: Gerard Braad <me@gbraad.nl>
    Date:   Wed Apr 20 03:01:37 2016 +0000
    
        I declare my preference
    

## What happened
```
$ git show
```
    commit b8586e361918fe8343b906706a1aa579badec64f
    Author: Gerard Braad <me@gbraad.nl>
    Date:   Wed Apr 20 03:01:37 2016 +0000
    
        I declare my preference
    
    diff --git a/hello b/hello
    index 670a245..d198fd6 100644
    --- a/hello
    +++ b/hello
    @@ -1 +1 @@
    -Hello, Git!
    +Hello, Git! You rule!


## Choice 3

```
$ git commit -m "Say goodbye to cvs"
```

    [master bf5d3d8] Say goodbye to cvs
     1 file changed, 1 insertion(+)

```
$ git add hello
$ git commit -m "I declare my preference"
```

    [master 89486a6] I declare my preference
     1 file changed, 1 insertion(+), 2 deletions(-)


## What happened
Both changes are commited. Use staging to your advantage to 'stage' partial changes.

```
$ git log
```

    commit 89486a636f60477d04637306ff75f382e0bac166
    Author: Gerard Braad <me@gbraad.nl>
    Date:   Wed Apr 20 03:05:57 2016 +0000
    
        I declare my preference
    
    commit bf5d3d87f4b354851ef5f41ec4bfba3673c326fa
    Author: Gerard Braad <me@gbraad.nl>
    Date:   Wed Apr 20 02:55:00 2016 +0000
    
        Say goodbye to cvs


## Choice 4

```
$ echo "Goodbye, CVS!" >> hello
$ git add hello
$ echo "Hello, Git! You rule!" > hello
```

```
$ git reset -- hello
```

This unstages the file and leaves the latest content


## For files in a commit
The previous files didn't exist in the repository. If you want to get a file
contents from a commit.

```
$ git reset HEAD hello
```

```
$ git checkout -- hello
```


## Move between commits

```
$ git checkout bf5d3d8   # or `git checkout master~1`
```

    Note: checking out 'bf5d3d8'.
    
    You are in 'detached HEAD' state. You can look around, make experimental
    changes and commit them, and you can discard any commits you make in this
    state without impacting any branches by performing another checkout.
    
    If you want to create a new branch to retain commits you create, you may
    do so (now or later) by using -b with the checkout command again. Example:
    
      git checkout -b new_branch_name
    
    HEAD is now at bf5d3d8... Say goodbye to cvs

```
$ cat hello
```

    Hello, Git!
    Goodbye, CVS!


## Back to master

```
$ git checkout master
```

    Previous HEAD position was bf5d3d8... Say goodbye to cvs
    Switched to branch 'master'


## What is master / are branches
Master is the name given to a branch. Branch names are pointers
to a change inside the git repository.

Branching in Git is a very cheap operation and initially exist
locally.


## Create a branch
To create a branch from the current checkout you can

```
$ git branch cool-feature
$ git checkout cool-feature
```

    Switched to branch 'cool-feature'

or

```
$ git checkout -b cool-feature
```


## What just happened

```
$ git branch
```

    * cool-feature
      master


## Graph

```
$ git log --oneline --graph --all

```

    * 5ce4316 I declare my preference
    * a4e6e04 Say goodbye to cvs
    * e52304d Add hello file


## Add some code

```
$ echo > hello << EOF
> #include<stdio.h>
> 
> int main(void) {
>     printf("Hello, World\n");
>     return 0;
> }
> EOF
$ mv hello hello.c
```


## What happened

```
$ git status
```

    On branch cool-feature
    Changes not staged for commit:
      (use "git add/rm <file>..." to update what will be committed)
      (use "git checkout -- <file>..." to discard changes in working directory)
    
            deleted:    hello
    
    Untracked files:
      (use "git add <file>..." to include in what will be committed)
    
            hello.c
    
    no changes added to commit (use "git add" and/or "git commit -a")


## I need to add and remove

```
$ git rm hello
$ git add hello.c
```


```
$ git rm hello
```

    rm 'hello'

```
$ git add hello.c
```


## Result

```
$ git status
```

    On branch cool-feature
    Changes to be committed:
      (use "git reset HEAD <file>..." to unstage)
    
            deleted:    hello
            new file:   hello.c

Note: the files are so different that no comparing can be done

```
$ git commit -m "Add Hello, C"
```


## What happened?
I have a master branch, and cool-feature.

Cool-feature is ahead by 1 change


```
  * ccd51d4 Add Hello, C
 /
* 5ce4316 I declare my preference
* a4e6e04 Say goodbye to cvs
* e52304d Add hello file
```


## Oops, I forgot to test
I haven't merged yet... so, let's test.

```
$ gcc hello.c -o hello
$ ./hello
```

    Hello World

```
$ git status
```

    Untracked files:
        hello
        

## We do not want to check in binaries

```
$ vi .gitignore
```

    hello
    <ESC>:wq

Now check this with `git status` and add this ignore file

```
$ git add .gitignore
$ git commit -m "Add ignored files (hello)"
```


## Merge
With merging to bring two branches together.

```
$ git checkout master
$ git merge cool-feature
```

    Updating 5ce4316..cf932b8
    Fast-forward
     .gitignore | 1 +
     hello      | 1 -
     hello.c    | 6 ++++++
     3 files changed, 7 insertions(+), 1 deletion(-)
     create mode 100644 .gitignore
     delete mode 100644 hello
     create mode 100644 hello.c


## What happened?

```
* master
|\
| * cf932b8 Add ignored files (hello)
| * ccd51d4 Add Hello, C
|/
* 5ce4316 I declare my preference
* a4e6e04 Say goodbye to cvs
* e52304d Add hello file
```

Note: standard behavior is Fast-forward


## What if we are behind?
What if someone else has also worked on the code

```
* 2c80817 Add basic Hello, C
| * cf932b8 Add ignored files (hello)
| * ccd51d4 Add Hello, C
|/
* 5ce4316 I declare my preference
* a4e6e04 Say goodbye to cvs
* e52304d Add hello file
```

Master is now ahead with a new change that was merged


## Back to the future
Rewriting history to take place in the future.

```
$ git checkout cool-feature
```

    Switched to branch 'cool-feature'


Get ready for conflicts


## Resolve conflicts

```
$ git rebase master
```

    First, rewinding head to replay your work on top of it...
    Applying: Add Hello, C
    Using index info to reconstruct a base tree...
    A       hello
    Falling back to patching base and 3-way merge...
    Auto-merging hello.c
    CONFLICT (add/add): Merge conflict in hello.c
    Failed to merge in the changes.
    Patch failed at 0001 Add Hello, C
    The copy of the patch that failed is found in:
       /home/ubuntu/workspace/awesome_project/.git/rebase-apply/patch
    
    When you have resolved this problem, run "git rebase --continue".
    If you prefer to skip this patch, run "git rebase --skip" instead.
    To check out the original branch and stop rebasing, run "git rebase --abort".


## Let's look at hello.c

    #include<stdio.h>

    int main(void) {
    <<<<<<< HEAD
        printf("Hello, World\n");
    =======
        printf("Hello World\n");
        return 0;
    >>>>>>> Add Hello, C
    }


We are told that there is a conflict from `<<<<<<< HEAD` to `=======` and
from `=======` to `>>>>>>> Add Hello, C`.

We edit the file till we think it is OK. leaving the `,` and the `return 0;`.


## Confirm
Make sure the code works; 'compile', 'run/test', and add resolved conflict.

```
$ git add hello.c
$ git rebase --continue
```

    Applying: Add Hello, C
    Applying: Add ignored files (hello)

```
$ git log --graph --oneline --all                                                                                                      
```

    * 066372d Add ignored files (hello)
    * f0a97ce Add Hello, C
    * 2c80817 Add basic Hello, C
    * 5ce4316 I declare my preference
    * a4e6e04 Say goodbye to cvs
    * e52304d Add hello file


## Merge these changes
```
$ git checkout master
```

    Switched to branch 'master'

```
$ git merge cool-feature
```

    Updating 2c80817..066372d
    Fast-forward
     .gitignore | 1 +
     hello.c    | 1 +
     2 files changed, 2 insertions(+)
     create mode 100644 .gitignore

Note: our change now only adds a `return 0;`


## Why rebasing?
The repository’s commit history is a record of what actually happened.

The repository’s commit history is the story of how your project was made.


## Review
In the case of OpenStack, we do not merge. We propose a change and rebase
on top of master to make sure we are up-to-date

Gerrit is used to perform the code-reviews and `git review` is used to submit/
propose your changes for review.


## Workflow
Create a topic branch

```
$ git checkout -b [branchname]
```

Code, code, code, commit
```
$ git commit
```

Write a great commit message

  * descriptive title, max 50 chars
  * concise, clear description. wrapped at 80 chars

```
$ git review
```


## What happens
First time you have to set your gerrit username and make sure your `ssh`
identity is known. I assume you have done this...

    git review
    remote: Processing changes: new: 1, refs: 1, done    
    remote: 
    remote: New Changes:
    remote:   https://review.openstack.org/[reviewid] [Title]
    remote: 
    To ssh://gbraad@review.openstack.org:29418/openstack/[repo].git
     * [new branch]      HEAD -> refs/publish/master/[branchname]


## Gerrit
Have a look at http://review.openstack.org/


## Make changes to review
Make changes and resubmit for review

```
$ git add [file]
$ git commit --amend
$ git review
```

Note: do not edit the `Change-Id` in the commit message. This is how Gerrit
tracks patch sets to the same commit.


## Don't

```
git push --force
```


## Reference

  * https://www.mediawiki.org/wiki/Gerrit/Tutorial
  * https://git-scm.com/book/en/v2
  * http://gitref.org/basic/
