# IAM-Integrate-OktaIDP-AWS-IAM
Here’s a step-by-step lab documentation for configuring Okta as an Identity Provider in AWS IAM Identity Center

📌 Prerequisites

Before you begin:

•	Admin access to Okta tenant (Admin Console).
•	Admin access to AWS IAM Identity Center (formerly AWS SSO) in the AWS console.
•	Identity Center enabled in your AWS account/organization.
•	Basic knowledge of SAML concepts.

✅ Step-by-Step Setup

🌐 1) Prepare Okta — Create AWS IAM Identity Center SAML App

1.	Sign into Okta Admin Console.
2.	Go to Applications → Applications.
3.	Click Browse App Catalog.
4.	Search for AWS IAM Identity Center and Add it.
5.	After adding, go to the Sign On tab.
6.	Under SAML Signing Certificates, click Actions → View IdP Metadata.
7.	Copy all XML metadata and save it as a file named metadata.xml.
o	This file contains Okta’s SAML IdP metadata you’ll upload to AWS later. AWS Documentation

🔐 2) Configure AWS IAM Identity Center as a Service Provider
1.	Sign in to AWS Console.
   
2.	Open IAM Identity Center (formerly AWS SSO).
   
3.	In the left nav, choose Settings.
   
4.	Click Actions → Change identity source.
  
5.	Select External identity provider and click Next.
   
6.	Under Configure external identity provider:
   
o	Service Provider metadata:     
	Click Download metadata file — this is AWS Identity Center’s SP metadata.     
	Save this metadata file locally.
o	Identity provider metadata:
	Click Choose file and upload the metadata.xml from Okta.

8.	Review, type ACCEPT, and click Change identity source.
o	This enables Okta as the external IdP for AWS Identity Center. AWS Documentation


