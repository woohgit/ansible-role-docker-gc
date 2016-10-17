Ansible Role: docker-gc
=========

[![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-woohgit.docker-gc-blue.svg)](https://galaxy.ansible.com/woohgit/docker-gc/) [![Build Status](https://travis-ci.org/woohgit/ansible-role-docker-gc.svg?branch=master)](https://travis-ci.org/woohgit/ansible-role-teleport)


An ansible role that sets up docker garbage collection using [spotify/docker-gc](https://github.com/spotify/docker-gc)

Requirements
------------

You should have docker installed. I recommend the one role below.

[angstwad.docker_ubuntu](https://galaxy.ansible.com/angstwad/docker_ubuntu/)

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):

	exclude_from_gc: []

Excluding images from garbage collection.

There can be images that are large that serve as a common base for many application containers, and as such, make sense to pin to the machine, as many derivative containers will use it. This can save time in pulling those kinds of images. There may be other reasons to exclude images from garbage collection.

This variable can contain image name patterns (in the grep sense),such as `spotify/cassandra:latest` or it can contain image ids (truncated to the length shown in docker images which is 12.)


	exclude_containers_from_gc: []

Excluding containers from garbage collection

There can also be containers (for example data only containers) which you would like to exclude from garbage collection. This variable should container name patterns (in the grep sense), such as mariadb-data.

	force_image_removal: 0

By default, docker will not remove an image if it is tagged in multiple repositories. If you have a server running docker where this is the case, for example in CI environments where dockers are being built, re-tagged, and pushed, you can enable a force flag to override this default by setting it to `1`.

	force_container_removal: 0

By default, if an error is encountered when cleaning up a container, Docker will report the error back and leave it on disk. This can sometimes lead to containers accumulating. If you run into this issue, you can force the removal of the container by setting the environment variable to `1`:

	grace_period: 3600

By default, docker-gc will not remove a container if it exited less than 3600 seconds (1 hour) ago. In some cases you might need to change this setting.

	gc_frequency:  "hourly"

How frequent should docker-gt run. Valid values are: `"hourly", "daily", "weekly", "monthly"`

	docker_sock: "/var/run/docker.sock"

The location of the docker server socket.


Example Playbook
----------------

    - hosts: servers
      vars:
        exclude_from_gc:
          - spotify/docker-gc
        force_container_removal: 1
      roles:
         - { role: woohgit.docker-gc }

License
-------

MIT / BSD


Author Information
------------------

This role was created in 2016 by [Adam Papai](http://www.wooh.hu).
