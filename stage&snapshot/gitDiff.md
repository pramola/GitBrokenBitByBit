This command is used to show changes between the different levels of the current branch, workspace directory and commit history


```
git diff  : show the unstaged changes from the staged changes(index). If changes commited then nothing is shown.
git diff --staged : show the added/removed changes from last commit(HEAD) to staged changes
git diff HEAD : show the difference between commited and unstaged changes.

git diff commitID_1 commitID_2 : show the difference between the two commit ids 
git diff branch_1 branch_2 : show the diff b/w two branches current/lastest HEAD to their common ancestor
```


Term	What it is
HEAD	The last commit (snapshot in .git/objects)
Index (Staging Area)	The "next commit" blueprint in .git/index
Working Tree	Your actual workspace directory on disk

```mermaid
flowchart TD
    A[git diff] --> B{Which two sides?}

    B -->|default| C[Index vs Working Tree]
    B -->|--staged| D[HEAD vs Index]
    B -->|HEAD| E[HEAD vs Working Tree]
    B -->|commit1 commit2| F[Commit A vs Commit B]

    C & D & E & F --> G[Compare file metadata<br/>path, mode, blob SHA]

    G --> H{Any differences?}
    H -->|No| I[Output: nothing to show]
    H -->|Yes| J[Build delta list:<br/>added / modified / deleted]

    J --> K[Rename detection<br/>similarity ≥ 50%]

    K --> L[For each modified file:<br/>run Myers diff algorithm]

    L --> M[Produce hunks:<br/>+ added lines<br/>- removed lines<br/>  context lines]

    M --> N[Format as unified diff]

    N --> O[Print to stdout]   
```