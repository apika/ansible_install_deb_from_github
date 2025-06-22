install_deb_from_github
=========

Install the latest .deb from a github repository.

Requirements
------------

- jmespath

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

- github_api_releases_url: Github API url that returns all the releases. Usually has the form of https://api.github.com/repos/USER/REPO/releases/latest
- json_query: Optional. Configure the [json filter](https://docs.ansible.com/ansible/latest/collections/community/general/json_query_filter.html#ansible-collections-community-general-json-query-filter) that finds the url. Default value: "assets\[?content_type=='application/vnd.debian.binary-package'\].browser_download_url"

Example Playbook
----------------

    - hosts: localhost
      roles:
        - role: ansible_install_deb_from_github
          github_api_release_url: https://api.github.com/repos/openbao/openbao/releases/latest
          json_query: "assets[? !contains(name, 'hsm') && content_type=='application/vnd.debian.binary-package'].browser_download_url"
