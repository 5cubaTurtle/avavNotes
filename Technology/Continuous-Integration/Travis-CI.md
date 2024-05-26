**Travis CI** is a hosted[[1]](https://en.wikipedia.org/wiki/Travis_CI#cite_note-1) [continuous integration](https://en.wikipedia.org/wiki/Continuous_integration "Continuous integration") service used to build and test software projects hosted on [GitHub](https://en.wikipedia.org/wiki/GitHub "GitHub"),[[2]](https://en.wikipedia.org/wiki/Travis_CI#cite_note-2) [Bitbucket](https://en.wikipedia.org/wiki/Bitbucket "Bitbucket"), [GitLab](https://en.wikipedia.org/wiki/GitLab "GitLab"), [Perforce](https://en.wikipedia.org/wiki/Perforce "Perforce"), [Apache Subversion](https://en.wikipedia.org/wiki/Apache_Subversion "Apache Subversion") and [Assembla](https://en.wikipedia.org/wiki/Assembla).

[tutorial](https://docs.travis-ci.com/user/tutorial/)
### Yaml file
Yaml file instructs the Travis CI engine to run [[Docker]] and build the application. 
Example *.travis.yml* file:
```yml
sudo: required
services:
  - docker

script:
  - docker build -t avasfields/node .
  - docker images avasfields/node
```
