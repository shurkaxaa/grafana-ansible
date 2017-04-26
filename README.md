Ansible-Grafana
===============

Install and configure Grafana server to be used with Monasca.

Requirements
------------

none

Role Variables
--------------

    grafana_keystone_url: "http://localhost:5000"
    grafana_keystone_default_domain: "default"
    grafana_keystone_default_role: "monasca-read"
    grafana_keystone_admin_roles: "admin"
    grafana_kestone_admin_roles: "admin"
    grafana_keystone_editor_roles: "monasca-user"
    grafana_keystone_read_editor_roles: "monasca-user,monasca-read-only-user"
    grafana_keystone_viewer_roles: "monasca-read-only-user"
    grafana_keystone_verify_ssl_cert: True
    
    grafana_golang_version: "go1.7.linux-amd64"
    grafana_admin_password: password
    grafana_db_type: mysql #Could be any of mysq/sqlite3/postgresql
    grafana_sqlite3_path: "/src/grafana/grafana.sqlite3.db"
    
    grafana_mysql_root_user: root
    grafana_mysql_root_password: root
    grafana_mysql_host: localhost
    grafana_mysql_port: 3306
    grafana_mysql_db: grafana
    grafana_mysql_user: grafana
    grafana_mysql_password: password
    
    grafana_http_addr: 0.0.0.0
    grafana_http_port: 3000
    grafana_http_protocol: http
    
    grafana_data_dir: "/srv/grafana/data"
    grafana_log_dir: "/var/log/grafana"
    grafana_plugins_dir: "/srv/grafana/plugins"
    
    grafana_users_allow_sign_up: False
    
    grafana_plugins:
      - repo: https://github.com/openstack/monasca-grafana-datasource
        version: master
    
    grafana_log_mode: "console file"
    grafana_log_level: info
    
    grafana_git_repo: "https://github.com/sapcc/grafana.git"
     
    grafana_clone_dir: "/opt/grafana-src"
    grafana_build_dir: "/opt/grafana-build"
    
    nvm_version: 0.32.1
    node_js_version: 4.0.0

Dependencies
------------

none

Example Playbook
----------------

    - name: Install Grafana
      hosts: grafana
      user: root
      roles:
        - { role: "grafana-ansible" }
      vars:
        - grafana_keystone_url: "http://{{ groups['devstack'][0] }}:5000"

Tested on
---------

Ubuntu 16.04 xenial xerus

Author Information
------------------
Flávio Ramalho

flaviosr@lsd.ufcg.edu.br

License
-------
Apache 2
