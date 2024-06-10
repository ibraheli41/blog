Yang biasa digunakan

```shell
git init #initialize an existing directory as Git Repo
git clone [url] #copy or download entire Repo via URL

git add . #add recent directory to stage
git commit -m "[description]" #staged content as a new commit snapshot
git push #upload to git repository
```

# Instalasi Git

###### Windows ->  download github for windows
###### Linux Ubuntu -> `sudo apt-get install git`
###### MacOS ->  `brew install git`

# Setup

```sh
git config --global user.name “[firstname lastname]”
git config --global user.email “[valid-email]”
git config --global color.ui auto
```

# Setup & Init

```sh
git init
git clone [url]
```

# Stage & Snapshot

```sh
git status
git add [file]
git reset [file]
git diff
git diff --staged
git commit -m “[descriptive message]”
```

# Branch & Merge

Branch = Percabangan 
fungsi diciptakan branch ->
misal ingin membuat ecommer. tapi kita tidak mungkin untuk menunggu kodingan dari yang lain selesai. Maka dari itu kita kerja dengan environment terpisah supaya tidak mengganggu kodingan lain. Misal ingin membuat fitur login maka kita perlu membuat branch berjudul login dan lain sebagainya.


```sh
git branch
git branch [branch-name]
git checkout
git merge [branch]
git switch
git log
```

# Inspect & Compare

```sh
git log
git log branchB..branchA
git log --follow [file]
git diff branchB...branchA
git show [SHA]
```

# Tracking Path Changes
```sh
git rm [file]
git mv [existing-path] [new-path]
git log --stat -M
```

# Ignoring Patterns
```sh
logs/
*.notes
pattern*/

git config --global core.excludesfile [file]
```

# Share & Update

```sh
git remote add [alias] [url]
git fetch [alias]
git merge [alias]/[branch]
git push [alias] [branch]
git pull
```

# Rewrite History

```sh
git rebase [branch]
git reset --hard [commit]
```

# Temporary Commits

```sh
git stash
git stash list
git stash pop
git stash drop
```












### Terminologi

Git
Repositori
Commit
Branch
Email github

### Sumber Referensi

training.github.com

# Successful Git Branching Model

![[Pasted image 20240610121637.png]]