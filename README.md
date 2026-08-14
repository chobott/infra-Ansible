# infra-Ansible

Ansible playbooks a konfigurace pro sprá¬¬vu Linux serverů.

## Rychlé¬¬ spuštění

1. Upravte `inventory.ini` a doplňte IP adresy / hostname vašich serverů.
2. Spusťte:
   ```bash
   ansible-playbook -i inventory.ini site.yml
   ```

## Struktura

- `inventory.ini` – definice serverů a skupin
- `site.yml` – hlavní playbook pro konfiguraci
- `README.md` – dokumentace

## Další kroky

- Přidat role (`ansible-galaxy init roles/<role_name>`)
- Použijte `ansible-vault` pro tajné¬¬ hodnoty
- Rozdělit playbooky podle účelu (např. `web.yml`, `db.yml`, `hardening.yml`)
