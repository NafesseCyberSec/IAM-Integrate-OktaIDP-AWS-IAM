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

🔄 3) Update Okta with AWS Identity Center Metadata

1.	Return to Okta Admin Console → Applications.
2.	Open the AWS IAM Identity Center app you created.
3.	Go to Sign On → Edit.
4.	In Advanced Sign-on Settings:

o	AWS IAM Identity Center ACS URL: paste the ACS URL from the AWS metadata you downloaded.
o	AWS IAM Identity Center Issuer URL: paste the issuer URL from the AWS metadata.
o	Application username format: choose a unique attribute such as Okta username.

5.	Save the settings. AWS Documentation

👥 4) (Optional) Enable SCIM Provisioning
To automatically sync users/groups from Okta into AWS IAM Identity Center:

1.	In AWS IAM Identity Center settings, look for Automatic provisioning and Enable it.
   
o	Copy the SCIM endpoint and access token generated.

2.	In Okta, go to your IAM Identity Center app Provisioning tab → Integration.
3.	Enter the SCIM endpoint and token from AWS.
4.	Configure Push Groups if desired to sync groups into AWS.
5.	Assign users to the app via the Assignments tab to start provisioning. AWS Documentation

🧪 5) Test the SSO Flow

1.	In Okta My Apps portal, launch the AWS IAM Identity Center app.
2.	You should be redirected to AWS and signed in using Okta credentials.
3.	Users will see the AWS Identity Center user portal with assigned AWS accounts/apps. AWS Documentation

   🧩 Next Steps (Optional)
   
•	Assign Access: Grant users/groups access to AWS accounts and permission sets in IAM Identity Center. AWS Documentation
•	Fine-Tune Attributes: Configure SAML attribute mappings in Okta for group/role assignments. AWS Documentation





