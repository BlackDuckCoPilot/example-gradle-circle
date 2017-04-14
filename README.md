# Black Duck CoPilot Gradle/Circle CI Example

[![CircleCI](https://img.shields.io/circleci/project/github/BlackDuckCoPilot/example-gradle-circle/master.svg)](https://circleci.com/gh/BlackDuckCoPilot/example-gradle-circle) [![Black Duck Security Risk](https://copilot.blackducksoftware.com/github/groups/BlackDuckCoPilot/locations/example-gradle-circle/public/results/branches/master/badge-risk.svg)](https://copilot.blackducksoftware.com/github/groups/BlackDuckCoPilot/locations/example-gradle-circle/public/results/branches/master)

Shows a working setup for using the Black Duck CoPilot integration to analyze the risk of project dependencies

## Gradle Setup

The `build.gradle` file has been modified to use the [hub-gradle-plugin](https://github.com/blackducksoftware/hub-gradle-plugin) to generate the data used by CoPilot for analysis:

```groovy
buildscript{
	repositories {
		mavenCentral()
		maven { url 'http://jcenter.bintray.com' }
	}
	dependencies {
		classpath group: 'com.blackducksoftware.integration', name: 'hub-gradle-plugin', version: '4.0.0'
	}
}

apply plugin: 'com.blackducksoftware.hub'

buildBom{
	deployHubBdio false
}
```

## Circle CI Setup

The `circle.yml` file has been modified to upload the generated data to Black Duck CoPilot:

```yaml
test:
  post:
    - ./gradlew buildBom
    - bash <(curl -s https://copilot.blackducksoftware.com/bash/circle) ./build/blackduck/*_bdio.jsonld
```
