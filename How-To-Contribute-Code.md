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
  * Pick up an issue. We have **_good first bug_** (meaning small Inexor related preknowledge is required) issues to help you getting started:
    * [difficulty beginner](https://github.com/inexor-game/code/issues?utf8=%E2%9C%93&q=label%3A%22good%20first%20bug%22%20%20label%3A%22diff%3Abeginner%22%20); Task which doesn't require you to have any previous experiences with the used language/the used technologies.
    * [difficulty intermediate](https://github.com/inexor-game/code/issues?utf8=%E2%9C%93&q=label%3A%22good%20first%20bug%22%20%20label%3A%22diff%3Aintermediate%22%20); You already made first touch with the used language and are ready for more.
    * [difficulty advanced](https://github.com/inexor-game/code/issues?utf8=%E2%9C%93&q=label%3A%22good%20first%20bug%22%20%20label%3A%22diff%3Aadvanced%22%20); Trickier tasks which also requires you to have some experience with the language and in approaching tasks.
  * You have a new idea for which we don't have an existing issue? (**Use the search first!**)
    * [Create a new issue](https://github.com/inexor-game/code/issues/new)
    * Positive feedback from an Inexor team member will verify you the feature fits into the big picture


***

_If you don't understand the following steps, this [Git-Tutorial](http://pcottle.github.io/learnGitBranching/) could help._
* [Fork the repository](https://help.github.com/articles/fork-a-repo/) and [clone your fork](https://help.github.com/articles/cloning-a-repository/)

1. Create a new branch
 * master-branch has to stay functional
 * naming usually `<yournick>/<newfeature>` so e.g. `donald_trump/great_wall`

2. Develop the feature in your branch
 * Checkout your branch
 * Develop your feature
 * Respect our [[Coding Standards]] (don't worry if you don't understand every detail, reviewing your work we will notify you about passages adaptions are needed)
 * At every logical step, commit your work to git
    * Commit often (but logically)
       * Your feature has to be merged into other branches as easy as possible
       * Big commits often make problems then
       * Use meaningful (!!!) commit messages, with your feature prepending your message e.g. "[physics] add gravity modifiers <new line> <empty line> More detailed description"
 * Push your work to the remote repository on GitHub

3. [Create a Pull Request](https://help.github.com/articles/using-pull-requests/)
 * You don't need to be completely finished with your work, you can create Pull Requests to get early feedback, just  note it then.
 * You might get requests to change several things about your implementation.


### Experiments welcome

Experiments are allowed and encouraged. But: Don't be upset if your idea is getting outvoted by the other Inexor people. If a feature is not a core functionality or controversial, better develop it as a plugin.

