# Labs Prep

Making the ansible slave and Jenkins in a cicd namespace in order to get pipelines working...

### Get an ansible Jenkins Slave Built

```shell
oc new-project dev
oc new-project release
oc new-project cicd
git clone https://github.com/redhat-cop/containers-quickstarts
cd containers-quickstarts/jenkins-slaves/jenkins-slave-ansible
oc process -f ../.openshift/templates/jenkins-slave-generic-template.yml     -p NAME=jenkins-slave-ansible     -p SOURCE_CONTEXT_DIR=jenkins-slaves/jenkins-slave-ansible     | oc create -f -
```

### Get a persistent jenkins up and running

```shell
oc create -f https://raw.githubusercontent.com/openshift/origin/master/examples/jenkins/jenkins-persistent-template.json -n openshift
oc new-app --template=jenkins-persistent

```

### Configure the ansible jenkins slave

Surprisingly didn't need to do anything - it's auto configured..!

### Create the github secret in the cicd and dev namespaces

oc create secret generic github-secret --from-literal=username=yourusername --from-literal=password=12345678

### Create the credential inside Jenkins

cicd-github-secret

Add the image here...




