# Chaotic-AUR Ansbile role

Hello and welcome to the repo managing our infrastructure. Lets have a look at how it all works:

- Ansible is used to have reproducable environments and sets up the base system for Docker
- Docker & docker-compose is used to setup Syncthing (used to sync mirrors)

## Some notes

- The Chaotic-AUR role is supposed to bootstrap a basic Chaotic-AUR build environment
- It also creates a GPG key if it doesn't exist and fetches it to `ansible/buffer`
- The content of `chaotic.conf` can be defined in `host_vars`, these also control whether a cluster node or primary node is being deployed
- If the primary node is managed by Ansible (`caur_primary: true`), SSH keys are automatically added to its `authorized_keys`
- Make sure to add the required `host_vars`, examples can be found in `ansible/roles/chaotic_aur/defaults/main.yml`
- If `caur_mirror` is set to `true`, a local Syncthing mirror and web server will be deployed as well - this needs `letsencrypt_data` and `letsencrypt_domain` to be specified
- Check `roles/chaotic_aur/defaults/main.yml` for all available variables
