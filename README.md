# Cloud_computing_with_aws


![img.png](img.png)

# What is cloud computing?
Cloud computing is a technology that allows users to access and use computing resources, such as servers, storage, applications, and services, over the internet. These computing resources are provided by third-party providers who manage and maintain the infrastructure necessary to deliver these services.

In cloud computing, users can access computing resources on demand, pay for what they use, and scale up or down their resources as needed. This allows businesses and individuals to avoid the costs and complexities of maintaining their own infrastructure and to focus on their core activities.





# Create an account

- Step 1 open AWS console and enter log in credentials that have been given to us by shahrukh.
- Remember to change your password when the account is created.
- Once you're in change your region to ireland.


# Capex & Opex


operation expenditure vs Capital expenditure (OpEx vs CapEx).Capital expenditure: Will need to by servers, cable, networking equipment whereas Operation expenditure allows us to forgo this and pay for what we use. Which provides companies with very high levels of flexibility. Companies using it:Many of these companies use it in a similar way, but Netflix for example uses CDN CloudFront to tell your geographic location and share content accordingly. Checks IP address. Sage maker for machine learningSummary:To summarise, although there will always be a market for traditional computing, cloud computing has definitely changed the industry and the way companies approach their computing infrastructure. 

[

# The three main types of cloud services are.

- Infrastructure as a Service (IaaS): Provides virtualized computing resources, such as servers, storage, and networking, that can be rented and accessed over the internet. With IaaS, users are responsible for managing and securing their own applications and data.


- Platform as a Service (PaaS): Provides a platform for building and deploying software applications without the need to manage the underlying infrastructure. PaaS typically includes application development tools, databases, and middleware.



- Software as a Service (SaaS): Provides access to software applications over the internet, with the infrastructure and maintenance handled by the service provider. SaaS applications are typically accessed through a web browser.



# The diffrent types of cloud.

- Public cloud: A public cloud is a cloud computing service that is made available to the general public over the internet. It is owned and operated by a third-party cloud service provider, and is hosted on their infrastructure. Public clouds are generally the most cost-effective option for businesses, as they allow for the sharing of resources and costs among multiple users. Examples of public cloud services include Amazon Web Services (AWS), Microsoft Azure, and Google Cloud Platform.



- Private cloud: A private cloud is a cloud computing service that is hosted on a private network. It is owned and operated by a single organization, and is typically hosted on their own servers or data centers. Private clouds provide organizations with greater control and security over their data and applications, as they are not shared with other users. Examples of private cloud services include VMware vCloud, Microsoft Azure Stack, and OpenStack.
 


- Hybrid cloud: A hybrid cloud is a cloud computing service that combines elements of both public and private clouds. It allows organizations to use both public and private cloud services, depending on their specific needs. Hybrid clouds provide organizations with the flexibility to use the best of both worlds, allowing them to take advantage of the cost savings of public clouds while still maintaining control and security of their data and applications. Examples of hybrid cloud services include Microsoft Azure Stack, IBM Cloud Private, and Oracle Cloud Infrastructure.


## What is the difference? 

The main differences between these three types of cloud service are the level of control and responsibility that the user has over the underlying infrastructure. With IaaS, the user has the most control over the infrastructure, but also has the most responsibility for managing it. With PaaS, the user has less control over the infrastructure, but can focus more on building and deploying applications. With SaaS, the user has the least control over the infrastructure, but can simply use the software application without worrying about infrastructure or maintenance.

Additionally, there are different deployment models for cloud services, including public, private, and hybrid cloud. Public cloud services are available to the general public and are owned and operated by a third-party cloud provider. Private cloud services are used by a single organization and are typically managed in-house or by a third-party service provider. Hybrid cloud services are a combination of public and private cloud, providing the benefits of both.

## Two tier architectures 
A two-tier architecture is a common pattern for building web applications and services on AWS. In this architecture, the application is divided into two layers: a presentation layer and a data layer.

There are several reasons why a two-tier architecture is important on AWS:

- Scalability: By separating the presentation and data layers, you can scale each layer independently based on its unique requirements. This allows you to handle more traffic and data without affecting the performance of the other layer.



- Security: Separating the presentation and data layers can also improve security. By isolating the data layer, you can ensure that sensitive data is protected and access is restricted only to authorized users.



- High availability: A two-tier architecture can also help ensure high availability of your application. By using load balancers and auto-scaling groups, you can distribute traffic across multiple instances of your presentation layer, and if one instance fails, traffic can be automatically rerouted to other healthy instances.



- Maintenance: Separating the presentation and data layers can make it easier to perform maintenance tasks such as updating software or applying security patches. By isolating each layer, you can avoid disrupting the entire application during maintenance.



- For DevOps engineers, a two-tier architecture provides several benefits:

- Automation: By using AWS services such as Elastic Beanstalk, CloudFormation, and CodeDeploy, DevOps engineers can automate the deployment and scaling of the presentation and data layers. This allows them to focus on improving the application and delivering new features.



- Monitoring: DevOps engineers can use AWS services such as CloudWatch and X-Ray to monitor the performance of the presentation and data layers. This allows them to identify issues and optimize the application for better performance.



- Resilience: DevOps engineers can use AWS services such as Route 53 and AWS Certificate Manager to ensure that the application is resilient and highly available. This reduces the risk of downtime and improves the user experience.



In summary, a two-tier architecture is important on AWS because it provides scalability, security, high availability, and easier maintenance. It also benefits DevOps engineers by providing automation, monitoring, and resilience.


![img_6.png](img_6.png)

# Requirements 

  App tier deployed -> available on public IP
   - Create 2nd tier with required dependencies: Ubuntu 18.04, mongodob installed, change mongod.conf 0.0.0.0.
- Need a security group for our database - allow 27017 from anywhere - allow only from app instance
    - Go back to the app and create an environment variable with the database endpoint
    - Relaunch the app
    - Securing architecture with firewalls
 - Separate firewall to app, seperate firewall to database
 - App is exposed to the world, database is exposed only to app, limiting access to database
 ## Steps

- Make an Ec2 instance 
- when you get to security group all we need to add is port 27017 because this the port of our database.
- Now that you have done that your instance should be readyand we now need to ssh into it.
- To do this we need to ensure our instance is selected and once it has go to the top right and hit connect.
- You will be bought to a new page and you need to hit `ssh client` and follow the steps on that screen.
- once you have ssh into the terminal you not want to run `git clone` and clone into your repo 
- you now want to run the following commands in this order to run mongo db.
- `sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv D68FA50FEA312927`
- `echo "deb https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list`
- `sudo apt-get update -ysudo apt-get upgrade -y`
- `sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20`
- Now we want to do a resart by doing `sudo systemctl restart mongod`
- Then do `sudo systemctl enable mongod`
- now you want to run a status check by doing `sudo systemctl status mongod`
- this should now be in an active state.
`