# github_packages_publish
Scrip to help publish Android Libraries to Github Package Repository

# configure library from publishing

## Add
```
GITHUB_PACKAGES_USER={your github username}
GITHUB_PACKAGES_TOKEN={your github personal access token}
```
```
e.g.
GITHUB_PACKAGES_USER=JRWilding
GITHUB_PACKAGES_TOKEN=23580923...
```

to your ~/.gradle/gradle.properties file. Create a personal acccess token with the read:packages, write:packages permissions -> https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line

## Add
```
plugins {
  id "digital.wup.android-maven-publish" version "3.6.2"
}
```

To your library's build.gradle file. This is a requirement to get the library's .aar file to be published

## Add
```
GITHUB_PACKAGES_OWNER={owner of the repo}
GITHUB_PACKAGES_REPOSITORY={repo}
GROUP={group id of the library}
ARTIFACT_ID={artifact id of the library}
VERSION_NAME={version of the library}
```
```
e.g.
GITHUB_PACKAGES_OWNER=JRWilding
GITHUB_PACKAGES_REPOSITORY=github_packages_publish
GROUP=com.github.JRWilding
ARTIFACT_ID=github-packages
VERSION_NAME=1.0.0
```

to your library's project/gradle.properties file
Your group id will likely be com.github.{github username} and your artifact id can be whatever.

## Add
```
apply from: "https://raw.githubusercontent.com/JRWilding/github_packages_publish/master/publish.gradle"
```

To your library's project/build.gradle file.

# publish new verison of library

Run the `publish` task that will now be available in your project. The library will be built and published to the GitHub Package Repository.

# use library as dependency
## Add
```
apply from: "https://raw.githubusercontent.com/JRWilding/github_packages_publish/master/repo.gradle"
dependencies {
  implementation ('{group id}:{artifact id}:{version}')
}
```
```
e.g
apply from: "https://raw.githubusercontent.com/JRWilding/github_packages_publish/master/repo.gradle"
dependencies {
  implementation ('com.github.JRWilding:github-packages:1.0.0')
}
```
to your app project's build.gradle file using hte same group id, artifact id and version that you published.
