# Section 5: Insider Risk Management in Microsoft Purview
---------------------------------------------------------
## Understanding Insider Risk Management in M365

How does insider risk management benefit an organization?
- Purview Insider Risk Management is a compliance solution that helps minimize internal risks by detecting, investigating, and responding to malicious and inadvertent activities within your organization.
- The insider risk policies allow you to define the types of risks that your organization needs to identify and detect, including reporting cases and escalating cases to Microsoft eDiscovery (Premium) if necessary.
- To ensure that users are complying with the compliance standards in your organization, risk analysts in your organization can take action quickly.

Identifying and addressing modern risk challenges: 
The first step in managing and minimizing risk within an organization is to understand the types of risks encountered in the modern workplace. A number of risks are influenced by external factors and events that cannot be controlled directly. In addition to these risks, there are other risks that are caused by internal events and user actions that can be minimized or avoided. An example of such a risk would be the risk posed by illegal, inappropriate, unauthorized, or unethical behavior and actions on the part of your organization's users. A wide range of internal risks are associated with these behaviors: 
- Leaks of sensitive data and data spillage
- Confidentiality violations
- Intellectual property (IP) theft
- Fraud
- Insider trading
- Regulatory compliance violations 

Modern workplaces provide users with a broad range of tools for creating, managing, and sharing data. It is often the case that organizations have limited resources and tools to identify and mitigate organization-wide risks while adhering to user privacy requirements.

Principles of Insider Risk Management: 
- Transparency: maintain a balance between user privacy and organizational risk with a privacy-by-design architecture.
- Configurable: policies can be customized according to industry, geographical region, and business groups.
- Integrated: Integrated workflow across Microsoft Purview solutions.
- Actionable: retained insights that can be used to enable reviewer notifications, data and user investigations.

Workflow:
An insider risk management workflow assists you in identifying, investigating, and addressing internal risks within your organization. With focused policy templates, comprehensive activity signaling across Microsoft 365 services, and alerts and case management tools, you can identify and address risky behaviors quickly and efficiently. Insider risk management involves the following workflow for identifying and resolving internal risk activities and compliance issues:

<img width="720" height="372" alt="image" src="https://github.com/user-attachments/assets/2682e439-e7c8-4b08-ade1-cc9fe29a3dcc" />


1. Policies
  An organization's insider risk management policy is created by using predefined templates and policy conditions that define what triggering events and risk indicators will be examined. Among these conditions are how risk indicators are used for alerts, what users are included in the policy, which services are prioritized, and the length of time before detection occurs. Getting started with insider risk management is as simple as selecting one of the following policy templates. 
    - Data theft by departing users
    - Data leaks
    - Data leaks by priority users
    - Data leaks by risky users
    - Security policy violations
    - Security policy violations by departing users
    - Security policy violations by risky users
    - Security policy violations by priority users
    - Patient data misuse
    - Risky browser usage

2. Alerts
	The Alerts dashboard displays alerts that are automatically generated based on risk indicators that match policy conditions. The dashboard provides a quick overview of open alerts over time, as well as alert statistics for your organization. To facilitate the identification of existing alerts and new alerts that require action, all policy alerts are displayed with the following information:
    - ID
    - Users
    - Alert
    - Status
    - Alert severity
    - Time detected
    - Case
    - Case status
    - Risk factors

3. Triage (Insider Risk Case)
	When new user activities require investigation, alerts are automatically generated with a Needs review status. This information can be quickly identified by reviewers, who can then review, evaluate, and triage these alerts. A case alert can be resolved by opening a new case, assigning the alert to an existing case, or dismissing the alert. With alert filters, you can quickly identify alerts based on their status, severity, or time of detection. 
	
	During the triage process, reviewers have the option of viewing alert details, viewing user activity associated with the policy match, viewing the severity of the alert, and viewing the user profile.
	
4. Investigate (Insider Risk Case)
	Upon selecting a case on the case dashboard, the case will be opened for investigation and review. This step is at the core of the insider risk management process. In this section, risk activities, policy conditions, alert details, and user details are synthesized into an integrated view for reviewers. Among the most important investigation tools in this area are: 
    - User activity: The risk activity of the user is automatically displayed in an interactive chart that shows the risk levels for current and past risk activities over time. For more information on specific activities, reviewers can drill into specific activities and examine the entire risk history of the user.
    - Content explorer: Data files and email messages associated with alert activities are automatically captured and displayed. Files and messages may be filtered and viewed by data source, file type, tag, conversation, and a wide range of other attributes. 
		- Case notes: The Case Notes section allows reviewers to provide notes regarding a case. In this list, all notes are consolidated in a single view, including information about the reviewer and the date of submission.
	
5. Action (Insider Risk Case)
	The insider risk management case information may need to be shared with other reviewers or services within your organization in more serious cases. With Microsoft Purview, insider risk management is tightly integrated with other solutions to help you resolve risks from start to finish. 
    - eDiscovery (Premium): When you escalate a case for investigation, you have the option of transferring data and managing the case through Microsoft Purview eDiscovery (Premium). eDiscovery (Premium) provides an end-to-end workflow for preserving, collecting, reviewing, analyzing, and exporting information that is relevant to your organization's internal and external investigations. The tool enables legal teams to manage all aspects of the legal hold notification process. (Learn about eDiscovery - https://learn.microsoft.com/en-us/purview/edisc)
    - Office 365 Management APIs integration (preview): Insider risk management supports the exportation of alert information to security information and event management (SIEM) services via the Office 365 Management APIs. By accessing alert information in the platform that is most appropriate for your organization's risk processes, you are able to act on risk activities in a more flexible manner. (Office 365 Management APIs overview - https://learn.microsoft.com/en-us/office/office-365-management-api/office-365-management-apis-overview)


Learn about Insider Risk Management - https://learn.microsoft.com/en-us/purview/insider-risk-management 

---------------------------------------------------------

## Insider Risk Management Connectors

Data Connectors: gather information from third-party services to improve insider risk management.

Connector Capabilities: different types of connectors are available, supporting insider risk management and other functionalities like eDiscovery.

Settings > Data Connectors > All Connectors 

Learn about connectors for third-party data - https://learn.microsoft.com/en-us/purview/archive-third-party-data

---------------------------------------------------------

## Managing Insider Risk Management settings

Managing insider risk within Microsoft Purview settings summary:
1. Analytics: Enable analytics to analyze activities related to insider risk policies (tenant and user levels).
2. Data Sharing: Exporting data to SIEM systems and sharing user risk details with Microsoft solutions like data loss prevention and Microsoft Defender.
3. Detected Groups: Defining groups to focus detection efforts on and create exceptions for specific activities.
4. Global Exclusions: Settings that allow exclusions of certain domains, file types, or criteria from detection policies.
5. Inline Alert Customization: Offers the ability to customize alert settings for better management.
6. Intelligent Detections: A scoring system is introduced for assessing user activities and determining risk levels.
7. Microsoft Teams Integration: Integration of insider risk management with Teams.
8. Policy Time Frames: Allows users to set time frames for recording activities relevant to insider risk policies.
9. Power Automate: automate processes related to insider risk management.
10. Priority User Groups: Defining user groups for closer monitoring based on access levels and past risk.
11. Privacy Considerations: Methods to handle user identities respectfully, using pseudonyms for users triggering risk policies.


Settings > Insider Risk Management


Learn about Insider Risk Management settings - https://learn.microsoft.com/en-us/purview/insider-risk-management-settings

---------------------------------------------------------

## Managing the settings for policy indicators

Configure policy indicators in Insider Risk Management - https://learn.microsoft.com/en-us/purview/insider-risk-management-settings-policy-indicators

---------------------------------------------------------
## Policy templates

Learn about Insider Risk Management policy templates - https://learn.microsoft.com/en-us/purview/insider-risk-management-policy-templates

---------------------------------------------------------

## Creating Insider Risk Management policies

Microsoft Purview > Insider Risk Management > Policies

Two options available quick policy and custom.

Quick policy - preconfigured settings to set up a policy based on common insider risk scenarios (data leak, data theft, risky AI usage, etc.)

\+ Create policy > Custom policy

	1. Policy template
		- Choose template:
			- Data leaks
			- Perquisite: DLP policy (optional)
	2. Name and description
		- Name: Data Leakage 
		- Description:
	3. Users and groups
		- Options:
			- All users, groups, and adaptive scopes (selected option)
			- Specific users, groups, and adaptive scopes
		- Exclude users and groups (optional)
	4. Content to prioritize
		- Options:
			- Prioritize content (options)
				- SharePoint sites
				- Sensitivity labels (selected option)
				- Sensitive info types (selected option)
				- File Extensions
				- Trainable classifiers
			- Don’t prioritize content right now (setup once policy is created)
		- Sensitivity labels (can add multiple)
			- Add label: Top Secret Data
		- Sensitive info types (can add multiple)
			- Add SIT: 
		- Decide whether to score only activity with priority content
			- Options:
				- Get alerts for all activity
				- Get alerts only for activity that includes priority content
	5. Triggering events
		- Options:
			- User matches a DLP policy (up to 20)
			- User performs an exfiltration activity (multiple activity options) 
		- Thresholds for triggering events
			- Apply built-in thresholds (recommended) 
			- Choose your own
	6. Indicators
		- Select indicators used to generate alerts
		- Detection options (multiple advanced ML & settings to configure)
			- Sequence detection
			- Cumulative exfiltration detection
			- Risk score boosters
		- Choose threshold type for indicators
			- Apply thresholds provided by Microsoft
			- Apply thresholds specific to your users' activity
			- Choose your own thresholds
	7. Finish
	
Stay updated (options) choose what emails to receive for alerts:
- When a new policy generates its first alert
- When new high severity alerts are generated
- Weekly email summarizing policies that have unresolved warnings


<img width="1664" height="1259" alt="image" src="https://github.com/user-attachments/assets/937dcc4e-27e0-442d-a876-bcc65eabebc7" />

Create and manage Insider Risk Management policies - https://learn.microsoft.com/en-us/purview/insider-risk-management-policies

---------------------------------------------------------

## Working with forensic evidence settings

Microsoft Purview > Insider Risk Management > Users > Forensic Evidence

Off by default, capture user activity to help determine whether the user's actions pose a risk.

Capacity 20GB free, more storage will inquire additional costs.

Manage Insider Risk Management forensic evidence - https://learn.microsoft.com/en-us/purview/insider-risk-management-forensic-evidence-manage#capacity-and-billing

---------------------------------------------------------

## Managing insider risk level for Adaptive Protection

Microsoft Purview > Insider Risk Management > Users > Adaptive Protection

Adaptive protection in Microsoft Purview uses machine learning to identify the most critical risks and proactively and dynamically apply protection controls from:
- Microsoft Purview Data Loss Prevention (DLP)
- Microsoft Purview Data Lifecycle Management (preview)
- Microsoft Entra Conditional Access (preview)

Dynamically mitigate risks with Adaptive Protection - https://learn.microsoft.com/en-us/purview/insider-risk-management-adaptive-protection







