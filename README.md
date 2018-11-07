# Black Duck CoPilot Gradle/Circle CI Example

[![CircleCI](https://circleci.com/gh/BlackDuckCoPilot/example-gradle-circle/tree/master.svg?style=svg)](https://circleci.com/gh/BlackDuckCoPilot/example-gradle-circle/tree/master) [![Black Duck Security Risk](https://copilot.blackducksoftware.com/github/repos/BlackDuckCoPilot/example-gradle-circle/branches/master/badge-risk.svg)](https://copilot.blackducksoftware.com/github/repos/BlackDuckCoPilot/example-gradle-circle/branches/master)

Shows a working setup for using the Black Duck CoPilot integration to analyze the risk of project dependencies

## Circle CI Setup

The `.circleci/config.yml` file has been modified to upload generated dependency data to Black Duck CoPilot:

```yaml
    - deploy:
          command: bash <(curl -s https://copilot-test.blackducksoftware.com/ci/circle2/scripts/upload)
```
