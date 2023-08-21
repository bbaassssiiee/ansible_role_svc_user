# svc_user

Ansible-role to install a service account.

## Testing ##

cd to this role's directory and run:

```bash
sudo -v
molecule cleanup -s localhost
molecule converge -s localhost
```

### Variables

To use this role it needs an SSH key-pair.
The SSH key pair should comply to the crypto-policy of the ssh servers.
The key files should be stored in a vars file in your project or inventory/group_vars.

You should encrypt this vars file using ansible-vault.

A public key for ~/.ssh/authorized_keys can stored in a single-line variable:

```
vault_svc_user_public_key: ssh-rsa ...
```

A matching private_key should be stored in a multi-line variable (pipe character |):

```
vault_svc_user_private_key: |
  -----BEGIN RSA PRIVATE KEY-----
  . . .
  -----END RSA PRIVATE KEY-----
```

See `defaults/main.yml` for other variables.

### Role variables

### Examples

```yaml
- name: Install svc_user
  hosts: all

  roles:
  - role: svc_user
```
