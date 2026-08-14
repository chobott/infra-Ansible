# infra-Ansible

Ansible playbooks a konfigurace pro sprá¬¬vu Linux serverů.

## Rychlé¬¬ spuštění

1. Upravte `inventory.ini` a doplňte IP adresy / hostname vašich serverů.
2. Spusťte:
   ```bash
   ansible-playbook -i inventory.ini site.yml
   ```

## Struktura

```
.
├── ansible.cfg            # globá¬¬lní¬¬ konfigurace
├── inventory.ini          # definice hostitelů
├── group_vars/
│   └── all.yml            # globá¬¬lní¬¬ proměnné¬¬
├── playbooks/
│   ├── site.yml           # základní¬¬ playbook (Nginx)
│   ├── hardening.yml      # bezpečnostní¬¬ hardening
│   ├── firewall.yml       # UFW firewall
│   └── monitoring.yml     # Node Exporter pro Prometheus
├── roles/
│   ├── nginx/             
│   └── common/            
└── README.md
```

## Příklady použití

### Instalace Nginx
```bash
ansible-playbook -i inventory.ini playbooks/site.yml
```

### Hardening všech serverů
```bash
ansible-playbook -i inventory.ini playbooks/hardening.yml
```

### Konfigurace firewallu
```bash
ansible-playbook -i inventory.ini playbooks/firewall.yml
```

### Monitoring (Node Exporter)
```bash
ansible-playbook -i inventory.ini playbooks/monitoring.yml
```

### Použití¬¬ rolí¬¬
```bash
ansible-playbook -i inventory.ini -e "@group_vars/all.yml" \
  -e "hosts: webservers" \
  -e "roles: [common, nginx]" site.yml
```

## Další kroky

- **Tajné¬¬ hodnoty**: Použijte `ansible-vault` pro hesla, API klí¬¬če apod.
  ```bash
  ansible-vault create group_vars/all/vault.yml
  ansible-playbook -i inventory.ini site.yml --ask-vault-pass
  ```

- **Rozšíření rolí¬¬**: Vytvořte vlastní role pomocí `ansible-galaxy init roles/<role_name>`.

- **CI/CD**: Integrujte s GitHub Actions pro automatické¬¬ testová¬¬ní¬¬ playbooků.

## Licence

MIT
