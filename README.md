<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Deployment in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy Active Directory within Azure Compute](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- <strong>Active Directory Configuration:</strong>
Set up an Active Directory server if you don't already have one. You can use Windows Server for this purpose.
Configure your Active Directory by defining your domain, organizational units, and user accounts.
- <strong>User and Group Management:</strong>
Create user accounts and groups within your on-premises Active Directory based on your organization's structure and needs.
Assign appropriate permissions and group memberships to manage access.
- <strong>High-Level Deployment:</strong>
Plan and execute your high-level deployment, which may involve deploying physical or virtual servers, databases, and applications in your on-premises or hybrid environment.
Ensure that your deployed resources integrate seamlessly with your on-premises Active Directory for authentication and access control.
- <strong>Integration and Security:</strong>
Implement security measures to protect your on-premises environment, such as firewalls, intrusion detection systems, and security policies.
Ensure that your deployed resources adhere to best practices for security and compliance.

These steps provide a basic framework for configuring Active Directory and conducting a high-level deployment in a non-Azure environment. The specific details and technologies used will depend on your organization's infrastructure and requirements.

<h2>Deployment and Configuration Steps</h2>

<p>To open the Server Manager program, follow these steps:

1. Press the Windows Logo Key.

In the search bar, type "Server Manager."

Look for the application in the search results and click on it to launch the program.

Locate "Manage" at the top right of the menu bar.

Click on "Manage" and choose "Add Roles and Features" from the dropdown menu.

A pop-up window will promptly appear. This window serves as the <em>installer wizard</em>, guiding you through the setup of roles and features.
</p>
<p>
<img src="https://github.com/GTaylorUS/ConfigureActDirectory/assets/146995823/c26925b6-cd9c-4c61-a469-d8ec70f2d933" height="40%" Width="40%"/>
  <img alt="image" src="https://github.com/GTaylorUS/ConfigureActDirectory/assets/146995823/3e56e6b5-20cf-42ac-ad41-243c382e614b" height="45%" width="45%"/>
</p>

<br />
<p>
2. Next up at the "Installation Type" section, select “Role-based or feature based installation” radio button and then click <strong>Next</strong>.

3. In the "Server Selection" checkpoint, choose the "Select a server from the server pool" radio button. This will display a list of servers installed on your machine. Click once on the desired server to select it. Proceed by clicking <strong>Next</strong>.
</p>

<img src="https://github.com/GTaylorUS/ConfigureActDirectory/assets/146995823/dbce1d03-571d-4fab-aa63-66191f07edd7" height="40%" width="40%">
<img src="https://github.com/GTaylorUS/ConfigureActDirectory/assets/146995823/40e25fe1-c9fa-4e80-a1d1-be18d9ae8af0" height="40%" width="40%">
</p>

<br />
<p>
4. In the "Select Server Roles" section, scroll through the list of available roles for your server. Locate "Active Directory Domain Services". To find it, click on the first role in the list and promptly type "active". This will highlight the relevant role. Once you see "Active Directory Server Roles", click the checkbox to confirm your selection. Proceed by clicking <strong>Next</strong>.

Following that, a pop-up window will appear. This serves as the checkpoint for adding new features. Locate the "Add features" button at the bottom of the window, and click it to reveal a list of available features.

Click <strong>Next</strong> without making modifications to any other settings.
</p>

<p> <img src="https://github.com/GTaylorUS/ConfigureActDirectory/assets/146995823/ea782057-2570-4afc-b41c-12b43f1cd085" height="40%" width="40%">
  <img src="https://github.com/GTaylorUS/ConfigureActDirectory/assets/146995823/a8695240-64bd-4db0-8bdb-1264b4bb33a2" height="40%" width="40%">
</p>
<br />

<p>
5. After completing the previous step, you will be directed to the section for adding the "Active Directory Domain Services" feature. In the installer wizard window, simply click <strong>Next</strong> to proceed. </p>
  
<p> <img src="https://github.com/GTaylorUS/ConfigureActDirectory/assets/146995823/db2bf7af-782c-4486-87f9-82d56be0fb6d" height="40%" width="40%">
</p>

<p>
6. Take a moment to review the summary of your chosen options here. If you notice any errors or wish to make adjustments from previous checkpoints, you can do so by clicking the "Previous" button.

Once you are satisfied with your selections at the "Confirmation" checkpoint, click the <strong>Install</strong> button to proceed.

7. The installation process will commence, and the duration may vary based on your machine's hardware configuration and the selected features. Please avoid interrupting the installation. After the installation is finished, click the <strong>Close</strong> button.
</p>

<p> <img src="https://github.com/GTaylorUS/ConfigureActDirectory/assets/146995823/59699e16-9440-493c-ba9d-f0f56b057079" height="40%" width="40%">
  <img src="https://github.com/GTaylorUS/ConfigureActDirectory/assets/146995823/284be45f-6dc2-4b6b-a1ec-212925371132" height="40%" width="40%">
</p>

<h4>Promoting Your Server to a Domain Controller</h4>

<p>
1. Now that you've added the essential "Active Directory Domain Services" feature, it needs to be promoted to a <strong>Domain Controller (DC)</strong>. Follow these steps:

If you've closed it, reopen "Server Manager". Check for a yellow triangle warning sign near the menu bar at the top right of the Server Manager dashboard. This sign indicates that Active Directory Domain Services was installed correctly.

Click on the warning sign to reveal a dropdown list with necessary post-deployment configuration actions. 

Locate and select the <em>Promote this server to a domain controller</em> option.
</p>

<p> <img src="https://github.com/GTaylorUS/ConfigureActDirectory/assets/146995823/e9a0738c-a2ad-4eaa-92f5-1f61c5de24e4" height="40%" width="40%">
</p>

<h4>Add and Deploy a forest</h4>

<p> 
2. At this stage, a configuration wizard will appear on your screen, serving as your guide for the deployment configuration. The initial step in this configuration process is to add a new forest.

Choose the "Add a new forest" radio button and input your desired root domain name. Then, proceed by clicking <strong>Next</strong> (Note that when adding a new forest, there are multiple options available, and you have the flexibility to select any option from the provided list.)

3. When you reach the "Domain Controller Options" checkpoint, leave all the settings as they are. Enter your password and confirm it. It's crucial to keep a record of this password as changing it later can be cumbersome.
</p>

<p> <img src="https://github.com/GTaylorUS/ConfigureActDirectory/assets/146995823/3844d355-e4b1-4e18-a6d4-b3cf7fe90027" height="40%" width="40%">
<img src="https://github.com/GTaylorUS/ConfigureActDirectory/assets/146995823/97156681-4e96-48ca-957c-36c040747a1d" height="40%" width="40%">
</p>

<h4>Setting and Configuring Domain Controller options</h4>

<p> 4. On the <strong>DNS Options Page</strong>, you may encounter an error message indicating that no parent zone is found, and no delegation for your DNS server could be created. Disregard this message and proceed by clicking the <strong>Next</strong> button, making no changes to the settings at this checkpoint.

5. On the <em>Additional Options</em> page, enter your desired NetBIOS domain name in the given textbox. Click <strong>Next</strong>.

6. Several paths will be displayed on your screen. There's no need to modify these paths, and you're not obligated to record them. Simply click <strong>Next</Next>.
</p>

<p> 
  <img src="https://github.com/GTaylorUS/ConfigureActDirectory/assets/146995823/f59204a6-63a9-41de-9159-7308dc94ef80" height="40%" width="40%">
</p>

<h4>Selection Review</h4>

<p> 
  7. Review the options you've selected thus far on the configuration wizard at this stage. If necessary, use the "Previous" button to return to earlier checkpoints and make any desired adjustments. When you are content with the selected options, proceed by clicking <Strong>Next</Strong> on the <em>Review Options</em> page.
</p>

<p> 
  <img src="https://github.com/GTaylorUS/ConfigureActDirectory/assets/146995823/77da0cf9-80d7-4803-a27a-ecc858a8ce8b" height="40%" width="40%">
</p>

<h4>Run Prerequisites Check</h4>

<p>Now, move to the <em>Prerequisites Check</em> checkpoint. Here, you will determine whether all the prerequisite checks were completed successfully. If any errors are detected, a list of errors will be presented in the window. To address these errors, refer to the indicated checkpoints and make the necessary corrections. Once all errors are resolved, a green checkmark accompanied by a success message will appear. At this point, click <strong>Install</strong> to initiate the installation.</p>

<p><img src="https://github.com/GTaylorUS/ConfigureActDirectory/assets/146995823/faef810b-d0a2-48f9-ba2a-6448d9d3ee17" height="40%" width="40%">
</p>

<p>Congratulations on successfully setting up Active Directory on your Windows Server 2022! To complete the process, your server machine will require a restart once the promotion is successfully completed.

After the restart, log in to your server using the newly created domain and the password you set in the previous steps. Once logged in successfully, you can begin managing Active Directory Domain Services through the administrative center. Additionally, integrate various tools with AD DS and start using them seamlessly.</p>


<br />
