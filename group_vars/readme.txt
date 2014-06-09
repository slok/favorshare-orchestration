This vars will be independent of the inventory (Production, staging...)


In Ansible 1.2 or later the group_vars/ and host_vars/ directories can
exist in either the playbook directory OR the inventory directory.
If both paths exist, variables in the playbook directory will be loaded second.