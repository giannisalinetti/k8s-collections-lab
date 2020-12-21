# K8S Collections Lab

Demo project to demonstrate Ansible community collections for Kubernetes and OpenShift

Requirements
------------
Install the following collection on the bastion machine:
```
$ ansible-galaxy collection install community.okd
$ ansible-galaxy collection install kubernetes.core
```

Collections should be available as role dependencies in the future. Active RFE have been opened upstream (https://github.com/ansible/ansible/issues/62847).

Role Variables
--------------
**api_url**: API endpoint of the managed server
**cluster_auth_user**: login user
**cluster_auth_password**: login password
**app_name**: Application name
**ns_name**: Target namespace (create if absent)
**app_image**: Application image
**app_replicas**: Final desired replicas
**service_name**: K8s service name
**route_hostname**: Application route name (works in OpenShift only)

Demo
----
To demonstrate the usage of Ansible Vault the cluster credentials have been
splitted in a dedicated `credentials.yaml` file. This file is managed with a
vault id associated with a password file `demo-password-file` (which contains 
the demo password, *RedHat123*).
This demo can be also executed from a job in Ansible Tower.

Before executing the demo update you *cluster_auth_password* and *cluster_auth_user*
variables accordingly with your target cluster with the `ansible-vault` command:
```
$ ansible-vault edit --vault-id demo@demo-password-file credentials.yaml
```

Playbook execution:
```
$ ansible-playbook playbook.yaml --vault-id demo@demo-password-file
```

Author Information
------------------
Gianni Salinetti
Red Hat Cloud Solution Architect
gsalinet@redhat.com
