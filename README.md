adduser_gitkeys
=========

GNU/Linux users and SSH-Keys from github/gitlab user keys.

Requirements
------------
None.

Role Variables
--------------

Available variables are listed here, including any variables that are in defaults/main.yml, vars/main.yml.

    git_repository_url: https://github.com


The repository URL from where the key's will be downloaded. 

```yaml
    - { username: "anakin.skywalker", gituser: "anakinskywalker", user_groups: "wheel" }
    - { username: "luke.skywalker", gituser: "lukeskywalker", user_groups: ["wheel", "adm"] }
```    

This dictionary contains the values that role accepts when creating a user. The only required value is the username.

The gituser parameter should be used when the Linux user and the github user have different names.

The user_groups parameter is used to add the linux user to a list of determined groups. Value can be a string or a list.

Obs.: Group must exist before assignment.


Dependencies
------------
None.

Example Playbook
----------------

This role is intended to be executed within a loop as shown below:

```yaml
    - hosts: alll
      become: true
      tasks:
      - name: Create Users
        include_role:
          name: arthurfelipems.adduser_gitkeys
        loop:
          - { username: "anakin.skywalker", gituser: "anakinskywalker", user_groups: "wheel" }
          - { username: "luke.skywalker", gituser: "lukeskywalker", user_groups: ["wheel", "adm"] }
```
License
-------

MIT

Author Information
------------------
This role was created by Arthur Silva in 2019.

