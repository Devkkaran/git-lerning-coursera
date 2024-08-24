# It is About Git Commit MSG how we type MSG in RIght Way
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