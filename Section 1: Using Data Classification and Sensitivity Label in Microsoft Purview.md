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
---------------------------------------------------------------------------------
## Trainable classifiers
---------------------------------------------------------------------------------
## Data explorer & content explorer for monitoring data classification
---------------------------------------------------------------------------------
## Sensitive info types (STI) with Optical character recognition (OCR)
---------------------------------------------------------------------------------
## Sensitivity labels
---------------------------------------------------------------------------------
## Creating sensitivity labels
---------------------------------------------------------------------------------
## Publishing Sensitivity labels
---------------------------------------------------------------------------------
## Auto-labeling policies for sensitive labels
---------------------------------------------------------------------------------
## Monitoring label usage
---------------------------------------------------------------------------------
## Microsoft Defender for Cloud Apps
---------------------------------------------------------------------------------
## Apply sensitivity labels in Microsoft Defender for Cloud Apps
