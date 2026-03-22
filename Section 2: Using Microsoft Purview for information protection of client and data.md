# Section 2: Using Microsoft Purview for information protection of client and data
----------------------------------------------------------------------------------
### Email encryption

Solutions available within Microsoft 365, focusing on three main options:

1. Microsoft Purview Message Encryption: This is the latest and most supported method by Microsoft. It requires specific licensing, including Azure Rights Management Services and Azure Information Protection. This solution automatically encrypts emails and attachments using Transport Layer Security (TLS) when sent from compliant email clients like Outlook, ensuring a seamless user experience.
	
2. Information Rights Management (IRM): An older encryption method that is still available but not actively supported. It focuses on sensitivity labels and offers automatic email encryption, though it is less compatible compared to newer solutions.
	
3. S/MIME (Secure Multipurpose Internet Mail Extensions): The oldest method still in use, which relies on digital certificates for encryption. While effective within organizations, it poses challenges for external communications, as it requires manual management of certificates by users.

Microsoft Purview Message Encryption is the preferred choice for organizations looking to secure their email communications due to its comprehensive and user-friendly functionality.

Learn more - https://learn.microsoft.com/en-us/purview/email-encryption


----------------------------------------------------------------------------------
### Message encryption

Microsoft 365 admin center > Exchange > Mail flow > Rules

\+ Add a rule > Apply Office 365 Message Encryption and rights protection to messages

	1. Set rule conditions
		- Name: Enable Purview Encryption
		- Apply this rule if: Apply to all messages (other options available)
		- Rights protect message with (Select one): Encrypt
		- Exception (optional)
	2. Set rule settings
		- Rule mode: Enforce
		- Severity: Not audit (because encryption is to be applied to all)
		- More settings available such as activate/deactivate rule, processing, match sender address. 
	3. Review and finish

<img width="2026" height="866" alt="image" src="https://github.com/user-attachments/assets/b9c7da45-65fc-4a7f-b895-c9dbe4278717" />

Learn more - https://learn.microsoft.com/en-us/purview/set-up-new-message-encryption-capabilities

----------------------------------------------------------------------------------
### Advanced Message Encryption - Compliance with Microsoft Purview

Apply sensitivity label for enhanced security.

Microsoft 365 admin center > Exchange > Mail flow > Rules

\+ Add a rule > Apply Office 365 Message Encryption and rights protection to messages

	1. Set rule conditions
		- Name: Compliance with Purview Message Encryption
		- Apply this rule if: Apply to all messages (other options available)
		- Rights protect message with (Select one): Top Secret Data (the sensitivity label defined in Purview)
		- Exception (optional)
	2. Set rule settings
		- Rule mode: Enforce
		- Severity: Not audit (because encryption is to be applied to all)
		- More settings available such as activate/deactivate rule, processing, match sender address. 
	3. Review and finish

<img width="1595" height="872" alt="image" src="https://github.com/user-attachments/assets/047c1788-7f49-4d06-b462-9b858d38691d" />

Advanced Message Encryption - https://learn.microsoft.com/en-us/purview/ome-advanced-message-encryption

Add your organization's brand to your Microsoft Purview Message Encryption encrypted messages - https://learn.microsoft.com/en-us/purview/add-your-organization-brand-to-encrypted-messages

_____________________________________________

Setup maps
If you created:
#### - Rule 1 → Apply sensitivity label (Compliance with Purview Message Encryption)
#### - Rule 2 → Encrypt email (Enable Purview Encryption)

Then:
- Purview Audit logs  shows:
  - Label applied
  - Encryption action
- Activity Explorer shows:
  - Labeling activity 
- Exchange trace :
  - Rules triggered 

Why both exist - key concept:
Microsoft separates:
1. Encryption alone
	- Just protect the message
	- Fast, simple
	- No governance context
2. Label-based protection
	- Classify + protect + control
	- Tied to compliance, auditing, DLP


