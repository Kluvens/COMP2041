# Git
git is a version control system(VCS) - track changes to a file or set of files over time
so that you can recall specific versions later

git is open source under the GPLv2 licence
- git repo
- created for and still used by Linus Torvalds for the linux kernel

VCS terminology:
- Repository (repo)
- braches
- tags
- commits

Many VCSs use the notion of a repository
- store all versions of all objects (files) managed by VCS
- may be single file, directory tree, database
- possibly accessed by filesystem, http, ssh or custom protocol
- possibly structured as a collection of projects

## Git repository
git uses the sub-directory ```.git``` to store the repository
Inside .git there are:
- Object IDs are hashes- objects can be: a blob, a tree, a commit
- Blobs are file contents - no file names, permissions, linkes etc
- Trees are directory listings - model the file system. this is where: file names, permissions, links etc live. trees can point to other trees to store subdirectories
- commits are snapshots - represents the state of the working directory at a particular time and has a list of parent commits
- branches provide pointers to the commits

Some of the best known Git repo hosting services
- github
- gitlab
- bitbucket

Why Git?
- distributed VCS - multiple repositories, no oracle
- every user has their own repository
- created by Linus Torvalds for Linux kernel
- external revisions imported as new branches
- flexible handling of branching
- various auto-merging algorithms
- not better than competitors but better supoorted/more widely used
- at first stick with a small subset of commands
- substantial time investment to learn to use Git's full power

## SSH keys
What they are:
- a form of public/private key cryptography
- you share the public key
- you keep the private key

What they are used for:
- encryption
- signing
- authentication

How they work on UNIX systems:
- stored in ```~/.ssh/```
- created by ssh-keygen
- used by many programs

## ssh-keygen
Common flags:
- -t type of key: rsa, ed25519, ecdsa
- -a number of rounds, larger number = harder to rack
- -b number of bits in the key
- -f filename of the private key file
- -C add a comment (usaully an email address and/or description)
- -P add a passphrase (better to use stdin)

## git commands
The GIG 7:
- git init <repo> or git clone <repoURL>
- git status
- git add <file>
- git commit -m "message"
- git pull
- git push
 
The others
- git branch <branch>
- git checkout <branch>
- git fetch
- git log
- git stash
