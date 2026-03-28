# Section 3: Data Loss Prevention (DLP) with Microsoft Purview

Important: If there is an insider threat they will find a way to steal and leak data. DLP policies are meant to prevent accidents.
----------------------------------------------------------------------------------

## DLP policies, roles, and permissions overview:

#### Identify and monitor sensitive information across a range of platforms. 
  - Exchange Online e-mails
  - SharePoint Online and OneDrive files and folders
  - Files and chats in Microsoft Teams
  - Devices if onboarded through Endpoint DLP



#### Compliance with regulatory requirements use cases 
  - Protect credit card information (PCI-DSS) - Block external sharing of documents or emails containing credit card information.
  - Protecting healthcare data (HIPAA) - Detecting and preventing the sharing of medical terms and patient information via email or Teams.
  - Ensure the safety of national identification numbers (e.g., SSNs, NINs) - Alert or block emails containing Social Security or tax identification numbers. 
	
#### Examples of internal corporate policies 
  - Block non-CFO employees from sharing quarterly results stored in SharePoint Online to prevent accidental sharing of financial reports.
  - Enhance the protection of executive communications - Implement more strict controls over email communications and files shared by board members and executives.
  - Endpoint DLP can be used to restrict the uploading of sensitive data to personal cloud storage services such as Dropbox or Google Drive. 
	
#### Use cases specific to a particular geographical regions or business units
  - Protect sensitive data from being shared with non-GDPR countries by EU users - Identify and prevent data transfer violations that may violate the GDPR.
  - Enhance HR and Legal policies to ensure that only authorized individuals are able to access and share employee records or contracts.

#### Use cases for devices and endpoints 
  - Protect sensitive files from being copied to USB drives - Prevent sensitive files from being exfiltrated via removable storage devices.
  - Do not allow users to print documents containing internal project code names, financial forecasts, etc.
  - Detect screen capture attempts - Monitor or block screenshots of documents tagged with sensitive labels (if integrated with sensitivity labeling). 

#### Examples of communication oversight 
  - Stop external sharing of NDAs (non-disclosure agreements) protected content by enforcing a policy that detects keywords and phrases from NDAs and prevents the exchange of emails or files between parties.
  - To reduce false positives, notify users before sending sensitive data - Use policy tips in Outlook and Teams to educate users.

#### Custom or Industry-Specific Use Cases 
  - Use custom sensitive information types or keywords to prevent unauthorized sharing of engineering schematics or CAD files.
  - Maintain a list of active legal cases stored in SharePoint libraries by establishing a custom policy.
  - Block attempts to copy, paste, or upload code files from engineers' laptops using Endpoint DLP.

#### DLP with emails in Exchange online: 
  - Monitors email messages and attachments in real time.
  - Detects when users try to send sensitive info (e.g., credit card numbers, financial data) externally or to unauthorized users.
    - Can: Block or encrypt the email.
    - Send policy tips to warn the sender.
    - Trigger incident reports to admins.
  - Trigger incident reports to admins.

#### DLP with files and folders in SharePoint and OneDrive:
  - Scans files stored or shared in SharePoint sites and OneDrive for Business accounts. 
  - Detects sensitive content like PII, financial, or health data. 
  - Policies can:
      - Restrict sharing with people outside your organization.
      - Automatically block download or access.
      - Alert users with policy tips in Office apps (Word, Excel, PowerPoint). 
  - Works whether the file is actively being shared or just sitting in storage.


#### DLP chats and files in Microsoft Teams:
  - Monitors chat messages and files shared in 1:1, group, and channel chats.
  - Helps prevent accidental or intentional leakage of sensitive info (like sending a payroll document to the wrong team).
  - DLP applies to messages sent through:
    - Teams desktop and web clients.
    - Mobile app (for supported features).
  - If a violation is detected: 
    - Message can be blocked from sending.
    - A notification is shown to the user (policy tip).


#### Devices via Endpoint DLP:
  - Extends DLP protection to Windows client devices onboarded through Microsoft Defender for Endpoint.
  - Monitors actions taken on files containing sensitive data:
  - Copying to USB drives 
    - Printing
    - Uploading to personal cloud apps
    - Copy/paste to unauthorized apps 
  - Can block, audit, or warn depending on policy. 
  - Adds visibility and control even before data leaves the device, complementing cloud-based DLP.

#### Roles and permissions related to Data Loss Prevention (DLP) within Microsoft 365:
  1. Roles Overview:
  - Various built-in roles that manage DLP policies are discussed, including:
    - Client Compliance Administrator: Full access to manage DLP across the platform.
    - Compliance Data Administrator: Manages sensitive data across SharePoint, Exchange, and OneDrive.
    - Information Protection Admin: Oversees DLP sensitivity labels and classification settings.
		
  2. Limited Permission Roles:
  - Information Reader: Can view DLP alerts and reports but cannot modify policies.
  - Security Administrator: Has some access to DLP but cannot create or edit policies without additional permissions.
  - Security Reader: Can monitor DLP alerts but lacks modification abilities.
  - Global Administrator: Has comprehensive access to all features, including DLP.
		
  3. Custom Roles: create custom roles to meet specific organizational needs, allowing tailored permissions.
	
  4. Critical Roles: first three roles (Client Compliance Administrator, Compliance Data Administrator, and Information Protection Admin) are the most essential for effective DLP management.
	
  5. Administration Guidance: navigating to Microsoft admin portal to manage these roles, including assigning and creating custom roles.


Data governance roles and permissions in Microsoft Purview
https://learn.microsoft.com/en-us/purview/data-governance-roles-permissions

----------------------------------------------------------------------------------

## Create DLP policy

Microsoft Purview > Data Loss Prevention > Policies

\+ Create policy

	1. Template or custom policy
		- Choose category (Financial, Medical, Privacy, Custom. etc.)
			- Financial
		- Regulations
			- U.K. Financial
				- Will detect and protect: credit card number, EU debit card, SWIFT code
	2. Name
		- Name: U.K. Financial Data
		- Description: 
	3. Admin units
		- Assign admin unit (Entra ID)
		- Or full directory (assign to all)
	4. Locations
		 - Choose where to apply:
			- Exchange, SharePoint, OneDrive, Teams, Device, Fabric and Power BI workspaces, Etc.
			- Can also edit them (exclude or include specific groups)
		- Further configurations available and can add additional STIs, as well as set assign confidence level
		- Policy actions
			- Send tips to users when triggered
			- Add automated action, customize, and configure 
			- Set up alert, severity, report, etc.
		- Restrict access or encrypt the content in Microsoft 365 locations
		- Customize access and override settings
	5. Policy settings
		- Define policies settings
			- Default or custom
	6. Policy mode
		- Run the policy in simulation mode
		- Turn on
		- Leave off
	7. Finish

<img width="1403" height="928" alt="image" src="https://github.com/user-attachments/assets/54ed5527-32ab-401b-a29d-b368a46f8056" />

May take up to an hour before deployed

<img width="2547" height="816" alt="image" src="https://github.com/user-attachments/assets/df5e027d-3a0c-491f-b166-1b58af475ff5" />

Create and deploy data loss prevention policies - https://learn.microsoft.com/en-us/purview/dlp-create-deploy-policy

----------------------------------------------------------------------------------

## Adaptive protection with DLP

Adaptive Protection is a dynamic, intelligence-based (ML) feature that automatically adjusts the enforcement of DLP policies based on user risk levels, enabling targeted and efficient data protection.

Its functions include:
Instead of applying the same DLP rules to all users, Adaptive Protection tailors enforcement based on how risky a user's behaviour is, as determined by Insider Risk Management.
	- High risk users, for example, those downloading large volumes of files or showing signs of data exfiltration may automatically be subject to stricter DLP controls, such as blocking file sharing and uploads.
	- Low risk users continue to operate under less restrictive DLP rules and maintain a normal level of productivity.

The process is as follows:
1. Insider Risk Management continuously monitors user behaviour across M365, including email, file access, Teams, etc.
2. Users are assigned risk levels - Low, Medium, or High based on detected activity.
3. DLP policies configured for Adaptive Protection applies different actions depending on a user's current risk level.
4. As risk levels change, DLP enforcement automatically adjusts in real-time.

Example scenario:
An employee in the marketing department attempts to upload a confidential client list to their personal Google Drive. Insider Risk Management flags this as suspicious and increases the user's risk level to High. Through Adaptive Protection enabled - DLP immediately blocks the sharing attempt and alerts the compliance office. For a low risk user, the same action might only trigger a warning or audit log.

Adaptive Protection advantages:
- Enables proactive protection based on risk
- Reduce false positives for low-risk users
- Decreased alert fatigue by focusing on high-risk activity
- Automatically scales protection based on behaviour patterns


Microsoft Purview > Insider Risk Management > Users > Adaptive Protection

Learn about Adaptive Protection in Data Loss Prevention https://learn.microsoft.com/en-us/purview/dlp-adaptive-protection-learn

----------------------------------------------------------------------------------

## DLP policy and rule precedence

Policy precedence Important!
- lower number = higher priority (for DLP policies)
- Higher number = higher priority for sensitivity labels)

To change priority click on policy and select Reprioritize to assign higher or lower priority.

<img width="1292" height="352" alt="image" src="https://github.com/user-attachments/assets/44c084da-73c2-408e-9a10-00c37532d50b" />

Policy rule precedence - multiple rules can be applied to one DPL policy, to avoid conflict between rules:

During creation or in edit mode in the Advanced DLP rule step:
- If there is a rule conflict - most restrictive rule will take effect over the less restrictive rules inside the DLP policy.

----------------------------------------------------------------------------------

## Defender for Cloud apps to deploy DLP file policies

On top of dealing with data loss prevention in regards to Microsoft Purview, there is also have the ability to apply file policies with the help of Defender for Cloud App in conjunction with data loss prevention.

Microsoft Defender > System > Settings > Cloud Apps > Information Protection (Files)

--> Enable file monitoring 


Microsoft Defender > Cloud Apps > Policies > Policy management

\+ Create policy > File policy

<img width="1278" height="1209" alt="image" src="https://github.com/user-attachments/assets/764159d0-32e3-4dae-a79f-953a3c5cb9c6" />
<img width="1277" height="1106" alt="image" src="https://github.com/user-attachments/assets/19571c5f-19b0-4839-8c2f-f49f91198fb1" />
<img width="1366" height="520" alt="image" src="https://github.com/user-attachments/assets/db72c916-7b65-4e5d-b838-6b4cd1dbf3c7" />

----------------------------------------------------------------------------------

## Monitoring DLP alerts, events, and view reports

Microsoft Purview > Data Loss Prevention > Alerts

Alerts won't show up until the DLP policy is turned on to support it.

Microsoft Purview > Data Loss Prevention > Policy

During creation or in edit mode in the Advanced DLP rule step:

- Edit rule - scroll to incident reports:
	- Send alert to admin when rule match occurs. (turn on - is off by default)
- Choose admin to send the alert to (optional)
	- Name : email

<img width="683" height="655" alt="image" src="https://github.com/user-attachments/assets/32c394dc-aea7-4aa7-96ef-5f03170ded8b" />


Further insights are in the explores - Data Explorer & Activity explorer

Activity explorer - will show all activates regarding DLP polices that occur, great for understanding how DLP is applied and if its effective.

----------------------------------------------------------------------------------

## DLP settings and Just-in-time (JIT) protection

Microsoft Purview > Settings > Data Loss Prevention

Get started with Microsoft Purview Data Loss Prevention just-in-time protection - https://learn.microsoft.com/en-us/purview/endpoint-dlp-get-started-jit







