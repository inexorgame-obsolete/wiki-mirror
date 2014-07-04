### Git

We pulled the complete commit history of sauerbraten and devided it in only-code, only-data and only-build parts. Why? Because checkouts and commits are much faster without binary blobs.

Avoid committing binaries into the **source** repository, so the repository stays leigthweight.

### Adding new features

Create a new branch first, so that the main (master) branch stays functional all the time. Switch to this branch, then develop your feature. As soon your feature is working, tell the others to test your branch. If everyone is fine with it, merge the feature into the master branch.

### Bigger changes

Some features might be on strategical nature or might be an architectural change. For example replacing the sauerbraten vector class by the vector class of the stdlib would be a bigger architectural change. Another example would be to integrate XMPP to solve multiple features with XMPP as a strategical technology. Both needs discussion with the other developers first.

### Experiments allowed

Experiments are allowed and encouraged. But: use your own branch and don't be upset if it don't find it's way into the master branch.

### Develop modular, clean and document your work

* No spaghetti code
* No code duplication
* Refactor your work
* Document your code
* Document the feature -> [Changelog]

### Content Contribution

TODO: license details