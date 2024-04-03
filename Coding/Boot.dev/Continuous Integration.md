Refer to `/Users/albert/Desktop/code/bootDev/learn-cicd-starter`

__Continuous Integration__ (CI) is where developers regularly push code changes into a central repository, and by doing so, automated builds and tests are automatically run.

A __good CI pipeline__ typically includes _unit tests, integration tests, styling checks, linting checks, security checks_ or any other type of automated test. If _any_ of the tests fail, the build is considered broken and the developer is notified so they can fix it.

__GitHub Actions workflows__ are written in [YAML](https://en.wikipedia.org/wiki/YAML), and GitHub automatically checks for and runs workflows in the `.github/workflows` directory of your repository.

