# Section 4: Data retention in Microsoft Purview
-----------------------------------------------------------------

## Understanding information retention and disposal

Concepts of information retention and disposition, emphasizing the importance of managing data within organizations:
- Purpose of Retention: companies must consider how long to retain sensitive information, addressing legal obligations, industry standards, and the risks of retaining outdated data.
- Retention Actions: two primary actions: retaining or deleting information, and the combinations of these actions that can be taken.
- Retention Policies vs. Labels: Retention policies manage data at broader levels, affecting all content in specific areas, while retention labels allow for more granular control over individual items.
- Importance of Configuration: Setting retention configurations is crucial for reducing storage burdens and ensuring compliance with legal standards.
- Content Preservation: The lecture explains how retention settings operate with content in place and how modifications to governed content lead to preservation actions.
- Conflict Resolution: retention takes precedence over deletion and the longest retention period prevails always.
- Disposition Reviews: The process after content reaches the end of its retention period, options: suspending deletion, archiving content, or extending retention.
- Understanding Terminology: The importance of understanding retention terminology is key to implementing effective practices.


Important!
Distinctions between retention policies, retention labels, and retention label policies:

1. Retention Policies: These are comprehensive rules applied by administrators that enforce retention and deletion automatically across various platforms like mailboxes and SharePoint sites. They require no interaction from users and are suitable for managing large-scale data retention, such as retaining all Teams messages for seven years before deletion.
2. Retention Labels: Unlike policies, retention labels focus on individual items such as emails or documents. Users can apply these labels manually or they can be assigned automatically based on certain criteria. This allows for individual item management, including triggering a review before deletion. For example, a document can be labeled to be retained for ten years if it's a financial record.
    - Retention Label Policies: These act as a mechanism to deliver retention labels, enabling administrators to publish these labels to users in specific locations. This facilitates user visibility and application of the labels. For instance, a policy might publish a confidential label specifically for the HR department's OneDrive.

-----------------------------------------------------------------

## Using adaptive labels

Retention policies should adapt as individuals move within an organization:
- static - manual updates required
- Adaptive - designed to adjust automatically based on user attributes, such as department changes, ensuring relevant retention policies are applied efficiently.

Creating a new adaptive scope:
Settings > Roles and scopes > Adaptive scopes

\+ Create scope

	1. Name
		- Name: Sales Users Scope
		- Description: 
	2. Admin unit
		- Add remove admin units or Full directory
	3. Scope type
		- Options:
			- Users
			- SharePoint sites
			- M365 Groups
		- Create the query to define users
			- User attribute: 
				- Department | is equal to | Sales
				- Or | Job title | is equal to | Sales
	4. Review

<img width="1662" height="540" alt="image" src="https://github.com/user-attachments/assets/17a5cc9a-9a62-4d81-ae52-e947e3f16b7d" />

Adaptive scopes - https://learn.microsoft.com/en-us/purview/purview-adaptive-scopes

-----------------------------------------------------------------

## Creating retention labels

Microsoft Purview > Data Lifecycle Management >  Retention labels

\+ Create a label

	1. Name
		- Name: 7 year retention 
		- Description for users: 7 year retention
		- Description for admins:
	2. Label settings
		- Options:
			- Retain items forever or for a specific period (items cannot be deleted during the set period)
			- Enforce actions after a specific period (items can be deleted after a certain amount of time, or specify what happens to that item)
			- Just label items (classify labeled items, users can edit, move, or delete the items)
	3. Period (Retain item forever or for a specific period)
		- Retain items for: 7 years
			- Can also set a custom amount of time
		- Start the retention period based on
			- When Items were created (other options available such as custom or automated events)
		- Choose what happens after the retention period (options)
			- Delete items automatically
			- Start a disposal review
			- Change the label
			- Run a Power Automated flow
			- Deactivate retention settings
	4. Finish
		- Publish this label to M365 locations
		- Auto-apply this label to a specific type of content
		- Do nothing

<img width="1665" height="648" alt="image" src="https://github.com/user-attachments/assets/629435f9-0123-4ef0-b9ca-09d01356a329" />

Learn about retention policies and retention labels - https://learn.microsoft.com/en-us/purview/retention?tabs=table-overriden

-----------------------------------------------------------------

## Publishing a retention label using a label policy

Microsoft Purview > Data Lifecycle Management > Label policies

\Publish labels

	1. Choose labels to publish
		- 7 year retention
	2. Administrative Units
		- Add remove admin units or Full directory
	3. Scope
		- Options:
			- Adaptive
				- Add predefined adaptive scope
			- Static
				- Choose locations (Exchange, SharePoint, OneDrive, M365 mailboxes & sites)
	4. Name your policy
		- Name: 7 year retention policy
		- Description: 
	5. Finish

May take up to 24hrs to deploy.

<img width="1605" height="570" alt="image" src="https://github.com/user-attachments/assets/5d299796-5cf7-4ebe-8aaa-a491ce88f261" />

Publish retention labels and apply them in apps - https://learn.microsoft.com/en-us/purview/create-apply-retention-labels?tabs=manual-outlook%2Cdefault-label-for-sharepoint

-----------------------------------------------------------------

## Auto-apply labels for retention

Microsoft Purview > Data Lifecycle Management > Label policies

\Auto-apply a label

	1. Name
		- Name: Auto-apply 7 year retention to financial data
		- Description:
	2. Info to label 
		- Options:
			- Apply label to content that contains sensitive info (selected option)
			- Apply label to content that contains specific words or phrases, or properties
			- Apply label to content that matches a trainable classifier
			- Apply label to cloud attachments and links shared in Exchange, Teams, Viva Engage, and Copilot
		- Content that contains sensitive info
			- Category: Financial
			- Regulations: U.K. Financial data (build-in)
				- Default: Credit card Nr., EU Debit Card Nr., SWIFT Code
		- Define content that contains sensitive info
			- Add sensitive info types, set confidence, and instance count
		
	3. Administrative Units
		- Add remove admin units or Full directory
	4. Scope
		- Options:
			- Adaptive
				- Add predefined adaptive scope
			- Static
				- Choose locations (Exchange, SharePoint, OneDrive, M365 mailboxes & sites)
		- Choose adaptive policy scope and locations
			- Add scope: Sales Users Scope
			- Choose location (based on the scope): Exchange mailboxes, OneDrive 
	5. Label
		- Choose label to auto-apply
			- 7 year retention
	6. Mode
		- Test the policy before running
		- Turn on policy
	7. Finish

May take up to 7 days to deployed.

<img width="1608" height="629" alt="image" src="https://github.com/user-attachments/assets/d49dec99-a814-4ed0-b358-ec02d373838d" />

Automatically apply a retention label to retain or delete content - https://learn.microsoft.com/en-us/purview/apply-retention-labels-automatically
-----------------------------------------------------------------

## Retention policies precedence & conflict

<img width="520" height="481" alt="image" src="https://github.com/user-attachments/assets/ce151eaa-ba23-4cb3-b03c-9e95fa17ee71" />

Learn about retention policies and retention labels - https://learn.microsoft.com/en-us/purview/retention?tabs=table-overriden
-----------------------------------------------------------------
## Creating a retention policy
Microsoft Purview > Data Lifecycle Management > Policies > Retention policies 

\+ New retention policy

	1. Name
		- Name: 5 year retention demo
		- Description: 
	2. Administrative Units
		- Add remove admin units or Full directory
	3. Type
		- Options:
			- Adaptive
			- Static (Selected option)
		- Locations
			- Exchange, SharePoint, OneDrive, etc., ….. , AI apps
			- Can be further edited to include or exclude  users, groups, sites
	4. Retention settings
		- Three options:
			- Retain items for a specific period
				- 5 years (or set a custom period)
				- Start the retention period based on (options)
					- When items were created
					- When items were last modified
				- At the end of the retention period (options)
					- Delete items automatically
					- Do nothing
			- Retains items forever
			- Only delete items when they reach a certain age
	5. Finish
		- Important: Items that are currently older than 5 years will be deleted after you turn on this policy. 
      This is especially important to note for locations scoped to 'All' sources (for example, 'All Teams chats') 
      because all matching items in those locations across your organization will be permanently deleted.​

May take up to 7 days to deploy.

<img width="1608" height="629" alt="image" src="https://github.com/user-attachments/assets/81649b9b-8b7f-43cf-a6c4-1ef5b8ddfbd6" />

-----------------------------------------------------------------

## Concepts for recovering  retained content in M365

To recover retained content in M365, it depends on where the content was stored (e.g., Exchange, SharePoint, etc.) and whether it was deleted but under retention. How recovery works:

	1. Exchange Online (Email)
	If an email is deleted but under a retention policy or label:
		- Its removed to the Recoverable Items folder
		- You can recover it using:
			- Outlook: Folder > Recover Deleted Items
			- PowerShell: Search-Mailbox or Compliance Search
			- Microsoft Purview: Content Search (if it went to the Purges or DiscoveryHold  subfolder)
	Even after permanent deletion by user, retention keeps it hidden (not visible in mailbox) but still recoverable for the admin.

	2. SharePoint / OneDrive
	Deleted files under a retention policy go to:
		- First-stage Recycle Bin - user accessible for 93 days
		- Second-stage Recycle Bin - admin only 
	
	If retention policy is active, the content is also retained in a hidden "Preservation Hold Library" and:
		- Can be recovered via:
			- Content Search in Microsoft Purview
			- eDiscovery case
			- PowerShell (ex. Command  "Get-PnPListItem")
	
	3. Microsoft Teams
	Teams messages are stored in mailboxes:
		- Channel messages > Group mailbox
		- 1:1 chats > User mailbox
	
	Recover using:
		- Microsoft Purview eDiscovery or Content Search
		- Export and restore from results manually (no native restore button for Teams messages)



















