[title]: # (Master Node Setup)
[tags]: # (remote access controller)
[priority]: # (3)
# Steps to Configure Master Node On-premises Environment

1. Mount NFS Filesystem on Folder `/opt/efs`. This has been completed by you if you have followed the instructions under [Setup a Standalone NFS Server](nfs.md).
1. Copy files to new `/opt/efs` from `/opt/efs_old`

   ```bash
      cp -prv /opt/efs_old/piper /opt/efs/piper
      cp -prv /opt/efs_old/panel /opt/efs/panel
      cp -prv /opt/efs_old/vault /opt/efs/vault
   ```
1. Create a backup directory

   ```bash
      mkdir /root/oid_backup
   ```
1. Copy panel files to new `/opt/efs` and create soft links

   ```bash
      cp -prv /home/onionid/panel/storage/vault/* /opt/efs/panel/vault/
      mv /home/onionid/panel/storage/vault /root/oid_backup/
      ln -s /opt/efs/panel/vault /home/onionid/panel/storage/vault
   
      cp -prv /home/onionid/panel/storage/videos/* /opt/efs/panel/videos/
      mv /opt/efs/panel/videos /root/oid_backup/
      ln -s /opt/efs/panel/videos /home/onionid/panel/storage/videos
   
      cp -prv /home/onionid/panel/storage/org-keys/* /opt/efs/panel/org-keys/
      mv /home/onionid/panel/storage/org-keys  /root/oid_backup/
      ln -s /opt/efs/panel/org-keys /home/onionid/panel/storage/org-keys
   
      cp -prv /home/onionid/panel/storage/windows/rdp/fetch/* /opt/efs/panel/rdp/fetch/
      mv  /home/onionid/panel/storage/windows/rdp/fetch /root/oid_backup/
      ln -s /opt/efs/panel/rdp/fetch /home/onionid/panel/storage/windows/rdp/fetch
   
      cp -prv /home/onionid/panel/storage/windows/rdp/reset/* /opt/efs/panel/rdp/reset/
      mv  /home/onionid/panel/storage/windows/rdp/reset /root/oid_backup/
      ln -s /opt/efs/panel/rdp/reset /home/onionid/panel/storage/windows/rdp/reset
   
      cp -prv /home/onionid/panel/storage/recordings/* /opt/efs/panel/rdp/recordings/
      mv /home/onionid/panel/storage/recordings  /root/oid_backup/
      ln -s /opt/efs/panel/rdp/recordings /home/onionid/panel/storage/recordings
   
      cp -prv /home/onionid/panel/storage/backup-keys/* /opt/efs/panel/backup-keys/
      mv  /home/onionid/panel/storage/backup-keys /root/oid_backup/
      ln -s /opt/efs/panel/backup-keys /home/onionid/panel/storage/backup-keys
   
      cp -prv /home/onionid/panel/storage/framework/sessions/* /opt/efs/panel/sessions/
      mv /home/onionid/panel/storage/framework/sessions  /root/oid_backup/
      ln -s /opt/efs/panel/sessions /home/onionid/panel/storage/framework/sessions
   
      cp -prv /home/onionid/panel/storage/framework/cache/* /opt/efs/panel/cache/
      mv /home/onionid/panel/storage/framework/cache  /root/oid_backup/
      ln -s /opt/efs/panel/cache /home/onionid/panel/storage/framework/cache 
   
      cp -prv /home/onionid/panel/storage/user-pub-keys/* /opt/efs/panel/user-pub-keys/
      mv  /home/onionid/panel/storage/user-pub-keys /root/oid_backup/
      ln -s /opt/efs/panel/user-pub-keys /home/onionid/panel/storage/user-pub-keys
   
      cp -prv /home/onionid/panel/storage/piperlogs/* /opt/efs/panel/piperlogs/
      mv /home/onionid/panel/storage/piperlogs  /root/oid_backup/
      ln -s /opt/efs/panel/piperlogs /home/onionid/panel/storage/piperlogs
   
      cp -prv /home/onionid/panel/public/img/profile_pics/* /opt/efs/panel/public/profile_pics/
      mv /home/onionid/panel/public/img/profile_pics  /root/oid_backup/
      ln -s /opt/efs/panel/public/profile_pics  /home/onionid/panel/public/img/profile_pics
   ```
1. Clear cache

   ```bash
      sudo -i -u onionid /usr/bin/php /home/onionid/panel/artisan cache:clear
      sudo -i -u onionid /usr/bin/php /home/onionid/panel/artisan config:clear
      sudo -i -u onionid /usr/bin/php /home/onionid/panel/artisan config:cache
   ```
