Once you've completed the build procedure, the procedure to start Inexor is a little bit complicated at the moment.
That's due to ongoing refactorings.

So this page serves as an introduction to the (temporal) startup-procedure.
It's expected to get superseded as issue #449 is solved.

### Prerequirements

* You [built](https://github.com/inexorgame/inexor-core/wiki/Build) Inexor
* (make sure the subfolders inside inexor-core/flex/interfaces are not empty)

## Get it first-time ready

1. Open a Terminal and go into the inexor-core flex subfolder
    * windows users: right-click on the flex directory with your shift-key pressed. press the entry with `cmd`, `command prompt` or `Powershell`
2. update flex
    * **windows users** (this is an open bug see #478)
        * run: `git fetch` and afterwards `git checkout 0dab4fa4e6039cb8e65bc50e4c94b1b0b9f2aafc`
    * **linux users**
        * run `git pull`
3. install flex
    * `npm install`

## Run it:

4. `npm start`
    * in the flex subdirectory as well

### Dev setup (ui-flex):
TODO @aschaeffer or @Fohlen