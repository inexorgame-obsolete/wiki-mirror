You might also be interested in [[How to Contribute Content]].

***

### Git

We divided the Project in [**only-code**](https://github.com/inexor-game/code) (the game itself) and [**only-data**](https://github.com/inexor-game/data) (game content like maps). 
Why? Because checkouts and commits are much faster without binary blobs.

Avoid committing binaries into the **code** repository, so the repository stays lightweight.

### Adding new features

Presteps:  
* Always helpful: [Speak with the other Inexor people](Contact) about your feature idea.

* Take some time to document a roadmap for yourself. Which features would you like to work on or help implementing them? 
  * Pick up an issue. We have **_good first bug_** issues to help you getting started:
    * [difficulty beginner](https://github.com/inexor-game/code/issues?utf8=%E2%9C%93&q=label%3A%22good%20first%20bug%22%20%20label%3A%22diff%3Abeginner%22%20); you just starting to code or you are unfamiliar with our technologies
    * [difficulty intermediate](https://github.com/inexor-game/code/issues?utf8=%E2%9C%93&q=label%3A%22good%20first%20bug%22%20%20label%3A%22diff%3Aintermediate%22%20); you are familiar with our technologies
    * [difficulty advanced](https://github.com/inexor-game/code/issues?utf8=%E2%9C%93&q=label%3A%22good%20first%20bug%22%20%20label%3A%22diff%3Aadvanced%22%20); you know exactly what you are doing
  * You have a new idea for which we don't have an existing issue? (**Use the search first!**)
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
 * Please respect our [[Coding Standards]] (don't worry if you don't understand every detail, it may not apply to your work, likely if you choosed a _difficulty beginner_ issue)
 * At every logical step, commit your work to git
    * Commit often
       * Your feature has to be merged into other branches as easy as possible
       * Big commits often make problems then
 * Push your work to the remote repository on GitHub

3. [Create a Pull Request](https://github.com/inexor-game/code/compare) (https://help.github.com/articles/using-pull-requests/)
 * You don't need to be completely finished with your work, you can create Pull Requests to get early feedback, just don't forget to mention, that you are not finished yet.
 * You might get requests to change serveral things about your implementation.
 * In the worst case scenario we have to reject your Pull Request. You can extremely reduce this risk if you are **keep communicating with us about your ideas and progress. Transparency is the key.** So we will be able to tell you from the beginning if we don't favor an idea.

4. If your branch is successfully merged into master you should delete your feature branch do keep the repository clean.

### Experiments welcome

Experiments are allowed and encouraged. But: Don't be upset if your idea is getting rejected. If a feature is not a core functionality or controversial, better develop it as a plugin.

