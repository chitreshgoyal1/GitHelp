Problem: Remove commit 98y65r4 and 987xcrt
=======

    abcd123    some message
    xyze456    another commit message
    98y65r4    commit is not required
    987xcrt    commit is not required
    dslr67r    initial commit


    Solution: There are two alternatives to this


Way 1: Revert a commit - Maintain History
    
          It means it will revert that commit and create a new commit for same to keep it in history. 
          You would need to execute it twice (once per commit):

          git revert 98y65r4
          git revert 987xcrt
          (execute gitk --all to see a graphical representation of the state of your repo):

          **Now it look like:**
          2222222    revert of 987xcrt: this commit is not required
          1111111    revert of 98y65r4: this commit is not required
          abcd123    some message
          xyze456    another commit message
          98y65r4    commit is not required
          987xcrt    commit is not required
          dslr67r    initial commit

          Now push both new commits to remote repo:
          git push
          This solution is safe because it does not make destructive operations on your remote repo.

Way 2: Interactive rebase - No fooprint

          It means it will delete both commit from history, there will be no track if the commit existed or not.

          **rebase to an older commit**
          git rebase -i dslr67r  or  git rebase -i HEAD~5
          
          When you execute the command and vi editor will open with a text similar to this:

          pick    dslr67r    initial commit
          pick    987xcrt    commit is not required
          pick    98y65r4    commit is not required
          pick    xyze456    another commit message
          pick    abcd123    some message
          
          **Just go on and delete the lines you don't want, like this:**

          pick    dslr67r    initial commit
          pick    xyze456    another commit message
          pick    abcd123    some message
          Save the file and close the editor.

          Till now it has only modified the local copy 
          See the tree of commits with gitk --all
          
          Alternate way to see is:
          git log --pretty=oneline --abbrev-commit

          Now you need to push your changes to your repo, which is done with a "push force", but before you execute the command bear in mind that push force is a destructive operation, it will overwrite the history of your remote repository and can cause merge troubles to other people working on it. If you are ok and want to do the push force, the command is:

          git push -f
