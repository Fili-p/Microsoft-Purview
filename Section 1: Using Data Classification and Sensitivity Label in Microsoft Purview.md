# Section 1: Using Data Classification and Sensitivity Label in Microsoft Purview
---------------------------------------------------------------------------------
## Creating custom sensitive info types

Microsoft Purview > Information Protection > Classifiers > Sensitive info types

There will be a list of built-in sensitive info types (SIT) across the various platforms within Microsoft 365.

To create a custom sensitive info type:

\+ Create sensitive info type 

	1. Name
		- Name: Credit Card Info TL
		- Description: Credit Card Info TL (Test Lab)
	2. Pattern
		- + Create pattern
			- Confidence level - the more supporting elements there are the higher the confidence level is going to be.
			  -  High Confidence
			- Primary element - information to detect.
			  - Function > choose function (built-in)
					- Func_credit_card 
			- Character proximity - supporting elements found in proximity to primary element.
			  - Default 300 (characters)
			- Supporting elements:
			  - Add proximity within 300 characters
				- Choose function >  Func_expiration_date
			- Create
		- More patterns can be added.
	3. Recommended confidence level
		- Will display the confidence level defined in the previous step.
	4. Finish
		- Review settings and create.

<img width="979" height="705" alt="image" src="https://github.com/user-attachments/assets/b91d9a6f-dea2-4ddf-9124-60b5d002ef94" />

May take up to 24 hours before it is fully deployed and ready for use.

In the Sensitive info types list search for Credit Card Info TL

<img width="1441" height="890" alt="image" src="https://github.com/user-attachments/assets/90c158f2-f430-4c24-b3ab-74ee57075414" />

Test > Upload file (credit_card_example.docx) - credit cards are fake (AI generated).

<img width="1244" height="1267" alt="image" src="https://github.com/user-attachments/assets/b9773d5c-151f-4146-8483-cdf6f5abb8b6" />

A test file containing four credit card numbers was scanned, and the system successfully detected all four instances, demonstrating accurate sensitive data identification.

Create custom sensitive information types - visit Microsoft doc for more info.
https://learn.microsoft.com/en-us/purview/sit-create-a-custom-sensitive-information-type

---------------------------------------------------------------------------------
## Document Fingerprinting

Analyzing documents and building a template from those documents than then becomes a sensitive information type (SIT). 

Microsoft Purview > Information Protection > Classifiers > Sensitive info types

\+ Create Fingerprint based SIT

	1. Name
		- Name: Fingerprint_credit_card_info
		- Description: Fingerprint_credit_card_info
	2. Upload file
		- Upload file
		- Confidence level (ranking system) as defined by Microsoft's algorithm, can be modified as needed.
	3. Finish
		- Review settings and create.

<img width="837" height="559" alt="image" src="https://github.com/user-attachments/assets/4a56dca5-9538-4dc9-8baf-b40b4abb3b9b" />

In the Sensitive info types list search for Fingerprint_credit_card_info (type: Fingerprint)

Document fingerprinting - visit Microsoft doc for more info.
https://learn.microsoft.com/en-us/purview/sit-document-fingerprinting

---------------------------------------------------------------------------------
## Exact data match (EDM) classifiers

Used to create highly precise, customized, and secure classification rules for sensitive data protection. Applies to structured data such as employee IDs, patient records, customer databases, etc. - to prevent data leaks, enforce compliance and DLP.

Microsoft Purview > Information Protection > Classifiers > EDM classifiers

\+ Create EDM classifier

	1. Name your classifier
		- Name: John Doe Credit Card Info
		- Description: John Doe Credit Card Info
	2. Define the schema
		- Two options: Upload a file (sample data) or Manually define data structure
			- Upload a file then review sample data for accuracy
		- Select primary elements
			- Credit Card Number
		- Configure settings for data in selected columns
			- Read through and check all that apply
			- For more info visit - https://go.microsoft.com/fwlink/?linkid=2196225
	3. Specify detection rules
		- For more info visit - https://learn.microsoft.com/en-us/purview/sit-get-started-exact-data-match-create-rule-package
	4. Review and submit

<img width="956" height="757" alt="image" src="https://github.com/user-attachments/assets/185085ee-a0ae-4c89-8f9b-34c5ddeeef01" />

May take up to a few days until available for deployment in large environments.

Test results

<img width="1111" height="733" alt="image" src="https://github.com/user-attachments/assets/d034de87-9e94-4e56-98fb-e90734d667f1" />

-

EDM STI - visit Microsoft doc for more info.
https://learn.microsoft.com/en-us/purview/sit-get-started-exact-data-match-based-sits-overview

---------------------------------------------------------------------------------
## Trainable classifiers

With a Microsoft 365 trainable classifier, you can train it to recognize different types of content by giving it samples to examine. It can be used to identify items for application of Office sensitivity labels, Communications compliance policies, and retention labels. 

To create a custom trainable classifier, it is necessary to provide it with samples that are selected by a human and are positively correlated with the category. Following the processing of the positive matched samples, you test the classifier's ability to predict by presenting it with both positive and negative samples. 

The following permissions are required to access classifiers in the UI: 
- For the tenant to be able to create custom classifiers, the Global Admin must grant permission. 
- To train a classifier, a Compliance Administrator role is required. 

Classifiers can only be used in these scenarios with accounts that have the following permissions: 
- Retention label policy: Record Management and Retention Management roles 
- Sensitivity label policy: Security Administrator, Compliance Administrator, Compliance Data Administrator 
- Communication compliance policy: Insider Risk Management Admin, Supervisory Review Administrator 

Important note!
- A custom classifier can be trained and reviewed only by the user who created it.

Timeline:
- Trainable classifiers may take about a month to deploy.

Seed Content:
- Seed content is chosen by a human and is judged to represent the category of content.
- A minimum of 50 positive samples and up to 500 are required
- A trainable classifier will process up to 500 samples created recently (based on the file creation date and time stamp). 
- More samples will enable the classifier (ML model) to make more accurate predictions.

Trainable Classifiers- visit Microsoft doc for more info.
https://learn.microsoft.com/en-us/purview/trainable-classifiers-get-started-with

---------------------------------------------------------------------------------
## Data explorer & content explorer for monitoring data classification

Microsoft Purview > Information Protection > Explorers

- Data Explorer: helps users review information classified as sensitive as data is ingested. Initially, data may be sparse but will grow as users engage with the labelling process.
- Activity Explorer: records actions performed by users, can be filtering by date and specific actions.


### Microsoft Purview > Settings > Data Connectors

- Data Connectors: enable ingestion of data from various sources into Microsoft 365. This integration, including from third-party applications like Salesforce, enhances the functionality of monitoring tools.

---------------------------------------------------------------------------------
## Sensitive info types (STI) with Optical character recognition (OCR)

Example use case - scan PDF files for sensitive information. Supported locations includes Exchange, SharePoint sites, OneDrive accounts, Teams chat and channel messages, and Devices.

Perquisite: pay-as-you-go subscription - https://learn.microsoft.com/en-us/purview/ocr-cost-estimator

Cost Estimate: $1.00 for every 1,000 items scanned. (Each page is scanned separately - 10 pages in a PDF file will count as 10 separate scans).

To enable OCR: Microsoft Purview > Settings > Optical character recognition (OCR)

Optical character recognition in Microsoft Purview - https://learn.microsoft.com/en-us/purview/ocr-learn-about

---------------------------------------------------------------------------------
## Sensitivity labels

A label identifies classification information regardless of where the data is stored or who has access to it. Labels may include visual markers such as a header, footer, or watermark.

The process of using labels is as follows:
- Admin: creates a sensitivity label, and publishes the label to users and groups selected in a label policy.
- End user: labels documents with available labels.
- Office or third-party app/service: enforces protection settings on the email or document according to the labels that have been applied.
	
The sensitivity label is like a stamp that is applied to content and is: 
- Customizable: Depending on the organization's needs and sensitive content level, you can create categories. For example, Personal, Public, General, Confidential, and Highly Confidential.
- Clear text: As labels are stored in clear text in the metadata of files and emails, third-party apps and services can read them and take appropriate protective measures.
- Persistent: In the case of files and emails, the label is stored within the metadata, so it travels with the content, regardless of where the content is stored. This allows to apply and enforce policies based on unique label identification.

In the event that a sensitivity label is applied to an email or document, any protection settings configured for that label will be enforced on its content. The following options can be configured for a sensitivity label: 
- Protect data by encrypting emails and documents. It is also possible to restrict what actions users or groups are allowed to perform, as well as for how long. 
- Mark the content of an email or document by adding a watermark, header, or footer when using Office apps. Emails cannot be watermarked.

### Microsoft Purview > Settings > Roles and scopes 

Microsoft Entra ID: List of existing roles and assigned users.

Role groups: is where you assign users to a role. There are a number of built-in roles, with predefined permissions. Can also create a new role.

---------------------------------------------------------------------------------
## Creating sensitivity labels

Microsoft Purview > Information Protection > Sensitivity labels

\+ Create > Label

	1. Label details
		- Name: Top Secret Data
		- Display Name (name users see) - Top Secret Data
		- Label priority - default (can be changed after)
		- Description for users: Top Secret Data
		- Description for admins: Top Secret Data
		- Label color: Red
	2. Scope - where the label is going to be available
		- Default:
			- Files & other data assets (Microsoft 365, Fabrics includes Power BI, Azure)
			- Emails (Outlook)
			- Meetings (Outlook schedules & Teams)
			- Group & sites - not enabled in my test env
	3. Item - protection settings
		- Options include:
			- Control access
			- Apply content marking
			- Protect Teams meetings and chats - not enabled in my test env
		○ Access Control
			- Assign permission or let user decide
			- User access to content
			- Allow Offline access
			- Assign permissions to specific users or groups
				- Choose permissions
			- Optional: Watermarking & Double Key Encryption
		- Auto-labeling for files and emails: on/off
	4. Groups & sites - protection settings
		- Privacy and external user access
		- External sharing and Conditional Access
		- Private teams discoverability and sharing channel settings
	5. Finish
		- Publish label to user' apps
		- Don’t Create a policy yet 

<img width="1995" height="657" alt="image" src="https://github.com/user-attachments/assets/7e0c7476-71da-4598-9161-b14645b88846" />

\

Take note of priority number (higher number = higher priority) as this is auto applied and can be changed.

Lean about sensitivity label - https://learn.microsoft.com/en-us/purview/sensitivity-labels

---------------------------------------------------------------------------------
## Publishing Sensitivity labels

Microsoft Purview > Information Protection > Sensitivity labels

Choose the Sensitivity label and select > Publish label

	1. Labels to publish
		- Select labels to publish - Edit
	2. Admin units
		- If no specific admin unit is assigned click next to assign to all users and groups.
		- https://learn.microsoft.com/en-us/purview/purview-admin-units
			- Microsoft Entra ID - create an administrative unit 
	3. Users units
		- Select users and groups - make label available  
	4. Settings
		- Options:
			- Users must provide a justification to remove a label or lower its classification
			- Require users to apply a label to their emails and documents
			- Require users to apply a label to their Fabric and Power BI content
			- Provide users with a link to a custom help page 
		- Documents
			- Choose auto applied label
		- Emails
			- Choose auto applied label
			- Inherit label from attachments (highest priority applies automatically)
		- Meetings
			- Choose auto applied label
			- Inherit label from artifacts  - will replace the meeting's label (highest priority applies automatically)
		- Fabric and Power BI
			- Choose auto applied label
	5. Name
		- Name: Top Secret Data Publishing Policy
		- Description: 
	6. Finish
		

May take 24 hours to deploy. 

To see the published labels:
Microsoft Purview > Information Protection > Policies > Label publishing policies

<img width="2555" height="578" alt="image" src="https://github.com/user-attachments/assets/c149a2c2-58e2-4b6d-aa7d-676686b83b5f" />

Label view in a Word file (Top Secret Data) -  that’s where users will apply labels.

<img width="1530" height="372" alt="image" src="https://github.com/user-attachments/assets/b937a2d9-8962-43e9-8e92-54c5df40107b" />

Lean more about labels - https://learn.microsoft.com/en-us/purview/create-sensitivity-labels?tabs=classic-label-scheme

---------------------------------------------------------------------------------
## Auto-labeling policies for sensitive labels

Will auto match data in M365 such as files and emails when the data matches conditions specified.


Microsoft Purview > Information Protection > Sensitivity labels

Check box of the Sensitivity label and select > Create auto-labeling policy

	1. Name
		- Name: Top Secret Data auto-labeling policy
		- Description: 
	2. Label
		- Choose label to auto-apply
	3. Admin unit
		- Assign admin unit (units are created in Microsoft Entra ID)
		- Click next to assign policy to all users and groups
	4. Location
		- Options
			- Exchange email
			- SharePoint sites
			- OneDrive accounts
		- Each option can be further edited to apply to specific users and groups. Default is all users.
	5. Policy rules
		- Choose one option:
			- Common rules: applies the same rules to all three location defined in the previous step.
			- Advanced rules: allows for different rules to be set for each location.
		
		- Common rule > New rule
				- Name: Social Security Numbers
				- Description: 
			- Add Conditions > Content contains (more options are available):
				- Group name: SSN
				- Add > Sensitive info types (can add multiple STIs)
					- U.S. Social Security Number (SSN)
						- Define confidence and instances to find
			- Can also add exceptions (for certain things to ignore)
		- Additional label settings:
			- Email only - replace existing labels
			- All locations (purview) - replace existing labels
			- Apply encryption to email received from outside your organization
	6. Policy mode
		- Test now or later
			- Run policy in simulation mode - will gather items that match but labels won't be applied, until reviewed by a human to decide if the policy works as needed or policy requires further refinement.
				- Auto turn on after 7 day if not modified (optional)
			- Leave policy turned off
	7. Finish

May take 24 to 48 hours to deploy.

<img width="773" height="1015" alt="image" src="https://github.com/user-attachments/assets/2786f810-15a9-4b3c-856f-154b1ae24c35" />

Lean more about auto-labeling:
https://learn.microsoft.com/en-us/purview/apply-sensitivity-label-automatically?tabs=apply-label

---------------------------------------------------------------------------------
## Monitoring label usage

Monitor label usage within Microsoft Purview using: Data Explorer, and Activity Explorer.

Microsoft Purview > Information Protection > Explorers

Data Explorer: This tool helps users search for activities related to labeled data, like sensitivity and retention labels. It's important to wait about 24 hours after performing activities for the data to populate in the explorer.

Activity Explorer: This tool offers insights into all activities related to sensitive information and labels. Like Data Explorer, it requires waiting for data to populate. (Logs of all changes can be filtered by activity, location, user, label, etc.)

### Microsoft Purview > Information Protection > Reports

Reports: an overview dashboard for coverage and access control, provides insights and guides users to relevant areas for further exploration.
- Posture reports on/off


---------------------------------------------------------------------------------
## Microsoft Defender for Cloud Apps

Microsoft Defender for Cloud Apps main points:
1. Functionality: It acts as a cloud access security broker, monitoring user activities to prevent unauthorized access to cloud applications.
2. Tracking and Discovery: It generates log data, monitors user behavior, and helps prevent shadow IT by discovering unauthorized applications being used by employees, with over 16,000 SaaS applications identified.
3. Access Control: It can function as a reverse proxy to ensure users access only their business accounts and not personal ones, enhancing security.
4. Integration with Compliance: The tool integrates with Microsoft 365 compliance policies, aiding in managing sensitive information according to regulations such as GDPR, PCI DSS, etc.
5. Alerts and Behavior Monitoring: It generates alerts for admins regarding potential security violations and monitors user behaviors for cyber threats.
6. Conditional Access: The service supports conditional access app control, allowing organizations to enforce policies to restrict sharing of sensitive information outside the company.
7. Visibility and Management: It enhances visibility into cloud usage and creates app connectors for managing sanctioned applications, with policies to detect risky behavior and provide remediation strategies.

---------------------------------------------------------------------------------
## Apply sensitivity labels in Microsoft Defender for Cloud Apps

Microsoft 365 admin center > Security (Microsoft Defender) > Cloud apps > Policies > Policy management

\+ Create policy > File policy (apply sensitivity label)

File policies in Microsoft Defender for Cloud Apps - https://learn.microsoft.com/en-us/defender-cloud-apps/data-protection-policies#:~:text=To%20create%20a%20new%20file,policy%20and%20select%20File%20policy.




