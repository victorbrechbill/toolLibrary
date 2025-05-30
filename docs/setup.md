This guide will help you download (or "clone") this project from GitHub to your own computer using only the built-in Windows Command Prompt. No coding knowledge required.

✅ What You’ll Need
A GitHub account (free): https://github.com

Git installed on your PC: Download Git for Windows

📦 Step 1: Install Git
If you don’t already have Git installed:

Go to https://git-scm.com/download/win

Download and install it (you can accept all the default options).

After installing, open Command Prompt (cmd.exe) and type:

css
Copy
Edit
git --version
If it prints something like git version 2.x.x, you’re good to go!

🔐 Step 2: Set Up SSH Access
GitHub needs to know it's you when you clone the project. To do this securely, we use something called an SSH key.

A. Create an SSH key (just once)
Open Command Prompt

Type this command and press Enter:

perl
Copy
Edit
ssh-keygen -t ed25519 -C "your_email@example.com"
When asked where to save the file, just press Enter

If it asks for a passphrase, you can leave it empty and press Enter twice

B. Add the key to your GitHub account
Type this to show your key:

rust
Copy
Edit
type %userprofile%\.ssh\id_ed25519.pub
Copy the entire output

Go to https://github.com/settings/keys

Click “New SSH key”, give it a name (like "My Laptop"), and paste the key

📂 Step 3: Clone the Project
Once your SSH key is added:

In Command Prompt, go to the folder where you want to save the project:

bash
Copy
Edit
cd C:\Users\YourName\Documents
Then run this (replace with the actual repo name):

bash
Copy
Edit
git clone git@github.com:your-username/your-repo-name.git
✅ That’s it! You now have a copy of the project on your computer.