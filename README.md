# OAuthManager <a href="https://travis-ci.org/taruntomar/OAuthManager" target="_blank"><img src="https://travis-ci.org/taruntomar/OAuthManager.svg?branch=master" /></a>
A library to facilitate authentication using OAuth protocol

This library can be used to download auth token from AzureAD using OAuth2.0
It supports for Grant Type: Client Credential, User Credential

Get Token By Client Credential:
```
using Open.OAuthManager.AzureAD;

Authenticator auth = new Authenticator();

auth.Config.Client.Id= ""; // client id registered in AzureAD info
auth.Config.Client.Secret= ""; 
auth.Config.BaseURL= ""; // url of the authority which provide access. ex: https://management.core.windows.net/
auth.Config.TanentID= ""; // id of Tanent in AD
auth.Config.Resource = ""; // resource for which access is require ex: https://management.azure.com/
auth.Config.Scope = ""; // level of access in the resource 

string token = auth.GetAccessToken_FromClientCredential();
```

Get Token By User Credential:
```
using Open.OAuthManager.AzureAD;
Authenticator auth = new Authenticator();
// firstly download the authcode 
auth.Config.
string authCode = auth.GetAuthCode();

auth.Client.Id= ""; // client id registered in AzureAD info
auth.Client.Secret= ""; 
auth.BaseURL= ""; // url of the authority which provide access. ex: https://management.core.windows.net/
auth.TanentID= ""; // id of Tanent in AD
auth.Resource = ""; // resource for which access is require ex: https://management.azure.com/
auth.Scope = ""; // level of access in the resource 

string token = auth.GetAccessToken_FromClientCredential();
```

Firstly create the configuration object


```c#
AuthConfig config = new AuthConfig();
config.LoggedInUserEmail = "<current_user_email>";
config.TanentId = "<TanentID_in_AzureAD>";
config.RedirectURL = "<URL_which_will_call_to_pass_authcode>";
config.ClientId="<ClientID_RegisteredWithAzureAD>";

DatabaseManager dbManager = new DatabaseManager(connectionString);
AzureADE2EManager authManager = new AzureADE2EManager(config,dbManager);
Token token = authManager.GetAccessToken();
```

