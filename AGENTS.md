# AGENTS.md

## Running the playbook

```bash
ansible-playbook main.yml
```

Uses defaults from `ansible.cfg`:
- Inventory: `inventory`
- SSH key: `~/.vagrant.d/insecure_private_key`

## Testing

### Start the VM
```bash
vagrant up
```
Requires libvirt provider. VM is defined in `Vagrantfile` (Ubuntu 24.04, 2GB RAM).

### Run against existing VM
The inventory points to `192.168.121.53` (host `testing`). Update IP as needed if VM changes.

## Dependencies

```bash
ansible-galaxy collection install community.general
```

## Role structure

- Roles live in `roles/<name>/tasks/main.yml`
- Role variables in `vars_main.yml`
- Config files in `roles/<name>/files/`

## Current active roles

`main.yml` currently enables: `brave`, `tools`, `codium`, `nano`, `tmux`, `qemu`, `vagrant`, `ohmybash`, `bashrc`. Full set available in `README.md`.