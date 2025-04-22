By groups of two, you play the role of Alice and Bob, two biologists who want to code an ambitious R project to be able to add two integers. The tutorial is split in two scenarios that allow to present basic and intermediate functionalities of version control with git coupled with sharing with GitHub. It is voluntarily focused on *collaboration*, meaning that basic git operations that are typically also done in single-user projects are introduced in a collaborative context.

Don't panic.

Start by deciding who plays who. For context, Alice is an experienced ecologist, that has been working for longer than Bob, whose main project currently is the task of adding two numbers (mirroring a supervisor/student pair). Because of a lack of available office space in Alice's institute, Alice and Bob do not work in the same building and therefore can't share code in person via USB sticks. The university e-mail server is also broken: they can't share code via email. They HAVE to use GitHub.

 - :golf: Course of the scenario
 - :computer: Activity to do on your computers
 - :clipboard: Definition or technical explanation

# Scenario 0 : Starting the tutorial

 - `fork`, `clone`
 - inviting collaborators to a project
 
:golf: Bob searched the internet for existing projects and found one project that looks like a good place to start from. It's this tutorial's page !

:computer: Connected to their GitHub account, they `fork` the repository: it creates an identical repository in Bob's personnal account. Bob adds Alice's GitHub account as collaborator to their fork, via Settings > Collaborators > Add people.

:computer: With Rstudio, you can `clone` the repository : importe the code files and the git project on your personal computer in a dedicated folder. File > New Project > Version control > Git: fill in Bob's fork URL and create the project.

Alice and Bob clone the project on their two computers.

# Scenario 1 : adding modifications, one person at a time

:golf: Bob (wisely) decides to develop the project step-by-step and starts by writing a function to add 2 to any number. After writing the function, Bob wants to share it with Alice.

## 1a - record changes with git, share them

- create a commit with `add` and `commit`
- publish your commits to the remote server via `push` and import them with `pull`

:computer: Bob writes the new "add_two" function in, saves the file and adds the change to staging with `git add` (check the "Staged" box in the Rstudio Git panel). Once Bob is satisfied with the update, they can `commit` the changes : click on "commit" in the Git panel, write an informative commit message and click on commit. The changes are now tracked in Bob's local git project.

:computer: Bob shares the commit(s) with Alice : click on `push` to publish the local commits on GitHub. To see the new version, Alice clicks on `pull`. Check that the code on Alice's computer now matches the modifications the Bob `commit`ed and  `push`ed.

:computer: What if Alice wants to add a comment to the new code ? After `pull`ing Bob's changes, Alice can make new changes, for example adding a comment, `add` the file, `commit` the change, and `push` it.

## 1b - falling back to older versions

- `log`, `checkout`

:golf: The next day, Bob realises that there is probably a better solution for the project than to manually write a function for each integer that could possibly be added.

:computer: Bob checks the commit history (also called `git log`, History button in the Git panel), and Bob can click on the commit before the commit where they added the new function. Click on "view file": you can see the file as it was before ! The weird characters next to "view file" are the `commit hash`: they uniquely idendify each commit in the project. Bob can copy-paste the old version and paste it in place of the new one.

:clipboard: Alternatively, typing `git revert <hash>` creates a commits that cancels the changes of the given commit. Reverting several commits at once is possible with `git revert <hash1> <hash2> <hash3>`.

# Scenario 2: adding changes at the same time: working with several branches

:golf: Some time later, Bob is almost done with the project ! They created (at least) two new commits, where Bob created a new function that adds two numbers. They also added lines in main.R to try out some additions.

:computer: Do these changes, create `commit`s, `push` them and `pull` the new version on Alice's computer.

## 2a - create branches and navigate between them

- `branch`, `checkout`

:golf: After a few tests, Bob realises that their function is not very computationally efficient and wants to improve it. However, Alice needs the existing version to stay available on GitHub because she's leaving for a seminar where she wants to show other people how to add integers. She also wants to be able to add more example to main.R.

:clipboard: Working with alternative versions of the project requires `branches`: a branch is a reference to a commit. You can see the branch you are currently working on in the top-right of the git panel, next to the refresh icon. Alice and Bob were actually on branch main all this time ! While "on branch main", every new commit updates the "main" branch to point to that new commit. 

:computer: Alice and Bob agree that they will work on two separate branches : Alice creates a branch (git panel > new branch), called "alice-examples" and commit new examples on this branch. Be sure to tick "Sync branch with remote" so that the new branch is also created on GitHub. Bob creates a branch called "bob-optim" and commits an optimized version of their function there.

:computer: Alice can thus work on their new examples in main.R while using the old version of R/functions.R and `push` them, while Bob can work on their optimisation in R/main.R and `push` them. Compare the state of the project between Alice's computer, Bob's computer, the "alice-examples", "main" and "bob-optim" branches on GitHub.

## 2b - rassembler des branches localement

- `merge`

## 2c - rassembler des branches avec GitHub

- comparer des branches publiées grâce aux Pull Requests
