[title]: # (Standalone NFS Server)
[tags]: # (remote access controller)
[priority]: # (2)
# Setup a Standalone NFS Server

## Requirements

__OS__: Ubuntu 16.04 (refer to https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-16-04)  

## Step 1 — Downloading and Installing the Components

Please execute below commands to install `nfs-kernel-server` service.

```bash
   apt-get update
   apt-get install nfs-kernel-server
```

## Step 2 — Creating the Share Directories

Create a directory with name `/var/nfs/efs`

```bash
   mkdir /var/nfs/efs
```

## Step 3 — Configuring the NFS Exports

Open the `/etc/exports` file in your text editor with root privileges and add
following lines

```bash
   /var/nfs/efs       192.168.122.50(rw,sync,no_root_squash,no_subtree_check)
   /var/nfs/efs       192.168.122.51(rw,sync,no_root_squash,no_subtree_check)
```

`192.168.122.50` and `192.168.122.51` are private IP of Thycotic panel instances.

These IP addresses may be different for your installation.

Restart the NFS server with the following command:

```bash
   systemctl restart nfs-kernel-server
```

## Step 4 — Adjusting the Firewall

Allow NFS traffic on port 2049 from our OID panel instances using below command.

```bash
   ufw allow from 192.168.122.50 to any port nfs
   ufw allow from 192.168.122.51 to any port nfs
```
`192.168.122.50` and `192.168.122.51` are private IP of OID panel instances.

## Attach a NFS Mount to the Onion ID bash VM

To mount nfs folders in panel instances, we need to do following steps

1. Open file **/etc/fstab**

   ```bash
      vi /etc/fstab
   ```
1. Add following line to file

   ```bash
      192.168.122.136:/var/nfs/efs /opt/efs   nfs auto,nofail,noatime,nolock,intr,tcp,actimeo=1800 0 0
   ```
   `192.168.122.136` is the NFS server IP and `/var/nfs/efs` is the remote directory in NFS server. This directory will be shared between instances.
1. Initiate mount by executing following command.

   Move existing `/opt/efs` folder to `/opt/efs_old` and create new folder

   ```bash
      mv /opt/efs /opt/efs_old
      mkdir /opt/efs
   ```
1. Enable mount by following command

   ```bash
      mount -a
   ```
1. Verify the operatin by executing following command

   ```bash
      df -h
   ```

### Output

```bash
   root@station:~/.ssh# df -h
   Filesystem                    Size  Used Avail Use% Mounted on
   udev                          2.9G     0  2.9G   0% /dev
   tmpfs                         585M   67M  519M  12% /run
   /dev/sda1                      42G  8.1G   32G  21% /
   tmpfs                         2.9G  472K  2.9G   1% /dev/shm
   tmpfs                         5.0M     0  5.0M   0% /run/lock
   tmpfs                         2.9G     0  2.9G   0% /sys/fs/cgroup
   tmpfs                         585M     0  585M   0% /run/user/0
   none                           42G  8.1G   32G  21% /var/lib/docker/aufs/mnt/54959a050f8a629d6ee8dbe9847359b952083df275bdd4289fbebb3fbc1b13ba
   shm                            64M     0   64M   0% /var/lib/docker/containers/2bd8dce004accd6e336eb79784f4d0079483888864cf23636369c8231e128e6e/shm
   none                           42G  8.1G   32G  21% /var/lib/docker/aufs/mnt/d3749ecb0d5a6e4806e92b50d83cf5242798a1aee06bba6b213d7bf05b7d0bab
   shm                            64M     0   64M   0% /var/lib/docker/containers/0991724c9b667703f47a3effbbb1162f4f2b599d8ff9d6221253b1efa54d742a/shm
   192.168.122.136:/var/nfs/efs   14G  1.5G   12G  12% /opt/efs
```

`192.168.122.136:/var/nfs/efs 14G 1.5G 12G 12% /opt/efs` confirms that the NFS mount was successful.
