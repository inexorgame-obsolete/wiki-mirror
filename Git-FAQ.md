# Submodule FAQ:

* How can I create a submodule?
* [Someone else has updated a submodule on the origin (read: GitHub). How can I get the latest version?](#someone-else-has-updated-a-submodule-on-the-origin-read-github-how-can-i-get-the-latest-version)
* [How can I update a submodule on the origin?](#how-can-i-update-a-submodule-on-the-origin)
* [I get the error "fatal: reference is not a tree". What can I do?](#i-get-the-error-fatal-reference-is-not-a-tree-what-can-i-do)

***

##### Someone else has updated a submodule on the origin (read: GitHub). How can I get the latest version?

1. Pull the latest version of the repository.
2. Enter in the Git shell: `git submodule update`

##### How can I update a submodule on the origin?
Preconditions: You have pushed a new commit to a repository, which is getting used as a submodule.

1. Go to the repository, which uses the submodule.
2. Switch to the directory in which the submodule is located. To do this, enter `cd your/path/to/the/submodule`
3. Now execute: `git checkout` and `git pull`
4. Go back to the root directory of the repository (you can go one directory level up with `cd ..`).
5. Create a commit (`git commit -m "Update submodules"`)

##### I get the error "fatal: reference is not a tree". What can I do?
When this is happening the current initialized submodule repository is invalid. Possible scenarios: The repository is moved or deleted.

1. Execute: `git submodule deinit`
2. Pull the latest version of the repository.
3. Execute: `git submodule sync` (this refreshes the submodule URL and branch)
4. Execute: `git submodule update`

# Merging

#### Merging Pull Requests

    git checkout master
    git pull origin master
    git checkout <<featurebranch>>
    git rebase master
    git checkout master
    git merge <<featurebranch>>


