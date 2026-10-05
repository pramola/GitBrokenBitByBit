This command is used to check for changed/created files that are sitting in your current folder/git repository (local changes).

Local Changes : The changes made by you on the file sitting in your repository. Also called as working directory. 

Working Directory: The folder where you create files and folders and their content in the disk(local disk)

Local Repository: The .git(hidden folder) is the folder where all your changes and snapshot(a point in time) is captured. A history keeper. This is where your commited changes sit.

Staging : Intermediate region (Buffer zone) between your working directory and local repository. Here you add the files(their changes) that you want to commit to git so that they are registered in the git chain(branch)

Commit: The changes are  registered locally and ready to be pushed to parent branch or main(top) branch. The changes are not visible to other till  the changes need to be merged in the main branch (pushing changes)

The difference after creation of a file 

    ```D:\Learning\GitBrokenBitByBit>git status
        On branch main
        Your branch is up to date with 'origin/main'.

        Untracked files:
        (use "git add <file>..." to include in what will be committed)
                stage&snapshot/gitAdd.md

        nothing added to commit but untracked files present (use "git add" to track)```

After staging the changes 

    ```D:\Learning\GitBrokenBitByBit>git status
    On branch main
    Your branch is up to date with 'origin/main'.

    Changes to be committed:
    (use "git restore --staged <file>..." to unstage)
            new file:   stage&snapshot/gitAdd.md```
    
After commiting the changes

    ```D:\Learning\GitBrokenBitByBit>git status
    On branch main
    Your branch is ahead of 'origin/main' by 1 commit.
    (use "git push" to publish your local commits)

    nothing to commit, working tree clean```

The three regions where the changes travel.
```mermaid
graph LR
    A[Working Directory on disk] -- 'git add' --> B[Staging Area]
    B -- 'git commit' --> C[Local Repository .git folder]  
    

Git status - a safe, read-only command
```mermaid
graph TD
    subgraph "git status output"
        A["On branch main"]
        B["Your branch is ahead of 'origin/main' by 1 commit"]
        C["Changes to be committed:"]
        D["Changes not staged for commit:"]
        E["Untracked files:"]
    end

    C -->|"staged changes (index vs HEAD)"| SA[Staging Area]
    D -->|"unstaged changes (worktree vs index)"| WD[Working Directory]
    E -->|"never added to git"| WD   
