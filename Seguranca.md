# Segurança em servidor tipo VPS

https://www.youtube.com/watch?v=WXL37SjSs9g&feature=youtu.be&fbclid=IwAR10lnvZ6CHIN63fAvFi2c7R2pS52XyIRd2-8iXorkmibniDqJjByd0A0qI

- Acesso SSH com chave criptografada. Criar chave SSH no desktop usando a senha do desktop, copiar e colar a chave pública para o servidor
- fail2bn
- Desabilitar o acesso com root ao SSH
- Mudando a senha do SSH
- Desabilitar cache de senha do SSH
- Update e upgrade do sistema. Sempre a última versão LTS da distribuição
- Habilitando o firewall
- Verificando conexões ativas

Acessando

ssh root@IP -i ~/.ssh/chave_publica

Criar usuário

sudo adduser ribafs

Adicionar ao grupo sudo

sudo adduser ribafs sudo

Após reiniciar o SSH

Adicionar o novo user ao ssh

ssh-copy-id -i ~/.ssh/chave-publica.pub ribafs@IP

Bloquear acesso com root e com senha

Reiniciar ssh

Mudar porta do SSH

Reiniciar ssh

Acessar usando a porta

-p porta

Desabilitar acesso visual do SSH

Antes de habilitar firewall (que bloqueia acesso com o servidor)

Liberar acesso da porta SSH
```php
sudo ufw allow porta/tcp
sudo ufw enable
```
Um bom utilitário é o tilix (é um terminal que pode ser dividido na vertical ou horizontal)

sudo apt install tilix

Desativar ping ufw

Verificar conxões ativas

netstat -peanut

Para acesso externo somente a porta do ssh. 53, do DNS somente para consulta interna

Ver servido da Cloudflare com DDOS


Não usar ftp, mas somente ssh

Proteger arquivos de configuração do apache, php e mysql contra escrita:

/etc/php/7.0/apache2/php.ini
/etc/apache2/sites-available/default e demais
/etc/mysql/my.ini
index.php, configuration.php, tempalte/.../index.php


Básicos

- Sistema operacional seguro e estável
- Atualização do SO e dos aplicativos
- Firewall com todas as portas fechadas, exceto algumas
- Alguns softwares que reforçam:
    - fail2ban
    - Web Application Firewall (WAF), como o ModSecurity. NAXSI para Nginx
    - 
- Otimizar a segurança:
    - Desktop
    - SSH
    - Apache/Nginx
    - PHP
    - MySQL/MariaDB
    - Joomla
    - Laravel

Os cuidados com a segurança colaboram para que os sites e aplicativos instalados no servidor sejam executados de forma esperada, rápida e sem interrumpção.

Princípios básicos de segurança:

- Hospede seu site em servidor seguro
- Efetue backup regularmente, especialmente a cada alteração no site
	A melhor opção atualmente para backup é o Akeeba Backup - https://www.akeebabackup.com/download.html
	Caso tenha dificuldade de usar o formato JPA, altere em Configuration - Archiver engine para ZIP format
	Ele gera o backup com um instalador. Para restaurar apensa instale como se fosse instalar o Joomla
	Faça também backup dos scripts de configuração do servidor para o caso de uma reinstalação
	Lembre de fazer o backup do servidor com os recursos da hospedagem ou crie um snapshot
- Também faça teste de restore de vez em quando para garantir que o backup está integro
- A quantidade de cópias de backup a ser guardada depende da importância do site. Se mais importante mais cópias
- As cópias devem ser armazenadas em mídia confiável: HD e DVD
- Efetue atualização com frequência. Mantenha o aviso de atualização ativo para que receba um aviso por e-mail e atualize imediatamente
- Após a primeira atualização reinicie o servidor
- Acessar de forma segura usando SSH (enxuto e configurado para salvar a senha) e nunca via FTP
- Manter seu desktop seguro, usando um sistema operacional seguro no mesmo, com firewall e outros cuidados
- Use e abuse da comunidade com seus conhecimentos e generosidade para manter-se atualizado em termos de segurança e proteger seu site
- Use senhas fortes
- Use o SSL para proteger pelo menos o administrator
- Use boas extensões para reforçar a segurança
- Remova todas as extensões que não estiver usando e não somente desabilite
- Evite instalar pacotes para desenvolvimento como gcc, make, etc e evite também instalar repositórios instáveis.
- Monitorar frequentemente os logs à procura de algo suspeito em todos os serviços ativos
- Use softwares tipo IDS que detectam intrusões
- Instalar um bom firewall de aplicativos como o mod_security
- Ficar bem atento, estudando, se informando sempre sobre o assunto de que cuida
- Logo após a configuração final do servidor já crie um backup ou snapshot da droplet e fique atento para criar outro logo que o servidor esteja concluído e bem configurado.
- Uma boa ideia é ter uma box no Vagrant do Ubuntu 16.04 em seu desktop, sendo cópia fiel e original do servidor localmente, mesma distribuição, mesma versão
- E use alguns que reforçam a segurança como:
fail2ban
denyhosts
lynis
rhhunter
mod_evasive
...


