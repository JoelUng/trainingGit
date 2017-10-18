# How to initialize a Git project

## Git global setup

```git
git config --global user.name "FirstName LastName"
git config --global user.email "your@email.com"
```
---

## Create the git project from github or gitlab

Execute the interactive steps from your favorite's git website.
It will display the command to execute on your local computer :

```git
git clone https://website.host/yourproject.git
cd yourproject
touch README.md
git add README.md
git commit -m "docs: add README"
git push -u origin master
```
---

## Add a existing project to gitlab or github

After created a git project on the website, you can add your existing project to git :

```git
cd "existing_folder"
git init
git remote add origin https://srisvm-vcs20.isocel.info/joel.ung/git-init.git
git add .
git commit
git push -u origin master
```