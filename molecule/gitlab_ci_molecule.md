# Testing Ansible's roles

## Description
Our infrastracture for CI is:
1. [Gitlab](https://about.gitlab.com)
2. [OpenShift Origin](https://www.openshift.org/)

We will configure [Gitlab runner](https://docs.gitlab.com/runner/install/kubernetes.html) to test ansible roles with [molecule](https://molecule.readthedocs.io). If you don't know [molecule](https://molecule.readthedocs.io) please read documentation [there](https://molecule.readthedocs.io).  
[Molecule](https://molecule.readthedocs.io) is able to use Docker for testing Ansible roles and that's what we needed.  

## Pipeline

<img src="oc-gitlab-ci-molecule.png" width="250">

## Set everything up

### Openshift

#### Create new project 

Openshift Web Console -> New project

<img src="NewProject.PNG" width="250">

Upload new Template

Openshift Web Console -> Gitlab-ci -> Add to Project -> Import YAML/JSON

Insert template:

<script src="https://gist.github.com/skk2010/35bda10797891270668ab4e39bdd1047.js"></script>



`oc adm policy add-scc-to-user privileged <user>`
