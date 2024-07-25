Configuring IntelliJ with Bitbucket using SSH Key
Step 1: Generate an SSH Key
Open a Terminal (Command Prompt or Git Bash on Windows).
Generate a new SSH key using the command:
sh
Copy code
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
Save the key when prompted. You can use the default location.
Enter a passphrase (optional but recommended).
Step 2: Add the SSH Key to the SSH Agent
Start the SSH agent:
sh
Copy code
eval "$(ssh-agent -s)"
Add your SSH private key to the SSH agent:
sh
Copy code
ssh-add ~/.ssh/id_rsa
Step 3: Add the SSH Key to Bitbucket
Log in to your Bitbucket account.
Go to Bitbucket settings.
Under the Security section, click on SSH keys.
Click "Add key".
Copy your SSH public key to the clipboard:
sh
Copy code
cat ~/.ssh/id_rsa.pub
Paste the key into the SSH key field on Bitbucket and save it.
Step 4: Clone a Repository from Bitbucket in IntelliJ
Open IntelliJ IDEA.
Go to File > New > Project from Version Control > Git.
Enter the Bitbucket SSH URL of your repository (e.g., git@bitbucket.org:username/repository.git).
Click "Clone".
Step 5: Configure SSH in IntelliJ
Go to File > Settings (or Preferences on macOS) > Version Control > Git.
Ensure the Path to Git executable is correctly set.
Click on Test to verify the connection.
Go to File > Settings (or Preferences on macOS) > Tools > SSH Terminal.
Ensure the SSH executable is set to Native.
Step 6: Verify Configuration
Open the Terminal in IntelliJ (View > Tool Windows > Terminal).
Test your connection by running:
sh
Copy code
ssh -T git@bitbucket.org
You should see a success message indicating you've authenticated successfully.
