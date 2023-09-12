
<!-- ABOUT THE PROJECT -->
## About The Project

The Windows Local Administrator Password Solution (LAPS) is a Microsoft-provided tool that empowers you to effectively control and regularly update local administrator passwords on Windows devices. Typically, local administrator passwords are identical across all Windows devices by default, presenting a potential security vulnerability. I recognized the need to enhance system security, which led me to initiate the project for implementing Microsoft LAPS within our organization.

LAPS addresses this issue by automatically generating distinct passwords for each device and securing them in Azure Active Directory. Notably, Windows LAPS does not require any specific licensing, as it is accessible to any organization with an Azure AD Free or higher license.

Windows LAPS is now available on the following OS platforms with the specified update or later installed:

* Windows 11 22H2 - April 11 2023 Update
* Windows 11 21H2 - April 11 2023 Update
* Windows 10 - April 11 2023 Update
* Windows Server 2022 - April 11 2023 Update
* Windows Server 2019 - April 11 2023 Update

## Implementation Plan

With Microsoft Intune, I can leverage Endpoint Security to implement LAPS (Local Administrator Password Solution) within our organization. We'll establish a policy containing all the recommended configurations to enhance compliance and bolster security.

### Built With

This project consisted of the following services

![Azure](https://img.shields.io/badge/Azure-Intune-blue)
![Azure](https://img.shields.io/badge/VMWare-Virtual_Machines-blue)

<!-- GETTING STARTED -->
## Getting Started

These steps outline the general approach I took to complete this project. While not providing an in-depth look into each step, they serve as a valuable starting point for anyone looking to initiate a similar project.

### Step 1: Enable Windows LAPS via Intune

1.	Sign in to Azure Active Directory.
2.	Navigate to Devices > Device Settings.
3.	Activate the "Enable Azure AD Local Administrator Password Solution (LAPS)" option by switching it to "Yes."
4.	Ensure you save the changes by clicking the "Save" button.

![Image Alt Text](../Images/Laps1.png)