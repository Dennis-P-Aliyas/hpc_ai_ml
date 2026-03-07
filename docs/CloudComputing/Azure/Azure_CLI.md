# Overview

- Majority of the users will make use of Azure Web Portal to manage the resources. But its command line interface - Azure CLI will be a prerequisite if you are planning to manage the infrastructure via code using tools like TerraForm.

# Install Azure CLI on WSL

- Refer the steps mentioned [here](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-linux?view=azure-cli-latest&pivots=apt#install-azure-cli)

# Validate the installation

- Validate that the azure CLI is installed 

        $ az version
        {
        "azure-cli": "2.84.0",
        "azure-cli-core": "2.84.0",
        "azure-cli-telemetry": "1.1.0",
        "extensions": {}
        }
        
# Configure Azure CLI

- Install `wslu` package in WSL so that the browser is opened automatically while initiating az login

        sudo apt install wslu

- Run below command and authenticate

        $ az login
        A web browser has been opened at https://login.microsoftonline.com/organizations/oauth2/v2.0/authorize. Please continue the login in the web browser. If no web browser is available or if the web browser fails to open, use device code flow with `az login --use-device-code`.

        Retrieving tenants and subscriptions for the selection...

        [Tenant and subscription selection]

        No     Subscription name     Subscription ID                       Tenant
        -----  --------------------  ------------------------------------  -----------------
        [1] *  Azure subscription 1  72480d0f-45db-4433-9e3d-6d1e08a8d954  Default Directory

        The default is marked with an *; the default tenant is 'Default Directory' and subscription is 'Azure subscription 1' (72480d0f-45db-4433-9e3d-6d1e08a8d954).

        Select a subscription and tenant (Type a number or Enter for no changes):

        Tenant: Default Directory
        Subscription: Azure subscription 1 (72480d0f-45db-4433-9e3d-6d1e08a8d954)

        [Announcements]
        With the new Azure CLI login experience, you can select the subscription you want to use more easily. Learn more about it and its configuration at https://go.microsoft.com/fwlink/?linkid=2271236

        If you encounter any problem, please open an issue at https://aka.ms/azclibug

        [Warning] The login output has been updated. Please be aware that it no longer displays the full list of available subscriptions by default.
# Useful Commands

- Logout from Azure account

        $az logout

- List azure subscriptions

        $ az account list --output table
        Name                  CloudName    SubscriptionId                        TenantId                              State    IsDefault
        --------------------  -----------  ------------------------------------  ------------------------------------  -------  -----------
        Azure subscription 1  AzureCloud   72480d0f-45db-4433-9e3d-6d1e08a8d954  52026037-6929-4d92-b7df-b5259303788e  Enabled  True

- Display details of a subscription 

        $ az account show --output table
        EnvironmentName    HomeTenantId                          IsDefault    Name                  State    TenantDefaultDomain                      TenantDisplayName    TenantId
        -----------------  ------------------------------------  -----------  --------------------  -------  ---------------------------------------  -------------------  ------------------------------------
        AzureCloud         52026037-6929-4d92-b7df-b5259303788e  True         Azure subscription 1  Enabled  dennispaliyasoutlook601.onmicrosoft.com  Default Directory    52026037-6929-4d92-b7df-b5259303788e

        $ az account show
        {
        "environmentName": "AzureCloud",
        "homeTenantId": "52026037-6929-4d92-b7df-b5259303788e",
        "id": "72480d0f-45db-4433-9e3d-6d1e08a8d954",
        "isDefault": true,
        "managedByTenants": [],
        "name": "Azure subscription 1",
        "state": "Enabled",
        "tenantDefaultDomain": "dennispaliyasoutlook601.onmicrosoft.com",
        "tenantDisplayName": "Default Directory",
        "tenantId": "52026037-6929-4d92-b7df-b5259303788e",
        "user": {
            "name": "dennis.p.aliyas@outlook.com",
            "type": "user"
        }
        }