# Introduction
RabbitMQ is a popular message broker typically used for building integration between applications or different components of 
the same application using messages. RabbitMQ is written in Erlang and has drivers/clients available for most major languages.

# RabbitMQ install steps (for windows)

**Following are the steps to install RabbitMQ locally.**

1. **Install Erlang :**
RabbitMQ has dependency on Erlang, so it is required to be installed before RabbitMQ.
So before downloading erlang, please check compatible version for rabbitmq and erlang at https://www.rabbitmq.com/which-erlang.html
Download the appropriate version of erlang from http://www.erlang.org/downloads
Once downloaded, right click on install file e.g. otp_win64_20.3.exe, go to properties and uncheck if blocking option is enabled (if available at bottom, else ignore)
To install, right click on install file and **choose run as an administrator**. This is very important step as mentioned in 
https://www.rabbitmq.com/install-windows.html (see section Install the server)

2. **Install rabbitmq :** 
Get the rabbitmq from https://www.rabbitmq.com/install-windows.html (make sure its compatibility with erlang).
You can download any of installer from Bintray of Github.
Once downloaded, right click on install file, go to properties and uncheck if blocking option is enabled (if available at bottom, else ignore)
To install, right click on install file and **choose run as an administrator**.

3. **Enable management console :**  
**(open command prompt in administrator mode)**,
then go to sbin dir of rabbit mq installation and execute rabbitmq-plugins.bat enable rabbitmq_management as below: 

*C:\Program Files\RabbitMQ Server\rabbitmq_server-3.7.4\sbin>rabbitmq-plugins.bat enable rabbitmq_management* 

That prints message as:	
  
  ```
	Enabling plugins on node rabbit@A6034709:
	rabbitmq_management
	The following plugins have been configured:
  		rabbitmq_management
  		rabbitmq_management_agent
  		rabbitmq_web_dispatch
	Applying plugin configuration to rabbit@A6034709...
		The following plugins have been enabled:
  			rabbitmq_management
  			rabbitmq_management_agent
  			rabbitmq_web_dispatch

	set 3 plugins.
	Offline change; changes will take effect at broker restart.
  ```
  
4. **Restart the service :**
From windows start menu, find the Rabbitmq stop and start commands. Using them restart the rabbitmq server.
*If normal stop and start does not work, try them in administrator mode*

5. **Access rabbitmq console :**
Open in browser http://localhost:15672 to access the management console.
The defualt credentials are guest/guest.

Note: The above steps work with windows 10 as well.

