# BackupResync
Esse tutorial é para voce que precisa fazer um backup automatizado no linux e não tem idéia de como fazer e deixar automatizado.

Iriei mostrar como fazer backups diários, semanais e mensais, iremos manter somente um numero máximo de backups, que pode ser configurado conforme sua necessidade.

O backup vai ter como exemplo situações de produção com uso de Docker, banco de dados ou pode ser feito com quaisquer arquivos, iremos usar:
Tar
find
Cron
Rsync

comando de backup do mysql novosga dentro do container em tempo real

sudo docker exec novosga_mysqldb_1  /usr/bin/mysqldump -u root --password='semad!dsis' novosga2 >  /home/docker/backup/daily/backup.sql


Esse comando compacta o dump do mysql e salva na pasta com a ano/mes/dia e mantem apenas 7 pastas de backup

#usar o dump criado na pasta diario compactar e criar uma pasta com a data do dia
sudo tar -zcf /home/docker/backup/daily/backup-novosga-$(date +%Y%m%d).tar.gz -C /home/docker/ mysqldump
find /home/docker/backup/daily/* -mtime +7 -delete

-----------------------------------




https://www.youtube.com/watch?v=j2vBT3T79Pg

https://tonyteaches.tech/rsync-backup-tutorial/

https://www.youtube.com/watch?v=vybL_kuBVsA&t=157s

Melhor maneira que eu achei de fazer um backup automatizado
