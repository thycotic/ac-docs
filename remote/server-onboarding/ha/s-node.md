[title]: # (Slave Node Setup)
[tags]: # (remote access controller)
[priority]: # (3)
# Steps to Configure New Slave Node On-premises Environment

1. Mount NFS filesystem on folder `/opt/efs`. Refer to instructions under [Setup a Standalone NFS Server](nfs.md).
1. Create a backup directory

   ```bash
      mkdir /root/oid_backup
   ```
1. Copy panel files to new `/opt/efs` and create soft links

   ```bash
      mv /home/onionid/panel/storage/vault /root/oid_backup/
      ln -s /opt/efs/panel/vault /home/onionid/panel/storage/vault

      mv /opt/efs/panel/videos /root/oid_backup/
      ln -s /opt/efs/panel/videos /home/onionid/panel/storage/videos

      mv /home/onionid/panel/storage/org-keys  /root/oid_backup/
      ln -s /opt/efs/panel/org-keys /home/onionid/panel/storage/org-keys

      mv  /home/onionid/panel/storage/windows/rdp/fetch /root/oid_backup/
      ln -s /opt/efs/panel/rdp/fetch /home/onionid/panel/storage/windows/rdp/fetch

      mv  /home/onionid/panel/storage/windows/rdp/reset /root/oid_backup/
      ln -s /opt/efs/panel/rdp/reset /home/onionid/panel/storage/windows/rdp/reset

      mv /home/onionid/panel/storage/recordings  /root/oid_backup/
      ln -s /opt/efs/panel/rdp/recordings /home/onionid/panel/storage/recordings

      mv  /home/onionid/panel/storage/backup-keys /root/oid_backup/
      ln -s /opt/efs/panel/backup-keys /home/onionid/panel/storage/backup-keys

      mv /home/onionid/panel/storage/framework/sessions  /root/oid_backup/
      ln -s /opt/efs/panel/sessions /home/onionid/panel/storage/framework/sessions

      mv /home/onionid/panel/storage/framework/cache  /root/oid_backup/
      ln -s /opt/efs/panel/cache /home/onionid/panel/storage/framework/cache 

      mv  /home/onionid/panel/storage/user-pub-keys /root/oid_backup/
      ln -s /opt/efs/panel/user-pub-keys /home/onionid/panel/storage/user-pub-keys

      mv /home/onionid/panel/storage/piperlogs  /root/oid_backup/
      ln -s /opt/efs/panel/piperlogs /home/onionid/panel/storage/piperlogs

      mv /home/onionid/panel/public/img/profile_pics  /root/oid_backup/
      ln -s /opt/efs/panel/public/profile_pics  /home/onionid/panel/public/img/profile_pics
   ```
1. Clear cache

   ```bash
      sudo -i -u onionid /usr/bin/php /home/onionid/panel/artisan cache:clear
      sudo -i -u onionid /usr/bin/php /home/onionid/panel/artisan config:clear
      sudo -i -u onionid /usr/bin/php /home/onionid/panel/artisan config:cache
   ```
