You might also be interested in [[How to Contribute Content]].

***

### Git

We divided the Project in **only-code** and **only-data**. 
Why? Because checkouts and commits are much faster without binary blobs.

Avoid committing binaries into the **source** repository, so the repository stays lightweight.

### Adding new features

Presteps:  
* Always helpful: [Speak with the other Inexor people](Contact) about your feature idea.

* Take some time to document a roadmap for yourself. Which features would you like to work on or help implementing them? 
  * Pick up an issue. We have **_good first bug_** issues to help you getting started:
    * [difficulty beginner](https://github.com/inexor-game/code/issues?utf8=%E2%9C%93&q=label%3A%22good%20first%20bug%22%20%20label%3A%22diff%3Abeginner%22%20); if you just starting to code or if you are unfamiliar with our technologies
    * [difficulty intermediate](https://github.com/inexor-game/code/issues?utf8=%E2%9C%93&q=label%3A%22good%20first%20bug%22%20%20label%3A%22diff%3Aintermediate%22%20); you are familiar with our technologies
    * [difficulty advanced](https://github.com/inexor-game/code/issues?utf8=%E2%9C%93&q=label%3A%22good%20first%20bug%22%20%20label%3A%22diff%3Aadvanced%22%20); you know exactly what you are doing
  * You have a new idea for which we don't have an existing issue? 
    * [Create a new issue](https://github.com/inexor-game/code/issues/new)
    * Get the discussion going, provide more information when asked
    * If you get positive feedback from an Inexor team member, you can start implementing your feature


***

_If you don't understand the following steps, this [Git-Tutorial](http://pcottle.github.io/learnGitBranching/) could help._
* [Fork the repository](https://help.github.com/articles/fork-a-repo/) and [clone your fork](https://help.github.com/articles/cloning-a-repository/)

1. Create a new branch
 * master-branch has to stay functional
 * naming usually `<yournick>/<newfeature>` so e.g. `a_teammate/ambient-occlusion`

2. Develop the feature in your branch
 * Checkout your branch
 * Develop your feature 
 * At every logical step, commit your work to git
    * Commit often
       * Your feature has to be merged into other branches as easy as possible
       * Big commits often make problems then
 * Push your work to the remote repository on GitHub

3. Tell the others about your feature 
 * see [[Contact]]
 * and [create a Pull Request](https://github.com/inexor-game/code/compare) (https://help.github.com/articles/using-pull-requests/)

4. If your branch is successfully merged into master you should delete your feature branch do keep the repository clean.

### Bigger changes

Some features might be **strategic nature** or might be an **architectural change**. For example replacing the Sauerbraten vector class by the vector class of the stdlib would be a bigger architectural change. Another example would be to integrate XMPP to solve multiple features with XMPP as a strategic technology. Both **needs discussion** with the other developers first.

### Experiments welcome

Experiments are allowed and encouraged. But: use your own branch and don't be upset if it doesn't find it's way into the master branch. If a feature is not a core functionality or controversial, better develop it as a plugin.

### Create documentation

Creating documentation is an essential part of the software development process. Please have a look [here to learn more about documentation](Documentation).

If you create a new feature or make a non-trivial change, it has to be documented in the [Changelog](https://github.com/inexor-game/code/blob/master/changelog.md).

### Develop modular, clean and document your work

* No spaghetti code
* No code duplication
* No overengineering
* Refactor your work
* Use comments 
* Other Stuff (e.g. Sauerbraten Uniques) [here](Coding Standards)

### Merging Pull Requests

    git checkout master
    git pull origin master
    git checkout <<featurebranch>>
    git rebase master
    git checkout master
    git merge <<featurebranch>>
