<!-- ABOUT THE PROJECT -->
## About The Project


Handling user accounts, especially in a large company, can be a very repetitive and time-consuming task. As the person responsible for creating all these accounts, I realized that we needed a simpler and faster way to bring new employees onboard. That's why I suggested automating and improving our onboarding process.

Here's why:
* Time Efficiency: By automating and streamlining our user account creation process, we'll be able to save a significant amount of time and effort. This means our new employees can get up and running faster, allowing us to operate more efficiently as a whole.
* Accuracy and Consistency: Automation ensures that every user account is created with precision and consistency. This reduces the chances of errors or discrepancies in user profiles, enhancing our data quality and overall security.
* Resource Savings: Automating repetitive tasks will free up our IT team's valuable time and skills. This can be channeled into more strategic projects, ultimately leading to resource savings and a more productive IT department.






### Built With

This project consisted of the following services

* ![Azure](https://img.shields.io/badge/Automate-blue)





<!-- GETTING STARTED -->
## Getting Started

These steps outline the general approach I took to complete this project. While not providing an in-depth look into each step, they serve as a valuable starting point for anyone looking to initiate a similar project.

### Step 1: Creating an Azure Automation Account

Azure Automation provides a cloud-based automation solution that supports the management of operating system updates and configurations. It ensures consistent control and oversight across both your Azure and non-Azure environments.

Please click [this](https://learn.microsoft.com/en-us/azure/automation/automation-create-standalone-account?tabs=azureportal) on how to create and set up your Azure Automation Account.

![Automation Account](https://learn.microsoft.com/en-us/azure/automation/media/automation-create-standalone-account/automation-account-portal.png)


### Step 2: Create a Hybrid Worker Group

Azure Automation Runbooks usually run in the Azure cloud, which can limit their access to resources outside Azure or on-premises. To address this, Azure Automation provides the Hybrid Runbook Worker feature, allowing you to run runbooks on the machine hosting the role for local resource interaction. In my scenario, I ran the runbook on our Domain Controller due to our Hybrid Azure setup. These runbooks are managed in Azure Automation and then sent to assigned machines for execution.

Head over to your Automation Account and under "Process Automation", select "Hybrid Worker Groups". Then select "+ Create hybrid worker group". Follow this [guide](https://learn.microsoft.com/en-us/azure/automation/extension-based-hybrid-runbook-worker-install?tabs=windows%2Cbicep-template) below more details. 

![Hybrid Worker Group](https://learn.microsoft.com/en-us/azure/automation/media/extension-based-hybrid-runbook-worker-install/hybrid-worker-groups-portal.png)

When you reach the point of adding a machine, you'll have the option to include Azure virtual machines, Azure Arc-enabled servers, or Azure Arc-enabled VMware vSphere (preview). However, you might observe that there are no devices available for addition to your Hybrid Worker Group. This is because in my scenerio, we need to ensure that Azure Arc Connected Machine Agent is installed on the Domain Controller. Once this is installed, it will then populate on the list of devices to add. Let's go ahead and learn how to install Azure Arc.

### Step 3: Install the Azure Connected Machine agent on Domain Controller to enable Azure Arc

I used the Azure Portal to generate me a script that automates the downloading and installation of the agent and establishes the connection with Azure Arc.

You can follow this [guide](https://learn.microsoft.com/en-us/azure/network-watcher/connection-monitor-connected-machine-agent?tabs=WindowsScript#generate-an-installation-script) which shows you exactly how to retrieve the script and how to install the agent. 

Once agenet has been added you can go back to adding the newly added Worker Device.

![Image Alt Text](Azure/Hybrid%Worker.png)









## Key Takeaways

* You'll come across numerous access/permission issues, view the logs and the error codes that appear to troubleshoot. For example - ensure you have the necessary permissions for your resource groups; otherwise, you won't be able to add role assignments to your automation account.
* In your Logic App, be certain to include a Hybrid Automation Worker Group in the "Create a job" section.
* When working with your runbook script, meticulously check for typos and eliminate any trailing spaces that could potentially lead to runbook failures.
* If you intend to create a user in the default "user" Organizational Unit (OU), the path should be specified as: CN="Users".

## Next Steps and Future Improvements

* Opt for triggering the Logic App via email, aligning with our current organizational practice.
* Instead of incorporating a "password" entry field in the Forms, explore a secure solution for automatic password generation to mitigate potential security concerns.
* Integrate automation for adding users to groups based on their selected department, ensuring that the appropriate security groups are assigned accordingly.
* Implement an automated email generation process to notify employees once their accounts have been successfully created.