# Git and GitHub initialization

This is a description of how to initialize Git using Terminal of text editor, in this case VS Code.

## Table of Contents
- [Version control]
- [Difference between Git and GitHub]
- [GitHub alternatives]
- [Difference beween git fetch and git pull]
- [Git rebase explained]

## Version control
Version control is a system that records changes to a set of files over time, allowing multiple contributors to collaborate on a project.
The two main types of version control systems are centralized and distributed. In a centralized system, there is a single, centralized repository that users connect to. 
In a distributed system, each user has a complete copy of the repository, which allows for more flexibility in collaboration and offline work.
Popular version control systems include Git (distributed), Mercurial (distributed), and Subversion (centralized). Git, in particular, is widely used in the software development community and has become the standard for version control in many projects.
The primary goal of version control is to manage and track changes systematically, enabling developers to:

1. Track Changes: Version control systems (VCS) keep a historical record of changes made to files. Each change is associated with a timestamp, author, and a description of the modification.

2. Collaborate: Multiple contributors can work on the same project simultaneously. Version control helps manage conflicts that may arise when different people make changes to the same file.

3. Revert to Previous States: If a mistake is made or an undesirable change occurs, developers can easily revert back to a previous state of the project. This is particularly useful for undoing changes and troubleshooting issues.

4. Branching and Merging: Version control allows developers to create branches, which are isolated environments for making changes without affecting the main project. Branches can later be merged to incorporate changes into the main branch.

5. Backup and Recovery: By maintaining a history of changes, version control systems serve as a backup mechanism. Even if data is lost or corrupted, it can often be recovered from the version control system.

6. Documentation: Version control systems provide a detailed log of changes, helping developers understand the evolution of the project. This serves as documentation for the project's history.


## Difference between Git and GitHub 
Git is the version control system itself, and it is used for tracking changes locally on a developer's machine. GitHub is a web-based platform that hosts Git repositories and provides collaboration tools, making it easier for teams to work together on projects.
Git is a distributed version control system (DVCS) designed for tracking changes in source code during software development.
It allows developers to work on a project collaboratively, tracking changes, creating branches, and merging code seamlessly. Git operates locally on a user's machine, which means that each developer has their own copy of the entire project history.
The majore features of git include branching, merging, commit history, local repositories.
While Git can be used without GitHub, GitHub leverages the capabilities of Git to enhance collaboration and project management in a centralized, web-based environment. Other similar services exist, such as GitLab and Bitbucket, each with its own features and advantages.
GitHub is a web-based platform that provides hosting for Git repositories. It adds a web-based interface and additional features on top of Git to facilitate collaboration.
GitHub serves as a central hub for projects using Git. It allows multiple developers to work on a project concurrently, provides a graphical interface for Git repositories, and includes features like issue tracking, pull requests, and project management tools.
And it's major key features are remote hosting of Git repositories, collaboration tools, issue tracking, pull requests, project management.


##Alternatives to GitHub
1. Bitbucket
2. GitLab
3. SourceForge

##Difference beween git fetch and git pull
'git fetch' retrieves the latest changes from the remote repository but does not automatically merge them into your working branch. 
It only updates the remote-tracking branches in your local repository. After running git fetch, you can inspect the changes fetched from the remote using commands like git log origin/main to view the commit history on the remote's main branch.
'git pull' is a combination of two actions: git fetch followed by git merge. 
It fetches the changes from the remote repository and then automatically merges them into the current working branch. Running git pull is a quick way to bring the latest changes from the remote into your working branch. 
It's a more straightforward command for updating your local branch with the changes on the remote.
Therefore, if you want to see the changes from the remote repository and decide how to integrate them manually, use 'git fetch'. If you want to quickly fetch and merge changes into your working branch, use 'git pull'.

##Git rebase
git rebase is a Git command used to reapply a series of commits on top of another commit or branch. Unlike git merge, which integrates changes from one branch into another, git rebase modifies the commit history itself. 
It's a powerful but potentially risky operation that should be used with care, especially on shared branches. While git rebase is a powerful tool, it should be used judiciously, especially in collaborative environments. 
It alters commit history, which can make collaboration more challenging if not done carefully. Avoid rebasing commits that have already been pushed to a shared branch, as it can cause conflicts for other collaborators who have pulled the previous version of the branch.
It is typically recommended to use git rebase on local branches before pushing changes to a shared repository to avoid disrupting other contributors.
git rebase workflow is as follows:
1. to start a rebase: This command tells Git to reapply the changes in the feature-branch on top of the main branch.
   git checkout feature-branch
   git rebase main
2. updating a branch: This ensures your local branch is up-to-date with the remote repository.
   git checkout feature-branch
   git pull origin feature-branch
3. resolving conflict: If there are conflicts during the rebase, Git will pause and allow you to resolve them. After resolving conflicts, you continue the rebase with:
   git rebase --continue

5. finishing a rebase: Once the rebase is complete, your local branch will have a new commit history, and it will be up-to-date with the latest changes from the main branch.
Using '--force' is necessary because the commit history has been rewritten, and the remote branch needs to be updated with the rewritten history.
   git push origin feature-branch --force

##Git cherry-pick
Git cherry-pick is a Git command that allows you to copy a specific commit from one branch and apply it onto another branch. It's useful when you want to selectively bring changes from one branch into another. 
Git cherry-pick is a powerful command, but it can result in conflicts if the changes being cherry-picked conflict with the current state of the target branch. In such cases, you may need to resolve conflicts manually. The command syntax is as follows;
   git cherry-pick <commit-hash> 
   where <commit-hash> is the identifier (hash) of the commit you want to cherry-pick.
For example; if you have a branch called develop with a commit you want to bring into your current branch (main). If the commit hash is, for example, agbadev2024:
1. Switch to the target branch (main)
git checkout main
2. Cherry-pick the specific commit from feature-branch
git cherry-pick agbadev2024
