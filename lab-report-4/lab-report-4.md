# Lab Report 4 - Vim 

## Lab Report Steps

### Step 4: Log into ieng6
- **Action**: Use SSH to log into your ieng6 account.
- **Keys pressed**: `ssh `

- **Effect**: Logs you into the ieng6 server using SSH. Replace `<user>` and `<host>` with your specific username and the ieng6 server address.

### Step 5: Clone Your Fork from GitHub
- **Action**: Clone your fork of the repository using the SSH URL.
- **Keys pressed**: `git clone <SSH-URL><enter>`

- **Effect**: Clones the repository from GitHub to your local machine. Replace `<SSH-URL>` with your repository's SSH URL.

### Step 6: Run the Tests (Demonstrating Failure)
- **Action**: Run the initial tests which are expected to fail.
- **Keys pressed**: `command-to-run-tests` `<enter>`


- **Effect**: Executes the test commands, showing that the initial tests fail. Replace `<command-to-run-tests>` with the specific command for your tests.

### Step 7: Edit the Code to Fix the Failing Test
- **Action**: Edit the code file where the tests are failing.
- **Keys pressed**: 
    - `vim ListExamples.java` `<enter>` open up ListedExamples.java in Vim to edit 
    - `:44 <enter>` to move cursor to line 44 
    - `fi` move to the next word on the line that starts with i 
    - `cwindex2`: Changes word where cursor is to index2
    - `esc` + `q!` : Exit and save
- **Effect**: Opens the file in Vim for editing, makes necessary changes, and saves them. Replace `<filename>` with the name of the file you're editing and `...edit commands...` with the actual keys you press to edit.

### Step 8: Run the Tests (Demonstrating Success)
- **Action**: Rerun the tests to show they now succeed.
- **Keys pressed**: `<command-to-run-tests><enter>`
- **Effect**: Reruns the tests, which should now pass. Use the same command as in Step 6.

### Step 9: Commit and Push the Changes
- **Action**: Commit and push the changes to your GitHub repository.
- **Keys pressed**: 
    - `git add .` `<enter>`  
    - `git commit -m "First Commit"` `<enter>`
    - `git push` `<enter>` 
- **Effect**: Save all changes, commits them with a message, and pushes the commit to GitHub repository.

