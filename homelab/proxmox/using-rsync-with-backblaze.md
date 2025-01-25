# Using rsync with Backblaze

## Setting Up Proxmox Backups with Rclone and Backblaze B2

Backing up your Proxmox VMs and containers is critical for maintaining a secure and reliable environment. This guide will walk you through setting up backups with Rclone and Backblaze B2 cloud storage.

### Step 1: Locate Proxmox Storage

Navigate to the storage directory for your backups:

```
cd /var/lib/vz
ls
pwd
cd dump
pwd
```

Take note of the storage location for your VMs and containers, as this will be required for configuration.

### Step 2: Edit the Proxmox Configuration File

Edit the configuration file of the container you wish to back up:

```
nano /etc/pve/lxc/101.conf
```

Update the file with the mount point for your backup location:

```
arch: amd64
cores: 2
features: nesting=1
hostname: rclone-ubuntu
memory: 512
mp0: /var/lib/vz/dump,mp=/mnt/proxmox-backups
net0: name=eth0,bridge=vmbr0,firewall=1,hwaddr=BC:24:11:70:7D:EE,ip=dhcp,ip6=dhcp,type=veth
ostype: ubuntu
rootfs: local-lvm:vm-101-disk-0,size=8G
swap: 256
unprivileged: 1
```

Check if the mount point works:

```
cd /mnt/proxmox-backups/
ls
```

### Step 3: Install Rclone

Install Rclone to sync backups to a remote server:

```
apt install rclone
```

### Step 4: Set Up a Backblaze B2 Account

1. Navigate to [Backblaze B2](https://www.backblaze.com) and create a free account.
2. Create a bucket with a unique name and leave the default settings.
3. Go to "Application Keys," generate a new application key, and note down the key and account ID.

### Step 5: Configure Rclone

Run the Rclone configuration tool:

```
rclone config
```

Follow the prompts to set up Backblaze B2 as your remote storage:

1. Choose `n` for a new remote.
2. Enter a name for your remote (e.g., `backblaze`).
3. Select `5` for Backblaze B2.
4. Enter your account ID and application key.
5. Set `hard_delete` to `false` (or as per your preference).
6. Confirm the configuration.

Verify the setup:

```
rclone listremotes
```

### Step 6: Sync Files with Rclone

To test syncing, upload a test file to your Backblaze bucket:

```
echo "Subscribe to updates!" > subscribe.txt
rclone sync subscribe.txt backblaze:your-bucket-name/
rclone ls backblaze:your-bucket-name/
```

For full backups, sync your Proxmox storage directory:

```
rclone sync /mnt/proxmox-backups/ backblaze:your-bucket-name/ -P
```

### Step 7: Schedule Automated Backups

1. In the Proxmox UI, create a backup job to run nightly at midnight.
2. Set retention policies under "Retention" to keep a manageable number of daily backups (e.g., total storage capacity × 2).

### Step 8: Add a Cron Job for Frequent Backups

For additional redundancy, you can schedule a cron job to run Rclone backups at 2:00 AM. Open the crontab editor:

```
crontab -e
```

Add the following line to schedule the job:

```
0 2 * * * rclone sync /mnt/proxmox-backups/ backblaze:your-bucket-name/ -P
```

This cron job will run at 2:00 AM.
