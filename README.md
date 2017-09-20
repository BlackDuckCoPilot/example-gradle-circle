# Black Duck CoPilot Gradle/Circle CI Example

[![CircleCI](https://img.shields.io/circleci/project/github/BlackDuckCoPilot/example-gradle-circle/master.svg)](https://circleci.com/gh/BlackDuckCoPilot/example-gradle-circle) [![Black Duck Security Risk](https://copilot.blackducksoftware.com/github/repos/BlackDuckCoPilot/example-gradle-circle/branches/master/badge-risk.svg)](https://copilot.blackducksoftware.com/github/repos/BlackDuckCoPilot/example-gradle-circle/branches/master)

Shows a working setup for using the Black Duck CoPilot integration to analyze the risk of project dependencies

## Circle CI Setup

The `circle.yml` file has been modified to upload generated dependency data to Black Duck CoPilot:

```yaml
test:
  post:
    - bash <(curl -s https://copilot.blackducksoftware.com/ci/circle/scripts/upload)
```
