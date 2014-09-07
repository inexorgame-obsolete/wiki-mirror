### Git

We pulled the complete commit history of sauerbraten and devided it in only-code, only-data and only-build parts. Why? Because checkouts and commits are much faster without binary blobs.

Avoid committing binaries into the **source** repository, so the repository stays ligthweight.

### Adding new features

Create a new branch first, so that the main (master) branch stays functional all the time. Switch to this branch, then develop your feature. As soon your feature is working, tell the others to test your branch. If everyone is fine with it, merge the feature into the master branch.

### Bigger changes

Some features might be on strategical nature or might be an architectural change. For example replacing the sauerbraten vector class by the vector class of the stdlib would be a bigger architectural change. Another example would be to integrate XMPP to solve multiple features with XMPP as a strategical technology. Both needs discussion with the other developers first.

### Experiments allowed

Experiments are allowed and encouraged. But: use your own branch and don't be upset if it doesn't find it's way into the master branch. If a feature is not a core functionality or controversial, better develop it as a plugin.

### Create documentation

Creating documentation is an essential part of the software development process. We document the code and in the wiki.

If you create a new feature or make a non-trivial change, it has to be documented in the [Changelog](Changelog).

### Develop modular, clean and document your work

* No spaghetti code
* No code duplication
* Refactor your work
* Use comments 

### Content Contribution

Since sauerbraten-fork's content is cleanly free, you are only allowed to contribute to the main-game with a license which allows use in all kinds (including commercial). If you want to read more about our license policy look into our [data repository](https://github.com/sauerbraten-fork/sauerbraten-fork-data#licensing).

Still, you are always allowed to provide license restricted material as an excluding contentpack and deploy it e.g. over your sauerbraten-fork server.