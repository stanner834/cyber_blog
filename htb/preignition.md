# Preignition

In this blog post, we dive into web server security, focusing on the importance of web enumeration and directory busting in penetration testing. Using tools like Nmap and Gobuster, we explore methods to uncover hidden web directories and potential vulnerabilities in a target system. We also show how to exploit a default Nginx installation, highlighting the critical need to secure admin panels with strong credentials.

First, let's begin by testing our connection with the target server using the `ping` tool.

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

After a successful connection attempt, we can start the enumeration phase by using the `nmap` tool with the `-sV` switch for version detection. Note that to run these scans, you must use root privileges.

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

We have identified an Nginx web server running on port 80. Copy and paste the IP address into your web browser to access the web page.

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

We find the default page for Nginx. This could mean that the web page is not completely configured yet. One thing we can try is uncovering new directories by enumerating the directory using Gobuster. You can install Gobuster using the following commands:

```
sudo apt install golang-go
go install github.com/OJ/gobuster/v3@latest
```

Note: These did not work for me; I had to use APT instead.

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

Once Gobuster is installed, you can use `gobuster -h` for a list of commands. For this machine, we only need to use the following switches:

* `dir`: specify we are using the directory busting mode of the tool
* `-w`: specify a wordlist, a collection of common directory names typically used for sites
* `-u`: specify the target's IP address

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

Once we run Gobuster, we have identified `admin.php`. Gobuster essentially makes multiple HTTP GET requests to the target domain using different directory names in hopes of identifying a hidden directory.

In your browser, navigate to the `admin.php` site and you will see a new web page. Attempt to log in to the account using default credentials, and the root flag will appear.

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

```
Username: Admin
Password: Admin
```

References:

{% embed url="https://app.hackthebox.com/c24837b0-21f2-4a1f-9820-487a08e63bb6" %}
