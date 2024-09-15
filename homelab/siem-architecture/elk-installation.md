# ELK installation

## Setting Up Elasticsearch, Kibana, and Fleet Server on a Single Ubuntu Server

In this guide, we'll walk through the process of setting up a complete Elastic Stack with Elasticsearch, Kibana, and Fleet Server on a single Ubuntu server using DEB packages. This setup is perfect for local testing or a small-scale deployment.

### Prerequisites

* A clean Ubuntu 20.04 or later machine
* Basic understanding of terminal commands
* Root or sudo privileges

### Step 1: Install Elasticsearch

#### 1.1 Add Elasticsearch’s GPG Key

To ensure that the downloaded packages are legitimate, add the GPG key from Elastic's official repository:

```bash
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
```

#### 1.2 Add Elasticsearch’s Repository

Next, add the Elastic Stack repository to your package sources list:

```bash
sudo sh -c 'echo "deb https://artifacts.elastic.co/packages/8.x/apt stable main" > /etc/apt/sources.list.d/elastic-8.x.list'
```

#### 1.3 Install Elasticsearch

Update your package list and install Elasticsearch:

```bash
sudo apt update
sudo apt install elasticsearch
```

During installation, note down the password for the built-in `elastic` superuser account and the command to start Elasticsearch as a service.

#### 1.4 Run Elasticsearch as a Service

Run the command to reload the system daemon and enable Elasticsearch to run as a service:

```bash
sudo systemctl daemon-reload 
sudo systemctl enable elasticsearch.service
```

#### 1.5 Configure Elasticsearch

By default, Elasticsearch binds to `localhost`. To allow external connections, modify its configuration file:

```bash
sudo nano /etc/elasticsearch/elasticsearch.yml
```

Uncomment and modify the following lines (you can identify the IP address of your host by running `ifconfig`):

```yaml
network.host: 192.168.1.1
transport.host: 0.0.0.0
```

#### 1.6 Start Elasticsearch

Start the Elasticsearch service:

```bash
sudo systemctl start elasticsearch.service
```

Verify that Elasticsearch is running:

```bash
sudo curl --cacert /etc/elasticsearch/certs/http_ca.crt -u elastic:$ELASTIC_PASSWORD https://localhost:9200
```

In this command, replace `$ELASTIC_PASSWORD` with the `elastic` superuser password from the install output.

Check the status of the Elasticsearch service:

```bash
sudo systemctl status elasticsearch
```

### Step 2: Install Kibana

#### 2.1 Install Kibana

Install Kibana using the same Elastic Stack repository:

```bash
sudo apt install kibana
```

Generate an enrollment token:

```bash
sudo /usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s kibana
```

#### 2.2 Configure Kibana

Open the Kibana configuration file to point it to your Elasticsearch instance:

```bash
sudo nano /etc/kibana/kibana.yml
```

Update the following lines with the IP address of your host:

```yaml
server.host: 192.168.1.1
```

#### 2.3 Start and Enable Kibana

Enable and start the Kibana service:

```bash
sudo systemctl daemon-reload
sudo systemctl enable kibana.service
sudo systemctl start kibana.service
```

Kibana will be accessible at `http://your_server_ip:5601`.

Check the status of Kibana:

```bash
sudo systemctl status kibana
```

When Kibana starts, it will generate a URL with a 6-digit code. Open the URL to complete the setup. You’ll be prompted to paste the enrollment token generated earlier. Log in using the `elastic` user credentials gathered from Elasticsearch installation.

### Step 3: Secure Elasticsearch and Kibana

#### 3.1 Set Up Built-in Users

Elasticsearch comes with several preconfigured users such as `elastic` and `kibana_system`. You can set their passwords using:

```bash
sudo /usr/share/elasticsearch/bin/elasticsearch-setup-passwords interactive
```

Follow the prompts and note the passwords for the `elastic` and `kibana_system` users.

#### 3.2 Update Kibana with Kibana System User Password

Edit the Kibana configuration to include the password for the `kibana_system` user:

```bash
sudo nano /etc/kibana/kibana.yml
```

Add this line:

```yaml
elasticsearch.username: "kibana_system"
elasticsearch.password: "your_kibana_system_password"
```

Restart Kibana to apply the changes:

```bash
sudo systemctl restart kibana
```

### Step 4: Install and Set Up Fleet Server

Fleet Server is the central management point for Elastic Agents. Let's install and configure it.

#### 4.1 Install Elastic Agent

First, download and install the Elastic Agent:

```bash
wget https://artifacts.elastic.co/downloads/beats/elastic-agent/elastic-agent-8.15.1-amd64.deb
sudo dpkg -i elastic-agent-8.15.1-amd64.deb
```

#### 4.2 Generate a Fleet Enrollment Token

In Kibana, navigate to **Fleet > Agents** and click **Add agent**. Choose to run Fleet Server on this host and generate a service token. Copy the token for use in the next step.

#### 4.3 Enroll Elastic Agent as Fleet Server

Run the following command to enroll the Elastic Agent and start Fleet Server:

```bash
sudo elastic-agent install \
  --fleet-server-es=https://localhost:9200 \
  --fleet-server-service-token=YOUR_SERVICE_TOKEN \
  --fleet-server-policy=fleet-server-policy \
  --fleet-server-es-ca-trusted-fingerprint=YOUR_FLEET_SERVER_CA_FINGERPRINT
```

* Replace `YOUR_SERVICE_TOKEN` with the service token generated in Kibana.
* Replace `YOUR_FLEET_SERVER_CA_FINGERPRINT` with the CA fingerprint for your Elasticsearch instance.

Once successfully enrolled, the Fleet Server will be up and running.

### Step 5: Verify Your Setup

#### 5.1 Check Elasticsearch Status

Ensure Elasticsearch is running correctly:

```bash
curl -X GET "http://localhost:9200/"
```

#### 5.2 Check Kibana

Access Kibana in your browser at `http://your_server_ip:5601` and log in with the `elastic` user and password.

#### 5.3 Check Fleet Server Status

In Kibana, go to **Fleet > Agents** and verify that the Fleet Server is listed as healthy.



ADD SECTION FOR INSTALLING FLEET

ADD SECTION FOR ADDING AGENTS

### Conclusion

You've successfully set up Elasticsearch, Kibana, and Fleet Server on a single Ubuntu server using DEB packages. With this foundation, you can start managing Elastic Agents across your environment and expand your stack with additional Elastic features like Observability and Security.

{% embed url="https://www.elastic.co/guide/en/elastic-stack/current/installing-stack-demo-self.html" %}
