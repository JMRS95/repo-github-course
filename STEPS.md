# Learn the basic git STEPS

## Basic git commands
1. **Configure your folder to git**
```bash
git init
```

2. **Add a file for git to track it**
```bash
git add <Your file(s)> <Your directory(ies)\>`
```

3. **Commit to confirm the changes**
```bash
git commit -m "Your commit message"
```

4. If you want **git to untrack a file and have NOT commited yet**
```bash
git restore --staged <Your file(s)> <Your directory(ies)\>
```

5. If it **has been commited:**
```bash
git rm --cached <Your file(s)> <Your directory(ies)\>
```

## Configure github with SSH


**Linux only**:
1. Install SSH
```bash
sudo apt update
```
```bash
sudo apt install openssh-client
```

2. Create a new directory for ssh in your computer:
```bash
mkdir -p ~/.ssh
```

3. Tell github you are the owner of the repository using SSH:
```bash
ssh-keygen -t rsa -b 4096 -C <yourmail@gmail.com>
```

4. It will ask you to generate a key (suggested): Enter it.
Next. it will generate:
- A `testkey` file
- A `testkey.pub` file (Private key --> **Keep it safe**)

5. Every time you want to connect/push/use account with your local machine you
must use your private key. You must **copy the key contained in your testkey.pub**\
- Copy the contents of your `testkey.pub` file (If Visual Studio is used just use
Ctrl+C on the line.)\

6. Go to your []https://github.com/ profile and **save your key**:\
The steps are:\
github.com: Your_Profile -> Settings -> SSH-GPG keys (Left side) -> New SSH key.\

7. Enter your Key in Github:
- Title: Whatever title you want. 
- Key type: I used 'Authentication type'
- Key: Enter your *passphrase*. You **must remember this passphrase or save it in a safe place**\

8. **(Extra)** In your computer, in case you accidentaly created your key in another directory,
move it to the ~/.ssh folder in your system:
```bash
mv <Your folder>/testkey ~/.ssh/
```
```bash
mv <Your folder>/testkey.pub ~/.ssh/
```

Or copy if prefered, in that case use cp instead of mv.
(Keep in mind that this file must be located in a SECURE place)
```bash
cp <Your folder>/testkey ~/.ssh/`
```
```bash
cp <Your folder>/testkey.pub ~/.ssh/
```

9. Change permissons to your testkey in your ssh directory.
```bash
chmod 600 ~/.ssh/testkey
```
```bash
chmod 644 ~/.ssh/testkey.pub
```
```bash
chmod 700 ~/.ssh
```

10. Start you SSH agent if not running:
```bash
eval "$(ssh-agent -s)"
```

11. Add your key
```bash
ssh-add ~/.ssh/testkey
```

12.  Requires you to **enter your passphrase** (Step 7.) with github\
(DON'T FORGET IT OR SAVE IT IN A SECURE PLACE.) 

13. Open your ssh config file
```bash
nano ~/.ssh/config
```

14. Paste this in your file:
```bash
Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/testkey
```

15. Now push your changes
```bash
git push origin main
``

