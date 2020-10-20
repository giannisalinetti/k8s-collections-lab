giannisalinetti.k8s-app-deploy
=========

Demo role to show how to use Ansible k8s and openshift community collections to manage a sample application deployment and scaling.

Requirements
------------

Install the following collection on the bastion machine:
```
$ ansible-galaxy collection install install community.okd
$ ansible-galaxy collection install install community.kubernetes
```

Collections should be available as role dependencies in the future. Active RFE have been opened upstream (https://github.com/ansible/ansible/issues/62847).

Role Variables
--------------

api_url: API endpoint of the managed server
cluster_auth_user: login user
cluster_auth_password: login password
app_name: Application name
ns_name: Target namespace (create if absent)
app_image: Application image
app_replicas: Final desired replicas
service_name: K8s service name
route_hostname: Application route name (works in OpenShift only)


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```
---
- hosts: localhost
  connection: local
  gather_facts: false
  vars_files:
    - vars.yaml
  roles:
    - giannisalinetti.k8s_app_deploy
```

License
-------
GPL-2.0-or-later

Author Information
------------------
Gianni Salinetti
Red Hat Cloud Solution Architect
gsalinet@redhat.com
