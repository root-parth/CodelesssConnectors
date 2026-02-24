☁️ Salesforce Service Cloud (Multi-Tenant) Custom Connector

This repository provides a Codeless Connector for Salesforce Service Cloud, optimized for multi-tenant architectures. It utilizes the standard Microsoft-released table schema but includes enhanced functionality to project a specific Tenant Name column, allowing you to distinguish data from multiple Salesforce organizations within a single Microsoft Sentinel instance.

🚀 Key Features

    Multi-Tenant Projection: Automatically maps data to a Tenant Name column for easy filtering and dashboarding.

    OAuth 2.0 Client Credentials Flow: Optimized for secure, headless service-to-service communication.

    Azure Custom Template Deployment: Standardized deployment via ARM/Bicep templates in the Azure Portal.

🔑 Phase 1: Salesforce Preparation

Before deploying to Azure, ensure you have configured your Salesforce environment for OAuth 2.0 Client Credentials Flow:

    Create a Connected App: Follow Salesforce's guide to create a Connected App.

    Enable Client Credentials: Follow Configure the OAuth 2.0 Client Credentials Flow.

    Gather Credentials: Collect the following for Phase 3:

        Consumer Key (Client ID)

        Consumer Secret (Client Secret)

        Salesforce Domain (e.g., https://your-domain.my.salesforce.com)

📦 Phase 2: Azure Deployment (Infrastructure)

This step provisions the connector resources into your Azure environment.

    Log in to the Azure Portal.

    Search for "Deploy a custom template" and select "Build your own template in the editor".

    Copy and paste the mainTemplate.json from this repository into the editor and click Save.

    Fill in the Deployment Form:

        Subscription: Select your target subscription.

        Resource Group: Select the group where your Sentinel/Log Analytics workspace resides.

        Region: Select the region matching your workspace.

        Workspace Name: Enter the name of the Log Analytics Workspace where Microsoft Sentinel is enabled.

    Click Review + Create, then Create.


⚙️ Phase 3: Connector Configuration

Once the deployment is complete, you must connect it to your Salesforce tenant.

    Navigate to your Log Analytics Workspace > Microsoft Sentinel > Data Connectors.

    Search for and select the Salesforce Service Cloud (Multi-Tenant) connector.

    Open the Connector Page and fill in the following fields:

Salesforce URL ->	Your "My Domain" URL.	https://contoso.my.salesforce.com
Salesforce Tenant Name -> The name to be projected to the Tenant Name column.	"ContosoProduction" (No special Characters or Spaces allowed)
Log Collection Interval ->	Frequency of data polling (in minutes).	Hourly / Daily
Consumer Key ->	The Client ID from Salesforce.	3MVG9...
Consumer Secret	-> The Client Secret from Salesforce.	7E8B2...


