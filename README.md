# atend

* This multi-module project shows that something changed between Apache Maven 3.8.4 and 3.8.5.
* The project will deploy to locally to /tmp/m2repo by setting altSnapshotDeploymentRepository.
* `installAtEnd` and `deployAtEnd` are set.
* An additional repository _repo.jenkins-ci.org_ is activated by a marker file in the project `.maven-profiles/settings-jenkins-repository`.
* Apache 3.8.5 (and 3.8.6) do not install or deploy anything while 3.8.4 does.
```
mkdir -p ~/Downloads
curl -s https://archive.apache.org/dist/maven/maven-3/3.8.4/binaries/apache-maven-3.8.4-bin.tar.gz | (cd ~/Downloads && tar xvz)
curl -s https://archive.apache.org/dist/maven/maven-3/3.8.5/binaries/apache-maven-3.8.5-bin.tar.gz | (cd ~/Downloads && tar xvz)

# Stuff is installed resp. deployed
~/Downloads/apache-maven-3.8.4/bin/mvn -B -V -s settings-oss.xml deploy

# Stuff is not installed resp. deployed
~/Downloads/apache-maven-3.8.5/bin/mvn -B -V -s settings-oss.xml deploy
```
