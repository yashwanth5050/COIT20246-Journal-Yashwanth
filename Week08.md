# Week 8 Journal – Cloud Computing

**Student Name:** Yashwanth. **GitHub:** https://github.com/yashwanth5050. **Unit:** COIT20246 Networking and Cyber Security. **Week:** 8. **Topic:** Cloud Computing.

## Activity 1 – Creating Azure Resources

### Objective

This activity was created to help you explore the relationship between the various components of an Azure cloud deployment and to create some Azure resources using the Microsoft Learn on Demand environment.

### Work Completed

Accessed the Azure on Demand temporary Azure account and completed the Azure Fundamentals activities through the Microsoft Learn on Demand environment. The exercise uses a resource group called IntroAzureRG to structure the resources created for the exercise.

The compute resource was a virtual machine that was named my-vm. The deployment, also, needed a virtual network that's going to provide network connectivity, a network interface to connect the virtual machine to a virtual network, a public IP address to make a specific service accessible from the Internet, a Network Security Group that regulates traffic that flows from the Internet into and out of the virtual machine, and a managed disk that holds the operating system and persistent data.

### Interpretation

The activity demonstrated the fact that making one cloud virtual machine requires several related services to be taken into account. The resource group is a logical container that makes it easier to organize, manage and remove those services when the lab is completed.

This activity covers creating a Linux virtual machine and making it accessible on the Web.Activity 2 will guide you in creating a Linux VM and enabling Web access.

### Objective

The aim of this activity was to create an Ubuntu virtual machine, install Nginx on it and then block web traffic via a Network Security Group rule, before re-opening it.

### Work Completed

The resource group, named IntroAzureRG, was created using the az group create command with the name of the group and the location eastus. A virtual machine my-vm was created using az vm create, and resource group IntroAzureRG, size Standard_D2s_v5, Standard public IP SKU, Ubuntu 22.04, administrator username azureuser and generated SSH keys.

You installed Nginx by using Linux Custom Script Extension using az vm extension set with the Microsoft.Azure.The learning activity extensions publisher and configure-nginx.sh script. The same resource group and virtual machine was then used to get the public IP address using az vm list-ip-addresses.

Nginx page was not able to be loaded prior to adding the HTTP rule because inbound TCP port 80 was not allowed by the network security configuration. Next, I added a inbound http rule in the Network Security Group. Once the rule was turned on, the Web service was accessible via its temporary public IP address.

There were two crucial inbound rules that were placed in the activity. Using TCP port 22, they managed to log in to the Linux virtual machine and use the SSH service for administration, and, using TCP port 80, they were able to log in to the web browser and use the Nginx service. Notified of successful connection to the server via SSH as the azureuser. The tutorial also threw in StrictHostKeyChecking=no in case host-key checking was a problem in relation to the lab. I edited /var/www/html/index.html with nano and added my name to the web page.

### Interpretation

This implication was illustrated during the timeout period before the Network Security Group change whereby a running application was not automatically accessible from the Internet. The application will be configured properly and network access will be denied on this occasion as well. Enabling the port (TCP) 80 demonstrated the separation between cloud network security controls and the actual application itself.

Cloud and On-premise costs comparison.Activity 3: Comparing Cloud and On-premintion costs.

### Objective

This activity was to understand the financial and operational considerations comparing different components of a consumer desktop computer with a similarly sized Azure virtual machine.

### Comparison

For the comparison I used a memory class with 16 Gb. The consumer system being used was an A$1149 PCCG AMD Ryzen 5 5500GT Home and Office PC with 16 GB RAM and 1 TB NVMe SSD. To get an indicative running-cost estimate I took a mean draw rate of 150 watts per day, with 8 hours above water, and an electricity rate of $0.35/kWh. This translates to an estimated electricity cost of approximately A$153.30 per year and an approximate total cost over the course of three years of approximately A$1,608.90 (excluding maintenance or replacement costs).

The virtual machine used for the cloud comparison was a 4 virtual CPU, 16 GiB memory Standard_D4s_v5 Linux virtual machine in the Australia East region. The model US price (pay-as-you-go compute) was US$0.240/hour. This equates to around A$0.336 an hour, based on an exchange rate of 1 USD to 1.40142 AUD. The indicative compute-only cost, at 730 hours per month, is about $2946.35 a year or $8839.04 over three years. Taxes, available discounts, and persistent disk storage and data transfer costs may impact the final cost of the cloud.

The desktop comes with an initial hardware investment, but can be cost-effective when it is in use on a regular basis over many years. It also benefits from the inclusion of local storage, and unlike some apps, can continue to function on a basic local task without needing to have Internet access. The drawbacks are: the owner is responsible for power, availability of space, maintenance, hardware replacement and backup.

The cloud virtual machine does not require an upfront purchase of the necessary infrastructure, and can be created, resized and deleted rapidly. It can be helpful for some temporary workloads or services required to have access from various places. The downside is that you will be charged for the use of these resources that are always on, and when you include storage, backup and data transfer fees it will result in some pretty high recurring expenses.

### Interpretation

When the comparison was performed, they discovered that cloud computing is not a given cost savings for all workloads. Cloud services offer flexibility and decrease the requirement to invest in hardware while on-premise equipment may be more cost-effective for consistent workloads that operate over extended periods. The decision of which to choose is determined by usage, extensibility, management complexity, service lifespan and requirement for agility.

## Activity 4 – Azure Storage and Resource Protection

The storage exercises illustrated how Azure Blob data can be either privately available or, if desired of course, publicly accessible. When publicly accessible content is provided, public access should be provided only when necessary since publicly exposed content can be retrieved by anyone with sufficient address.

In addition, Azure resource locks offer another type of administrative protection. While a read-only lock is active, no changes are allowed to the protected resource. A delete lock allows normal modification but prevents deletion. These controls can be helpful in mitigating threats to vital cloud resources inadvertently made by administrators.

## Problems and Troubleshooting

The web-page timeout was the primary trouble shooting concern. Nginx might be working and been trying to connect to inbound port 80, which was still blocked by the Network Security group. A rule to allow HTTP was added to the rule groups, and time was allowed to pass for the rule to take effect to resolve the access problem.

## Weekly Reflection

I have learnt more about cloud computing during week 8 it allows me to see it is about compute, networking, access control, storage and cost management. While the physical infrastructure was abstracted, a cloud server still relies on interfaces, addressing, traffic rules and persistence of storage as the virtual machine was created.

The cost comparison also revealed why Cloud or Local Hardware are appropriate for certain situations and not for others. Cloud resources are flexible and offer quick deployment – however, the cost for continuously run services can add up over time. How this is done is determined by the frequency of usage, the need for speedy scaling and the level of management control the organisation desires.