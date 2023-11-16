# 1. Codebase
A single codebase tracked in version control, deployable in multiple stages (development, staging, production), with each deployment using the same codebase but with different configurations.

## Best Practices
### 1. Use Version Control Systems like Git
* **Initializing a Repository:** Start by creating a new Git repository for your project.
  <br> For example, `git init` initializes a new Git repository in your project folder.
* **Committing Changes:** Regularly commit changes to track the evolution of your codebase.
  <br> For instance, after editing files, use `git add .` to stage changes and `git commit -m "Your commit message"` to commit them.
* **Remote Repositories:** Push your code to a remote repository (like GitHub, GitLab, Bitbucket) for backup and collaboration. 
  <br> `git remote add origin [repository URL]` adds a remote repository, and `git push -u origin master` pushes your code to it.

### 2. Maintain a Single Repository for Each Microservice in a Microservices Architecture
* **Separate Repositories for Each Service:** If your application is composed of multiple services (e.g., `user service`, `order service`, `inventory service`), each should have its own Git repository. 
<br> This isolation simplifies version control and continuous integration/deployment (`CI/CD`) processes for each microservice.
* **Versioning Microservices:** Use semantic versioning for each microservice repository to track changes and updates independently. 
<br> For example, incrementing major, minor, or patch versions based on the nature of changes.

### 3. Implement Branching Strategies

* **Feature Branching:** Create a new branch for each new feature. For example, `git checkout -b feature/user-authentication` creates and switches to a new branch for developing a user authentication feature. Merge this branch back into the main branch upon completion.
* **Gitflow Workflow:** A robust branching model for managing releases. It involves maintaining two main branches (`master` for releases and `develop` for development), along with `feature`, `release`, and `hotfix` branches. 
<br> For instance, start a new feature branch from develop, merge it back after completion, and eventually merge develop into master for a release.

#### Gitflow Example Workflow:

* **Start a new feature:** `git checkout develop` then `git checkout -b feature/new-feature`
* **Finish the feature:** `git checkout develop` then `git merge feature/new-feature`
* **Prepare a release:** `git checkout -b release/1.0.0 develop` for final adjustments, then `git checkout master` and `git merge release/1.0.0`
* **Hotfixes:** `git checkout -b hotfix/urgent-fix master`, fix the issue, then merge back into both master and develop.

By adhering to these practices, you ensure that your codebase remains organized, scalable, and conducive to collaborative development, especially vital in complex projects or microservices architectures.
