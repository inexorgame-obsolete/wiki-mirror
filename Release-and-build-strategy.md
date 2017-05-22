# Release and build strategy
The following article addresses main concerns and how to solve them during _alpha_ release phase (current).
The pad for this article can be found [here](https://hackmd.io/IYDgzARgpuYLQE5gHYDGcAsIBMA2OwEEAZnCBACaoCMyFEYqUyQA#).

## Short release system
Proposed system will bring releases more often and fast:

- every approved PR will bring a new release
- depending on it's severity, the release is either a patch, minor or major according to [semver](http://semver.org/)
- major releases will be called out for new Inexor series (names)

## The Inexor installer
The following proposal should make it easy for everyone to obtain Inexor:

* the core client and server will be npm modules
  * shipped via npm/update
  * built for Ubuntu 16.04 and Windows *only* for now
  * x64 is enough for now we think
  * building and publishing could/should be done via Travis and Appveyor
    * how is it possible to ship build stuff from conan?
* flex will be a npm module
  * flex has a standalone user interface
  * is opened by default in a Browser when core is *not* installed
  * contains: Install, Manage Plugins, Manage Instances

## Release plan, why
We've been seeing a much decreased rate of commitment to Inexor, mainly because "the average user" cannot see/touch/use Inexor at all. That should be changed.

## What's to be done:

- for team organisation: priorise tickets
- build a fast release cycle/system
- add the Flex UI
- go on with usual tickets (Refactoring, CEF bugs)
- add the information on the website!
