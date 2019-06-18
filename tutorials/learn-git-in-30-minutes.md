# Learn Git in 30 Minutes

​	

**Introduction**

**Configure Git**

**Git Clone**

**Git Add**

**Git Commit**

**Git push**

**Git pull**

**Branching**

**Merging**

**Using GUI -PHP Storm**

**Conflict**



***Introduction***

- Git is a collection of command line utilities that track and record changes in files.
- With it you can restore old versions of your project, compare, analyse, merge changes and more. 
- This process is referred to as **version control**. 
- Git is decentralized, which means that it doesn't depend on a central server to keep old versions of your files. 
- Instead it works fully locally by storing this data as a folder on your hard drive, which we call a **repository**. 
- However you can store a copy of your repository online, which makes it easy for multiple people to collaborate and work on the same code. 
- Git Hub is used for this purpose.



***Git Clone***

- If a project has already been set up in a central repository, the `git clone` command is the most common way for users to obtain a development copy. 
- Cloning is generally a one-time operation. 
- Once a developer has obtained a working copy, all version control operations and collaborations are managed through their local repository.

***Steps***

1. Access the link "https://github.com/codexten/docs"

2. Click on "clone or download"

3. Click to choose "use SSH"

4. Copy the text "git@github.com:codexten/docs.git"

5. Access Terminal: Ctl+Alt+T

6. type the command 

   ```
   git clone git@github.com:codexten/docs.git
   ```

7. Type "yes" and enter.

   

***Git Add***

- You want to start keeping track of all your space station locations. 

- To do so, let's create a file about all your locations.

- The file is un-tracked, meaning that Git sees a file not part of a previous commit.

- Tell Git to track your new `locations.txt` file using the `git add` command. 

- Just like when you created a file, the `git add` command doesn't return anything when you enter it correctly.

- We can add all the changes you made using the following git add command.

  ```
  git add .
  ```

- This command adds all the additional files.

- When we add a particular file, we use the following type of command.

  ```
  git add locations.txt
  ```

  

***Steps***

1. Open terminal (Ctl+Alt+T)

2. Choose to move to the directory you are working on.

   ```
   cd docs
   cd software-testing
   ```

3. Type the git add command.

   ```
   git add .
   ```

   

***Git Commit***

- The word commit itself quotes the meaning.

- Here we save the changes made using git commit command.

- The following command shows how to commit the changes made.

  ```
  git commit -m 'init'
  ```

- The -m indicates that a commit message follows.

- 'init' is the commit message given in the above command.

- The `git commit` takes the staged snapshot and commits it to the project history. 

  

***Steps***

1. Open terminal (Ctl+Alt+T)

2. Choose to move to the directory you are working on.

   ```
   cd docs
   cd software-testing
   ```

3. Type the git add command if any new files are added.

   ```
   git add .
   ```

4. Type git commit command to save the changes so far.

   ```
   git commit -m 'init'
   ```

   