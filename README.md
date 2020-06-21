# Ansible for a SANBI server integrated with the cluster and prepared to run Galaxy for IRIDA

Put the name(s) of the server in the hosts file before using this. You'll need to liase with
your friendly SANBI admins to make the required DNS entries.

## Installing Ansible roles

To install all the roles in `requirements.yml` do:

```bash
ansible-galaxy install -p roles -r requirements.yml
```
## Hashicorp vault

To get the vault token, ensure that vault is unsealed and on commander.sanbi.ac.za run:

```bash
VAULT_TOKEN=SuperSecretRootTokenInBitwarden VAULT_ADDR=https://commander.sanbi.ac.za:8200 vault token create -policy irida
```

or ask one on the admins via Slack or SANBI helpdesk.

To use the Vault:

```bash
VAULT_TOKEN="blah" VAULT_ADDR="https://commander.sanbi.ac.za:8200" ansible-playbook -u ubuntu -i hosts server.yml
```

The `-i` and `-u` might not be necessary if you have `inventory` and `remote_user` set in `ansible.cfg`.
