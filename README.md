Role Name
=========

This role installs Rancher 2 (see rancher.com) on a custom server using Docker.
It also installs:
  - one cluster (see the Role variables section)
  - Cert manager with a cluster issuer (see cert-manager.io)
  - in the future it will also install Rook (see rook.io)
Requirements
------------

No Requirements

Role Variables
--------------

- docker_version: "18.03" => The docker version you want to install
- rancher_container_name: "rancher-server" => The name you want for the rancher docker container
- rancher_url: "https://yourserverurl" => The url of the rancher server
- rancher_admin_password: "admin_password" => The password you want
- rancher_cluster_name: "cluster_name" => The name you want for the cluster being created
- rancher_network_provider: "calico" => The network provider
- install_rook: true => if you wish to install Rook
- rook_version: "0.9.1" => The version of Rook
- install_certmanager: true => if you wish to install cert-manager
- cluster_issuer_name: "letsencrypt-staging" => The clusterissuer name it should be "letsencrypt-staging" or "letsencrypt-prod"
- letsencrypt_email: "youremail@email.fr" => The email to user with letsencrypt
validate_certs: true => Use false if you do not desire to use SSL
rancher_ssl_port: 443 => Use a different if you do not desire to use SSL

Dependencies
------------

No Dependencies

Example Playbook
----------------

    - hosts: servers
      tasks:
      - include_role:
          name: '../../rancher2-ansible'
        vars:
          docker_version: "18.03"
          rancher_container_name: "rancher-server"
          rancher_url: "https://yourserverurl"
          rancher_admin_password: "admin_password"
          rancher_cluster_name: "cluster_name"
          rancher_network_provider: "calico"
          install_rook: true
          rook_version: "0.9.1"
          install_certmanager: true
          cluster_issuer_name: "letsencrypt-staging"
          letsencrypt_email: "youremail@email.fr"
          validate_certs: true
          rancher_ssl_port: 443

License
-------

MIT

Author Information
------------------

If you have any issue with the project please open one on Github.
Any pull request or improvement idea is welcome.
