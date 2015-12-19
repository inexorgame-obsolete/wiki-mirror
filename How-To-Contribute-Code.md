You might also be interested in [[How to Contribute Content]].

***

### Git

We divided the Project in **only-code** and **only-data**. 
Why? Because checkouts and commits are much faster without binary blobs.

Avoid committing binaries into the **source** repository, so the repository stays lightweight.

### Adding new features
_If you don't understand the following steps, this [Git-Tutorial](http://pcottle.github.io/learnGitBranching/) could help._

Presteps:  
* Most of the time helpful: Speak with the other Inexor people about your feature idea. [Contact](Developement-Environment)

* Assuming you aren't an Inexor team member, create first a fork of the code repository

1. Create a new branch
 * master-branch has to stay functional
 * naming usually `<yournick>/<newfeature>` so e.g. `a_teammate/ambient-occlusion`

2. Develope the feature in your branch
 * Checkout your branch (your filesystem will change _whush_ Git magic! )
 * Develope your feature 
 * At every logical step, commit your work to git
    * Commit often
       * Your feature has to be merged into other branches as easy as possible
       * Big commits often make problems then
 * Push your work to the remote repository on GitHub

3. Tell the others about your feature 
 * see [Developing Communication](Developing-Communication)
 * and create a Pull Request (https://help.github.com/articles/using-pull-requests/)

4. If your branch is successfully merged into master you should delete your feature branch do keep the repository clean.

### Bigger changes

Some features might be **strategic nature** or might be an **architectural change**. For example replacing the Sauerbraten vector class by the vector class of the stdlib would be a bigger architectural change. Another example would be to integrate XMPP to solve multiple features with XMPP as a strategic technology. Both **needs discussion** with the other developers first.

### Experiments welcome

Experiments are allowed and encouraged. But: use your own branch and don't be upset if it doesn't find it's way into the master branch. If a feature is not a core functionality or controversial, better develop it as a plugin.

### Create documentation

Creating documentation is an essential part of the software development process. We document the code and in the wiki.

If you create a new feature or make a non-trivial change, it has to be documented in the [Changelog](Changelog).

### Develop modular, clean and document your work

* No spaghetti code
* No code duplication
* No overengineering
* Refactor your work
* Use comments 
* Other Stuff (e.g. Sauerbraten Uniques) [here](Coding Standards)

### Pull Requests

    git checkout master
    git pull origin master
    git checkout <<featurebranch>>
    git rebase master
    git checkout master
    git merge <<featurebranch>>
