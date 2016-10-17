Ansible Role: docker-gc
=========

An ansible role that sets up docker garbage collection using [spotify/docker-gc](https://github.com/spotify/docker-gc)

Requirements
------------

You should have docker installed. I recommend the one role below.

- [angstwad.docker_ubuntu](https://galaxy.ansible.com/angstwad/docker_ubuntu/)

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: woohgit.docker-gc }

License
-------

MIT / BSD


Author Information
------------------

This role was created in 2016 by [Adam Papai](http://www.wooh.hu).
