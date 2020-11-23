# Atualizar automaticamente somente as atualizações de segurança num Ubuntu:

aptitude install unattended-upgrades

nano /etc/apt/apt.conf.d/10periodic

Excluir tudo e adicionar:
```bash
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "7";
APT::Periodic::Unattended-Upgrade "1";
```
Isso somente atualiza pacotes de segurança

## Atualização completa, de todos os pacotes:

apt-get update

apt-get upgrade

Atualize o servidor manualmente pelo menos uma vez por dia.


