# ansible_linux_setup

Playbook Ansible para automatizar el despliegue de un entorno de trabajo Linux (Ubuntu).

## Propósito

Automatizar la instalación y configuración de herramientas de desarrollo en una máquina Ubuntu, permitiendo replicar el entorno de trabajo de forma reproducible y idempotente.

## Herramientas instaladas

| Rol | Descripción |
|-----|-------------|
| `brave` | Navegador web |
| `codium` | Editor de código (VSCode open-source) |
| `nano` | Editor de texto con configuración |
| `tmux` | Multiplexor de terminal |
| `qemu` | Virtualización con KVM/libvirt |
| `vagrant` | Gestor de máquinas virtuales |
| `ohmybash` | Framework para Bash |
| `bashrc` | Configuración personalizada de Bash |
| `tools` | jq, flameshot, bat, lsd, NerdFonts |

## Estructura del proyecto

```
.
├── main.yml              # Playbook principal
├── ansible.cfg          # Configuración de Ansible
├── inventory            # Inventario de hosts
├── vars_main.yml        # Variables globales
├── Vagrantfile          # Definición de VM para testing
├── AGENTS.md            # Guía para agentes
└── roles/               # Roles de Ansible
    └── <nombre>/        # Cada rol
        ├── tasks/main.yml
        ├── handlers/main.yml
        └── files/       # Archivos de configuración
```

## Requisitos

- Ansible >= 2.9
- Ubuntu 24.04+
- Conexión SSH al host destino

## Uso

### Crear y aprovisionar VM con Vagrant

```bash
vagrant up
ansible-playbook main.yml
```

### Verificar sintaxis sin ejecutar

```bash
ansible-playbook main.yml --syntax-check
```

### Ejecutar un rol específico

```bash
ansible-playbook main.yml --tags tmux
```

## Configuración

- **Inventario**: Define el host destino en `inventory`
- **Usuario**: Configurable en `vars_main.yml` (por defecto `vagrant`)
- **Roles activos**: Editar `main.yml` para habilitar/deshabilitar roles

## Testing

El proyecto incluye Vagrant con provider libvirt para probar el playbook:

```bash
vagrant up          # Crear VM
vagrant ssh         # Conectar a la VM
vagrant destroy     # Eliminar VM
```