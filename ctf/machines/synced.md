# Synced

In this blog, we will go through how to enumerate and exploit an `rsync` service, a popular file transfer tool often used as an alternative to FTP. Rsync is known for its ability to only transfer modified files by identifying the deltas, making it a more efficient tool for syncing files. However, these features can also be exploited if proper security measures are not in place. Let's walk through a simple enumeration and exploitation scenario using rsync.

#### Step 1: Initial Enumeration Using Nmap

First, we need to enumerate the target machine to identify any open ports or running services. We will use Nmap to perform service version detection and run default scripts:

```bash
nmap -sV -sC <target_ip>
```

In this command:

* `-sV` enables version detection.
* `-sC` runs default scripts, which can provide additional information about the services running on the machine.

When the command completes, we see that **port 873** is open, which is the default port for `rsync`.

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

#### Step 2: Understanding Rsync

Rsync is typically pre-installed on most Linux distributions, and its common usage syntax looks like this:

```bash
rsync [OPTION] … [USER@]HOST::SRC [DEST]
```

Rsync transfers files using a remote connection and spawns a receiver process on the host, making it possible to exploit if misconfigured. You can review the available rsync commands on the [official man page](https://linux.die.net/man/1/rsync).

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (2).png" alt=""><figcaption></figcaption></figure>

#### Step 3: Listing Available Directories

Now that we know the rsync service is running, the next step is to try and list all available directories accessible to an anonymous user. We can do this using the `--list-only` option in rsync:

```bash
rsync --list-only rsync://<target_ip>/
```

If the server allows anonymous access, the command will return a list of available directories. In this example, we find a directory called **public**.

<figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

#### Step 4: Listing Files in the Public Share

Once we've identified the **public** directory, we can list its contents to see if there are any interesting files. Use the following command to list files inside the public directory:

```bash
rsync --list-only rsync://<target_ip>/public
```

This reveals the contents of the public directory, and we notice a **flag** file present in the list.

<figure><img src="../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

#### Step 5: Exfiltrating the Flag

With the flag file in sight, the next logical step is to copy or sync it to our local machine. Rsync makes this easy with the following command:

```bash
rsync rsync://<target_ip>/public/flag.txt /path/to/local/destination/
```

This command will sync the flag file from the public directory on the target machine to your local destination.
