# UNIR Tennis Match Automation

This project automates the generation of a tennis match file using **Vagrant** and **Ansible**. One player is defined statically in variables, while the second is fetched dynamically from an external API (`randomuser.me`).

## Project Structure

```bash
.
├── Vagrantfile
├── playbook.yml
├── roles/
│   └── match/
│       ├── tasks/
│       │   └── main.yml
│       ├── vars/
│       │   └── match_vars.yml
│       └── templates/
│           └── match.txt.j2
```

## Prerequisites

Make sure the following tools are installed on **Windows 11**:

- [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
- [Vagrant](https://developer.hashicorp.com/vagrant/downloads)
- [Visual Studio Code](https://code.visualstudio.com/) (or similar)

## Usage

### Start and provision the VM

```bash
vagrant up
```

### Re-provision if needed

```bash
vagrant up --provision
vagrant provision
```

### Access the VM

```bash
vagrant ssh
```

Then check the OS:

```bash
lsb_release -a
```

### Pause, resume or shutdown the VM

```bash
vagrant suspend
vagrant resume
vagrant halt
```

### Destroy the VM

```bash
vagrant destroy
```

## Customization

- To use a modern Ubuntu version (e.g. `hashicorp-education/ubuntu-24-04`).
- Static player information is set in `playbook.yml` and `roles/match/vars/match_vars.yml`.
- API player data is dynamically fetched and parsed in `main.yml`.

## Output Example

Upon successful provisioning, a file `/vagrant/match.txt` will be created with content like:

```txt
** UNIR TENNIS MATCH INFORMATION **

First Name: Aitor.
Last Name: Menta.
City: Madrid.
ID: 1234.

First Name: Emilio.
Last Name: Marín.
City: San Sebastián.
ID: 98727241-J.

Date: 2025-07-26T13:20:00Z.
```

## References

- [Vagrant Documentation](https://developer.hashicorp.com/vagrant)
- [Vagrant Cloud Boxes](https://portal.cloud.hashicorp.com/vagrant/discover)
- [Random User Generator](https://randomuser.me/)
