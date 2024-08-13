# Cloudflare DDNS

I use a DDNS script from the GitHub account below to automatically update my public IP in my Cloudflare DNS records. This is very helpful for running OpenVPN on my Pi, but it was also a fun side project. See the links below for reference; this Network Chuck video is very simple and straightforward. Download the script, configure the file, run a cron job, and you are good to go.

NOTE: Make sure to update `auth_method="global"`. I had to do this to get the script to work properly.&#x20;

References:

{% embed url="https://github.com/K0p1-Git/cloudflare-ddns-updater" %}

{% embed url="https://www.youtube.com/watch?v=rI-XxnyWFnM" %}

