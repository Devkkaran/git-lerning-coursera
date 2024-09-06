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

# 4. Git branches and merging

### Git Branch Commands

1. **List Branches**
   - Command: `$ git branch`
   - **Explanation:** Lists all branches in your repository, highlighting the current branch.

2. **Create a New Branch**
   - Command: `$ git branch <name>`
   - **Explanation:** Creates a new branch called `<name>`.

3. **Delete a Branch**
   - Command: `$ git branch -d <name>`
   - **Explanation:** Deletes the branch `<name>`. This will fail if the branch contains changes that haven’t been merged.

4. **Force Delete a Branch**
   - Command: `$ git branch -D <name>`
   - **Explanation:** Forcefully deletes the branch `<name>` even if it contains unmerged changes.

### Git Checkout Commands

5. **Switch to a Branch**
   - Command: `$ git checkout <branch>`
   - **Explanation:** Switches your working directory to the branch `<branch>`.

6. **Create and Switch to a New Branch**
   - Command: `$ git checkout -b <new-branch>`
   - **Explanation:** Creates a new branch called `<new-branch>` and switches to it immediately.

### Git Merge Commands

7. **Merge a Branch**
   - Command: `$ git merge <branch>`
   - **Explanation:** Merges changes from `<branch>` into your current branch.

8. **Abort a Merge**
   - Command: `$ git merge --abort`
   - **Explanation:** Aborts a merge in progress and returns the branch to its state before the merge started. This is useful if there are conflicts during the merge.

### Git Log Commands

9. **Visualize Commit History**
   - Command: `$ git log --graph`
   - **Explanation:** Displays an ASCII graph of the commit history, showing branches and merges.

10. **View Commit History in Oneline Format**
    - Command: `$ git log --oneline`
    - **Explanation:** Displays a concise, one-line summary of each commit.

### Practical Usage

- **Creating a Feature Branch:**
  ```bash
  git branch feature-x
  git checkout feature-x
  ```

- **Merging Changes from `feature-x` to `main`:**
  ```bash
  git checkout main
  git merge feature-x
  ```

- **Deleting `feature-x` After Merging:**
  ```bash
  git branch -d feature-x
  ```

### Tips

- **Always Make Sure to be on the Correct Branch:** Before performing operations like merging or deleting branches, ensure you’re on the branch you intend to work with.
  
- **Use Git Log:** Commands like `$ git log --oneline` and `$ git log --graph` are very useful for visualizing what’s happening in your repository, especially when dealing with multiple branches.

This guide will definitely help you efficiently manage branches and merges in Git!

# 5. Git Remote Commands Overview

| Command                | Explanation                                                                                          |
|------------------------|------------------------------------------------------------------------------------------------------|
| `git remote`           | Allows you to manage the set of repositories or “remotes” whose branches you track.                   |
| `git remote -v`        | Similar to `git remote`, but adding the `-v` shows more information such as the remote URL.           |
| `git remote show <name>`| Shows some information about a single remote repo.                                                   |
| `git remote update`    | Fetches updates for remotes or remote groups.                                                        |
| `git fetch`            | Can download objects and refs from a single repo, a single URL, or from several repositories at once. |
| `git branch -r`        | Lists remote branches and can be combined with other branch arguments to manage remote branches.      |


- **Scope**:
  - `git fetch` updates branches from a specific remote (or the default remote if no remote is specified).
  - `git remote update` updates branches from all remotes configured in your repository.

- **Usage Context**:
  - Use `git fetch` when you want to update from a specific remote, or when you’re working with a single remote (e.g., `origin`).
  - Use `git remote update` when you want to ensure all your remote-tracking branches are up-to-date with all remotes configured in your repository.

So, while `git fetch` can achieve similar results if used with the default remote, `git remote update` is more comprehensive in updating all configured remotes.

# 6. SSH protocol and how it works:

### What is SSH?
- **SSH (Secure Shell)** is a way to securely connect to a computer or server over the internet. It’s like a secure tunnel that keeps your data safe while you work on another machine.
  
### What is a Protocol?
- A **protocol** is a set of rules that computers follow to communicate with each other, similar to how we follow rules when talking to others. For computers, these protocols ensure that any device that follows the same set of rules can talk to each other.

### How SSH Protects Data
SSH uses something called **public-key encryption** to secure communication between your computer (client) and the server. Here's how it works:
1. **Encryption Keys**: When you connect to a server using SSH, both your computer and the server create special encryption keys. These keys ensure that any data passed between them is encrypted (hidden from others).
2. **Public and Private Keys**: 
   - **Public Key**: This is shared with everyone and is used to lock (encrypt) the message.
   - **Private Key**: This is kept secret by the server and is used to unlock (decrypt) the message.
3. **How It Works**: When you send data (like commands) to the server, your computer encrypts it using the public key. Only the server with the private key can decrypt it, so even if someone intercepts the data, they can’t read it.

### Uses of SSH
1. **Remote Login**: SSH is mostly used to log into remote servers (especially Linux/Unix servers). This means you can control a server from anywhere securely.
2. **File Transfers**: You can also use SSH to transfer files securely between your computer and the server using tools like **SCP** (Secure Copy Protocol) or **SFTP** (Secure File Transfer Protocol).
3. **Port Forwarding (Tunneling)**: You can use SSH to securely connect to services on a remote server by forwarding specific network ports.
4. **Jump Servers**: If you need to access servers behind a firewall, SSH can be used to first connect to a "jump server" (like a gateway) before accessing other servers.
5. **Running GUI Applications**: If you're running a program with a graphical interface on a server, you can display it on your local machine using **X forwarding**.

### Key Points:
- **SSH secures remote connections** so no one can see what you're typing or transferring.
- **Public and private keys** are used to ensure that only you and the server can read the messages.
- SSH is used for **remote login**, **file transfers**, and **tunneling** to make sure all your communication is safe.

I hope this clears things up!


# 7. SSH configuration process:

### 1. **What is SSH?**
SSH is a secure way to connect to another computer or server over the internet. It ensures that no one can see what you're doing while you're connected.

### 2. **Connecting through a Port**
- Every computer has **ports**, which are like doors that allow network traffic to come in and go out.
- SSH uses **port 22** by default to connect your computer (the client) to a remote server.

### 3. **How the Connection Works**
When you connect to a server using SSH:
1. **The Server Sends its Public Key**: This is like a lock the server gives you to secure communication.
2. **You Agree on Encryption Rules**: Both the client and server agree on a way to keep the data safe.
3. **A Secure Shell (Login) is Started**: Once everything is set, the server opens up a secure way for you to control it remotely.

### 4. **Generating Your SSH Key**
Before you connect to a server, you need a **public/private key pair**. Here’s how to create one:
- **Public Key**: This is shared with the server to encrypt your data.
- **Private Key**: This stays with you and is used to decrypt data from the server.

To create these keys:
- You open a terminal and type: `ssh-keygen -t rsa -b 2048`
  - This generates a pair of keys.
  - The keys are saved in a hidden folder called `.ssh` in your home directory.
  - SSH may ask if you want to add a **passphrase** for extra security (like a password). If you add a passphrase, you’ll need to enter it every time you use the key.

### 5. **Connecting for the First Time**
Once your key pair is ready:
- You connect by typing: `ssh <username>@<hostname>`.
  - **Username**: Your login name on the server.
  - **Hostname**: The address of the server (like `192.168.1.10` or `example.com`).
  
When you connect for the first time:
- SSH will show the **server’s fingerprint** (a unique identifier) and ask if you trust it. If you say yes, the server’s key is saved on your machine for future use.
- If the server key ever changes, SSH will warn you, as this might mean something suspicious is happening.

### 6. **SSH Server Setup**
On the server side:
- An SSH **daemon** (a program running in the background) listens on **port 22** for incoming connections.
- If you get errors like “**connection refused**,” it may mean the SSH server is not running.

### 7. **Useful Tips**
- You can copy your SSH key pair to all the devices you use (like your laptop, tablet, etc.), so you don’t have to create new keys for each device.
- If SSH warns you that the server’s key has changed, it might be a sign of a security issue. Contact the server admin to be sure.

### 8. **Optional Features**
SSH has extra features like **port forwarding**, which lets you access blocked services. These features are usually turned off for security reasons but can be enabled in the server’s configuration file if needed.

### Summary
SSH lets you securely connect to a server by using encryption. You create keys to authenticate yourself and can manage your server remotely. Once everything is set up, SSH keeps your connection safe.


# 8. API keys and how they work:

### 1. **What is an API Key?**
- An **API key** is like a password for programs to access and use a service (called an API). 
- When a program sends a request to an API, it includes the API key to prove who is making the request and what they are allowed to do.

### 2. **Why are API Keys Important?**
- API keys help to make sure that:
  - **Authentication**: The request comes from the right person or application.
  - **Authorization**: The person or app making the request is allowed to use specific parts of the API.

### 3. **How API Keys Work**
- Every time a program sends a request to the API, it must include the API key.
- API keys are often randomly generated and act as a **secure token** to identify the program or user making the call.

### 4. **How to Use API Keys**
When using APIs, the key can be sent in a few different ways:
1. **In the URL** (as a parameter in the web address):
   ``` 
   GET https://myapp.com/api/users/list?apikey=12345678
   ```
2. **In the HTTP header** (a hidden part of the request):
   ``` 
   GET https://myapp.com/api/users/list
   X-API-Key: 12345678
   ```
3. **In a POST request** to an authorization endpoint, which may return another token for future requests:
   ```
   POST https://myapp.com/api/auth
   { "token": "12345678" }
   ```

### 5. **Security Tips**
- **Don’t hardcode** API keys in your app's code, especially if it’s public (like on GitHub). If someone finds it, they can use your key and access the API with your permissions.
- For better security, many apps are now using **OAuth** instead of API keys. OAuth makes users manually approve the app before it can access the API.

### 6. **Key Points**
- API keys let apps interact with APIs safely, ensuring only authorized apps or users can make certain API calls.
- Always handle API keys carefully, and don’t leave them in your code where others can easily find them.

In short, API keys are used to keep API communication secure by checking who is making the request and what they’re allowed to do.


## Public and private keys and how they work together for security:

### 1. **What is a Public Key?**
- A **public key** is like a lock that anyone can use to secure information they send to you. 
- It’s used to **encrypt data** (make it unreadable) or to check if a digital signature (like a virtual stamp) is real.
- Public keys are available to anyone, but they are trusted because they come from a verified source, like a **certificate authority** (a trusted third party).

### 2. **What is a Private Key?**
- A **private key** is like the key to the lock — it’s **secret** and only you should have it.
- It’s used to **decrypt data** (make it readable again) or to create digital signatures that verify the message really came from you.
- **Never share your private key** with anyone else.

### 3. **How Do Public and Private Keys Work Together?**
Public and private keys work as a pair to keep communication secure. Here’s the basic process:

1. **Key generation**: Both the sender and the receiver get a pair of keys (public and private).
2. **Key exchange**: The sender and receiver **share** their public keys with each other.
3. **Encryption**: The sender **encrypts** the message using the receiver's public key.
4. **Send the message**: The encrypted message is sent to the receiver.
5. **Decryption**: The receiver uses their **private key** to decrypt (unlock) the message and read it.

### 4. **Key Takeaway**
- Public keys and private keys are like a **lock** and **key** that work together to keep data safe.
- The **public key** is used to **lock** (encrypt) the data, and the **private key** is used to **unlock** (decrypt) it.
- This process ensures that data is secure and that no one can tamper with it during transmission.

By using both types of keys, we can ensure that communications stay confidential and secure.
