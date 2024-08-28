# 1. It is About Git Commit MSG how we type MSG in RIght Way
### 1. **Structure of a Commit Message**
   A good commit message typically consists of three parts:
   - **Subject Line**: A brief summary of the changes (about 50 characters).
   - **Body**: A more detailed explanation (if necessary), wrapped at 72 characters.
   - **Footer**: (Optional) Any references to issues, PRs, or breaking changes.

### 2. **Guidelines for Writing Commit Messages**

   - **Use the Imperative Mood**: Write the subject line as a command. For example, use "Fix bug" instead of "Fixed bug" or "Fixes bug."
   - **Capitalize the First Letter**: Always start the subject line with a capital letter.
   - **Keep it Brief**: Limit the subject line to around 50 characters. If more detail is needed, use the body.
   - **Avoid Punctuation at the End of the Subject**: Don’t end the subject line with a period.
   - **Separate the Subject from the Body with a Blank Line**: This helps in making the commit message readable.
   - **Wrap the Body at 72 Characters**: This ensures that the message is displayed correctly in various interfaces.
   - **Explain *What* and *Why***: In the body, explain what changes were made and why, but avoid explaining *how* (the code itself shows that).

### 3. **Example Commit Messages**

#### Simple Commit (Subject Only):
```plaintext
Add user authentication feature
```

#### Commit with a Body:
```plaintext
Fix user login issue

The login form was not handling the case where users tried to
log in with an email address that had an uppercase letter.
This commit normalizes email addresses to lowercase before
processing the login request.

This change ensures consistency across the user authentication
process.
```

#### Commit with Footer (Issue Reference):
```plaintext
Update documentation for API changes

The API endpoint for retrieving user data has been updated to
include additional filtering options. Updated the documentation
to reflect these changes.

Fixes #42
```

#### Commit with Breaking Change:
```plaintext
Refactor database schema

Reorganized the database schema to improve performance and
reduce redundancy. This change requires a migration that will
break existing setups.

BREAKING CHANGE: The users table now has a unique constraint
on the email column.
```

### 4. **Why Follow These Guidelines?**
   - **Consistency**: Consistent commit messages help in quickly understanding the history of a project.
   - **Collaboration**: Clear messages make it easier for others (and your future self) to understand the changes.
   - **Automation**: Tools like GitHub, GitLab, and CI/CD systems often use commit messages for triggering actions, generating changelogs, etc.

Following these guidelines will help you write clear, concise, and informative commit messages, making your project history easier to navigate and understand.


# Git and Version Control Terms and Definitions

## Commit
A command to make edits to multiple files and treat that collection of edits as a single change.

## Commit Files
A stage where the changes made to files are safely stored in a snapshot in the Git directory.

## Commit Message
A summary and description with contextual information on the parts of the code or configuration of the commit change.

## Diff
A command to find the differences between two files.

## DNS Zone File
A configuration file that specifies the mappings between IP addresses and host names in your network.

## Git
A free open source version control system available for installation on Unix-based platforms, Windows, and macOS.

## Git Directory
A database for a Git project that stores the changes and the change history.

## Git Log
A log that displays commit messages.

## Git Staging Area
A file maintained by Git that contains all the information about what files and changes are going to go into the next commit.

## Modified Files
A stage where changes have been made to a file, but they have not been stored or committed.

## Patch
A command that can detect that there were changes made to the file and will do its best to apply the changes.

## Repository
An organization system of files that contain separate software projects.

## Source Control Management (SCM)
A tool similar to VCS to store source code.

## Stage Files
A stage where the changes to files are ready to be committed.

## Tracked
A file’s changes are recorded.

## Untracked
A file’s changes are not recorded.

## Version Control Systems (VCS)
A tool to safely test code before releasing it, allow multiple people to collaborate on the same coding projects together, and stores the history of that code and configuration.




# 2. Git Remove & Rename & .gitignore Diff & git log & add 

| **Command**            | **Explanation**                                                                                                                                                                 | **Link**                                                                                           |
|------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|
| `git commit -a`        | Automatically stages files that have been locally modified. New files that have not been published yet are not affected.                                                        | -                                                                                                  |
| `git log -p`           | Produces patch text that displays the lines of code that were changed in each commit in the current repository.                                                                 | -                                                                                                  |
| `git show`             | Shows one or more objects such as blobs, trees, tags, and commits.                                                                                                              | -                                                                                                  |
| `git diff`             | Similar to the Linux `diff` command, it can show the changes between commits, changes between the working tree and index, changes between two trees, changes from a merge, etc. | -                                                                                                  |
| `git diff --staged`    | Alias of `git diff --cached`, shows all staged files compared to the named commit.                                                                                              | -                                                                                                  |
| `git add -p`           | Allows a user to interactively review patches before adding them to the current commit.                                                                                         | -                                                                                                  |
| `git mv`               | Similar to the Linux `mv` command, this command can move or rename a file, directory, or symlink.                                                                               | -                                                                                                  |
| `git rm`               | Similar to the Linux `rm` command, this command deletes or removes a file from the working tree.                                                                                | -                                                                                                  |
| `.gitignore` files     | `.gitignore` files tell Git to intentionally ignore some files in a given Git repository. Useful for configuration files or metadata that should not be checked into the branch. | [Gitignore Documentation](https://git-scm.com/docs/gitignore)                                      |
|                        | When writing a `.gitignore` file, specific formats help Git understand the text, such as using `#` for comments or `/` for directory separators.                                | [GitHub Repository with `.gitignore` examples](https://github.com/github/gitignore)                |

# 3. Study guide: Git Revert

### **1. `git checkout`**
- **Purpose**: Switch between branches or restore files from a branch.
- **Usage**:
  - To switch branches: `git checkout <branch-name>`
  - To restore a file to its state in a specific branch: `git checkout <branch-name> -- <file-name>`
  
### **2. [`git reset`](https://jwiegley.github.io/git-from-the-bottom-up/3-Reset/4-doing-a-hard-reset.html)**
- **Purpose**: Unstage changes or move the HEAD to a different commit.
- **Types**:
  - **Soft Reset**: `git reset --soft <commit>` - Moves the HEAD to a specified commit but leaves changes in the staging area.
  - **Mixed Reset** (default): `git reset --mixed <commit>` - Moves the HEAD to a specified commit and unstages changes.
  - **Hard Reset**: `git reset --hard <commit>` - Moves the HEAD to a specified commit and discards all changes in the working directory and staging area. **Use with caution!**
- **Usage**: To unstage changes: `git reset` or `git reset <file-name>`

### **3. `git commit --amend`**
- **Purpose**: Modify the most recent commit, either to change the commit message or add more changes.
- **Usage**: `git commit --amend`
  - You can change the commit message or add new changes to the last commit.

### **4. `git revert`**
- **Purpose**: Create a new commit that undoes the changes made by a previous commit. This keeps your commit history intact.
- **Usage**: `git revert <commit-hash>`
  - This creates a new commit that reverses the effects of the specified commit.

### **5. SHA-1 Hash**
- **Purpose**: Identify commits and objects in Git. SHA-1 hashes are used for checking the integrity and identity of commits.
- **Usage**: You can find commit hashes using `git log`, and use these hashes with commands like `git revert`.

### **Additional Tips:**

- **Using `git stash`**: If you need to switch branches but have uncommitted changes, `git stash` can temporarily save your changes. Restore them with `git stash pop`.
- **Check Git Status**: Use `git status` frequently to check the state of your working directory and staging area.
- **Backup Your Work**: Before using commands that can potentially discard changes (like `git reset --hard`), consider creating a backup branch with `git branch backup-branch-name`.

Feel free to explore more detailed documentation on Git commands and usage to deepen your understanding.

