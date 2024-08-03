# MongoDB

MongoDB is a non-relational, open-source database management system (DBMS) that stores data as JSON documents in a flexible format.

MongoDB differs from relational database systems like MySQL, which store data in structured tables, by using documents instead of tables and rows. MongoDB documents are composed of key-value pairs and can store various types of data, including multivariate data types. The documents can vary in size and can include any number of fields.

Let's start by testing our connection using ping and running nmap to determine the running services on the machine. For this example, we will use the following nmap commands:

* `-p-`: This flag scans all TCP ports ranging from 0-65535.
* `-sV`: Attempts to determine the version of the service running on a port.
* `--min-rate`: Specifies the minimum number of packets that Nmap should send per second; it speeds up the scan as the number increases.

<figure><img src="../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

We have identified MongoDB running on port `27017`. We can try to connect to this DB using the MongoDB application. First, we need to download it from the internet:

```bash
curl -O https://fastdl.mongodb.org/linux/mongodb-linux-x86_64-3.4.7.tgz
tar xvf mongodb-linux-x86_64-3.4.7.tgz
cd mongodb-linux-x86_64-3.4.7/bin
```

<figure><img src="../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

When we try to connect to the database without any credentials, we are granted access. We can start using the `mongo` shell to interact with the database. MongoDB utilizes a JavaScript interface for communication. We can start by running `show dbs`.

<figure><img src="../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>

```javascript
use sensitive_information;
show collections;
```

This will list all the current collections in the database. We identify a `flag` collection, which we can read to complete this machine.

<figure><img src="../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>

References:

{% embed url="https://app.hackthebox.com/20e9bb13-9eb7-4b4a-8471-1dbdaefa2120" %}
