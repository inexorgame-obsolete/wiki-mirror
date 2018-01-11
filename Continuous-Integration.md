## Top-level overview (keep it short and simple)

  * [ci-docker](https://github.com/inexorgame/ci-docker) - Docker images
    * Linux: build by [Travis](http://travis-ci.org/inexorgame/ci-docker/) and published to [DockerHub](https://hub.docker.com/r/inexorgame/ci-docker/)
  * [inexor-core](https://github.com/inexorgame/inexor-core)
    * Linux: [Travis](http://travis-ci.org/inexorgame/inexor-core/) downloads our Docker images and builds and tests inexor-core within them; publishes build packages to [GitHub releases](https://github.com/inexorgame/inexor-core/releases)
    * Windows: [AppVeyor](https://ci.appveyor.com/project/inexorgame/code) builds and tests; publishes build packages to [GitHub releases](https://github.com/inexorgame/inexor-core/releases)
  * [ci-prebuilds](https://github.com/inexorgame/ci-prebuilds) - Conan dependencies packages
    * Linux: [Travis](http://travis-ci.org/inexorgame/ci-prebuilds/) downloads our Docker images and builds our Conan dependencies within them; publishes build packages to [our Bintray repository](https://bintray.com/inexorgame/inexor-conan)
    * macOS **_upcoming, highly experimental_**: [Travis](http://travis-ci.org/inexorgame/ci-prebuilds/) builds our Conan dependencies; publishes build packages to [our Bintray repository](https://bintray.com/inexorgame/inexor-conan)
    * Windows: [AppVeyor](https://ci.appveyor.com/project/inexorgame/ci-prebuilds) builds our Conan dependencies; publishes build packages to [our Bintray repository](https://bintray.com/inexorgame/inexor-conan)
  * [inexor-flex](https://github.com/inexorgame/inexor-flex)
     * Linux: [Travis](http://travis-ci.org/inexorgame/inexor-core/) builds and test; deploys documentation
     * Windows: [AppVeyor](https://ci.appveyor.com/project/inexorgame/inexor-flex) builds and test


## More details
Generally speaken, we are trying to build and test our applications on all [platforms (operating systems, compilers..) we support](https://github.com/inexorgame/inexor-core/wiki/Platform-Support).
