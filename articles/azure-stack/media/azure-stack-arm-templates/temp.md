Add a new Azure Stack tenant account in Azure Active Directory
After deploying the Azure Stack POC, you'll need a tenant user account so you can explore the tenant portal and test your offers and plans. You can create a tenant account by using the Azure portal or by using PowerShell.
Create an Azure Stack tenant account using the Azure portal
You must have an Azure subscription to use the Azure portal.
Log in to Azure.
In Microsoft Azure left navigation bar, click Active Directory.
In the directory list, click the directory that you want to use for Azure Stack, or create a new one.
On this directory page, click Users.
Click Add user.
In the Add user wizard, in the Type of user list, choose New user in your organization.
In the User name box, type a name for the user.
In the @ box, choose the appropriate entry.
Click the next arrow.
In the User profile page of the wizard, type a First name, Last name, and Display name.
In the Role list, choose User.
Click the next arrow.
On the Get temporary password page, click Create.
Copy the New password.
Log in to Microsoft Azure with the new account. Change the password when prompted.
Log in to https://portal.azurestack.local with the new account to see the tenant portal.
Create an Azure Stack tenant account using PowerShell
If you don't have an Azure subscription, you can't use the Azure portal to add a tenant user account. In this case, you can use the Azure Active Directory Module for Windows PowerShell instead.
[AZURE.NOTE] If you are using Microsoft Account (Live ID) to deploy Azure Stack PoC, you can't use AAD PowerShell to create tenant account. 
Install the Microsoft Online Services Sign-In Assistant for IT Professionals RTW.
Install the Azure Active Directory Module for Windows PowerShell (64-bit version) and open it.
Run the following cmdlets:
# Provide the AAD credential you use to deploy Azure Stack PoC

        $msolcred = get-credential

# Add a tenant account "Tenant Admin <username>@<yourdomainname>" with the initial password "<password>".

        connect-msolservice -credential $msolcred
        $user = new-msoluser -DisplayName "Tenant Admin" -UserPrincipalName <username>@<yourdomainname> -Password <password>
        Add-MsolRoleMember -RoleName "Company Administrator" -RoleMemberType User -RoleMemberObjectId $user.ObjectId

Sign in to Microsoft Azure with the new account. Change the password when prompted.
Sign in to https://portal.azurestack.local with the new account to see the tenant portal.
