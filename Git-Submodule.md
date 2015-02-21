# Submodule FAQ:

* How can I create a submodule?
* [Somebody else have updated a submodule on the origin (read: GitHub), how can I get the latest version?](#somebody-else-have-updated-a-submodule-on-the-origin-read-github-how-can-i-get-the-latest-version)
* [How can I update a submodule on the origin?](#how-can-i-update-a-submodule-on-the-origin)
* [I get the error "fatal: reference is not a tree". What can I do?](#i-get-the-error-fatal-reference-is-not-a-tree-what-can-i-do)

***

##### Somebody else have updated a submodule on the origin (read: GitHub), how can I get the latest version?

1. Pull the latest version of the repository.
2. Enter in the Git shell: `git submodule update`

##### How can I update a submodule on the origin?
Preconditions: You have pushed a new commit to a repository, which is getting used as a submodule.

1. Go in the repository, which uses the submodule.
2. You have to switch to the directory, in which the submodule is located. You can do this by entering `cd your/path/to/the/submodule`
3. Now execute: `git checkout` and `git pull`
4. Go back to the root directory of the repository (you can go one directory level up with `cd ..`).
5. Create a commit (`git commit -m "Update submodules"`)

##### I get the error "fatal: reference is not a tree". What can I do?
When this is happening, the current initialized submodule repository was getting invalid. Possible scenarios: The repository is moved or deleted.

1. Execute: `git submodule deinit`
2. Pull the latest version of the repository.
3. Execute: `git submodule sync` (this refreshes the submodule URL and branch)
4. Execute: `git submodule update`


