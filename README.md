Git Help
=======

New Repo:

    1. make repository from git account (example: abc)
    2. git remote add origin git@github.com:<username>/abc.git
    3. git pull origin master (getting update from main source in chitresh branch)

Branch:

    git branch (list branches)
    git branch chitresh (create branch chitresh)

Add and Commit:

    git add .
    git commit -m "message"

Push in branch:

    git checkout -b xyz (Switched to a new branch xyz)
    --
    git push origin master (if need to checkin in master branch)
    or
    git push origin chitresh (if need to checkin in chitresh branch)

Merge:
    
    git merge chitresh (branch cleanup )

Delete Branch:

    git push origin :chitresh (delete branch chitresh)
    git branch -D :chitresh (delete branch from local)
    
Delete Multiple Branch from local(unix):

    git branch -d `git branch | grep "somename*"`

Delete File and then commit:

    git rm filename.extn
    git add -u
    git commit -m "message"
       
    git push origin master
    
Switch to master branch and update source code:

    git checkout master  (Switched to branch 'master')
    git pull origin master (getting update in main source)

Merge master branch & chitresh branch:

    git merge --no-ff chitresh (merged master & chitresh)
    git push origin master (checkin in master code)


Suppose Conflicts:

    git add filename.rb ( you can use "git add ." also)
    git commit -m "my changes"
    --CONFLICT (content): Merge conflict in filename.rb
    --Automatic merge failed; fix conflicts and then commit the result.

Resolve Conflicts:
    git mergetool
    --Just to use my changes... no
    --their changes...

    git checkout --ours filename.rb
    git checkout --theirs filename.rb
    git add filename.rb
    git commit -m "using theirs"
    git pull origin branch_name
    
Resolve Multiple Conflicts: (Keep my changes)

    grep -lr '<<<<<<<' . | xargs git checkout --ours
    
Resolve Multiple Conflicts: (Keep their changes)

    grep -lr '<<<<<<<' . | xargs git checkout --theirs

Revert Changes:

    git revert commitnumber
    git merge master
    git add .
    git commit -m "revert files"
    git push origin master

Undo Commit:

    git reset --soft HEAD~1 
    
Hard Reset:

    git reset --hard origin/master

Agent Failure

    https://help.github.com/articles/error-agent-admitted-failure-to-sign/
    https://help.github.com/articles/testing-your-ssh-connection/
    https://www.digitalocean.com/community/tutorials/how-to-configure-ssh-key-based-authentication-on-a-linux-server
    
Check commit history

    git log (It will diplay all commits in latest to older order)
    git commit 72b6e6c75053fa8e160dea3bea678f32a675ae7a (it will show specific commit)ss
    git show --pretty="" --name-only 72b6e6c75053fa8e160dea3bea678f32a675ae7a (it will only list file name of specified commit)
    git diff-tree --no-commit-id --name-only -r 72b6e6c75053fa8e160dea3bea678f32a675ae7a (same as above) 

Git pull if conflict in pulling a branch 
    
    git pull -s recursive -X theirs <remoterepo> <branch>
