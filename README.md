# Automated-Configuration-of-Zabbix-Agent-2-using-Ansible-Playbooks-Offline
This guide will provide you with the necessary steps to install and utilize Zabbix Agent 2 for data collection and transmission to your proxy in an offline environment.

![image](https://user-images.githubusercontent.com/129797537/231611270-cd9aa611-a778-40f5-9445-21f5f0bb3a63.png)

# Introduction :

To start, it's important to understand why Ansible is a valuable tool for server configuration management. It can be a difficult and tedious process to manually install and configure servers, which is why Ansible is used to simplify and streamline this process. Additionally, Ansible requires minimal resources, as it only needs to be installed on a single host server and can then be used to manage other servers.

# Install zabbix agent 2 :
For many reasons of security, we avoid allowing internet servers so that why we will install a zabbix-agent 2 and put it in /tmp.

On host server:

![image](https://user-images.githubusercontent.com/129797537/231609051-26d8f8f1-9d0f-46d2-8541-a83f57a5f9f7.png)

Now in Ansible directory we will set up a playbook to install the agent in other servers:

![image](https://user-images.githubusercontent.com/129797537/231609310-04719c96-ad2c-4613-8fe6-c39fca9a5a2c.png)

We will include a YAML script to facilitate the installation of the Zabbix Agent.

![image](https://user-images.githubusercontent.com/129797537/231609645-1eda6869-4968-4075-b88d-c612786939d7.png)

After that we launch this command to start the installation:

![image](https://user-images.githubusercontent.com/129797537/231609775-5f1da554-f2b0-44fa-ba61-dcffd2c926cf.png)

To enable the Zabbix Agent to begin collecting information, we need to configure the connection information for the agent and the proxy. The configuration process will be automated using Ansible, so there's no need to worry. The relevant configuration file is located at /etc/zabbix/zabbix_agent2.conf.

Let create a file on the host server and put this configuration and send it to all your clients servers:

![image](https://user-images.githubusercontent.com/129797537/231609990-3c72b408-495f-4a7e-b7a3-1ab6a7d70caf.png)

![image](https://user-images.githubusercontent.com/129797537/231610108-1f2319f8-a0fb-4e90-a602-c3f629029c3c.png)

And now we will create a new playbook in /etc/Ansible to send this configuration and start the service:

![image](https://user-images.githubusercontent.com/129797537/231610285-8dc137e0-ee2f-40f7-9e4c-6c8d736bbdff.png)

![image](https://user-images.githubusercontent.com/129797537/231610416-2ad83292-9914-44c1-ad63-91bde83ff4af.png)


Now that the Zabbix Agent has been successfully installed on all of your client servers, the process is complete.
