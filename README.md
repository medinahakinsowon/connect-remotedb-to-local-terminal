# connect-remotedb-to-local-terminal




First

Create a db on aws console (rds) with the port 3306 open

database---mariadb
free-tier
self-managed
enter password
give db name

secondly

create an ec2 instance with ssm-connection. This creates the tunnel to connect your local

terminal with your remote db

thirdly

Install mysql workbench on your local work station

https://www.mysql.com/products/workbench/

Fourthly

Install session-manager-plugin on your local terminal

https://docs.aws.amazon.com/systems-manager/latest/userguide/install-plugin-debian-and-ubuntu.html

Then connect the terminal with the db (rds) 
aws ssm start-session \
    --region <your region> \
    --target <your bastion instance id> \
    --document-name AWS-StartPortForwardingSessionToRemoteHost \
    --parameters host="<your rds endpoint name>",portNumber="1433",localPortNumber="1433"

Now, go to the mysql workbench console
link the remote db
using the local port "1433" username "admin" password "the one you use to create your db"

