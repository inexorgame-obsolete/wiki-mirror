You might also be interested in:
* [Build](Build)
* [Coding Standards](Coding Standards)
* [Development Environment](Development Environment)
* [Recruiting](Recruiting)

### Git

We devided the Project in **only-code** and **only-data**. 
Why? Because checkouts and commits are much faster without binary blobs.

Avoid committing binaries into the **source** repository, so the repository stays ligthweight.

### Adding new features
_If you dont understand the following steps, this [Git-Tutorial](http://pcottle.github.io/learnGitBranching/) could help._

1. Create a new branch
 * master-branch has to stay functional
 * naming usually `<yournick>/<newfeature>` so e.g. `a_teammate/ambient-occlusion`

2. Develope the feature in your branch
 * Checkout your branch (your filesystem will change _whush_ Git magic! )
 * Develope your feature 

3. Tell the others about your feature [Briefings](Development Environment)

### Bigger changes

Some features might be on **strategical nature** or might be an **architectural change**. For example replacing the sauerbraten vector class by the vector class of the stdlib would be a bigger architectural change. Another example would be to integrate XMPP to solve multiple features with XMPP as a strategical technology. Both **needs discussion** with the other developers first.

### Experiments welcome

Experiments are allowed and encouraged. But: use your own branch and don't be upset if it doesn't find it's way into the master branch. If a feature is not a core functionality or controversial, better develop it as a plugin.

### Create documentation

Creating documentation is an essential part of the software development process. We document the code and in the wiki.

If you create a new feature or make a non-trivial change, it has to be documented in the [Changelog](Changelog).

### Develop modular, clean and document your work

* No spaghetti code
* No code duplication
* Refactor your work
* Use comments 
* Other Stuff (e.g. Sauerbraten Uniques) [here](Coding Standards)

### Content Contribution

Since our content is **cleanly free**, you are only allowed to contribute to the main-game with a license which allows use in all kinds (including commercial). If you want to read more about our license policy look into our [data repository](https://github.com/inexor-game/data#licensing).

Still, you are always allowed to provide license restricted material as an excluding contentpack and deploy it e.g. over your own server.