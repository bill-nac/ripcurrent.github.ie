# Azure
General concepts, hints and tips.

## Applications

### App Registrations
- Use App Registration to register *your* application for use with AD
- for identity provider to know that a user has access to an app, the user and the app must be registered
- Also allows us:
  -  to brand the sign-on experience, control what users have access
  - The app can request scope permissions e.g. "User.Read" to read the user profile
  - Share a secret with Identifity platform which *proves the apps identity*. (used as our app is confidential). Uses this secret when requesting tokens.

### Enterprise Application
- Use these to register an instance of this application. Other organisations could have an Enterprise Application for your App Registration.
- You'll see many Enterprise applications listed as this will contain those which are used by your organisation but built but others (e.g. Adobe etc)
- The enterprise application resource controls what the app can do in our tenant
  
### Web App
- create a web application (does not need an App Registration etc)
- push code to this using GIT. This is a great option, can set this for CI.
- note the use of logs under *App Service Logs*
- Git Workflow:
  - Actions builds the projects
  - Deployments can be seen under Environments
  - The configuration files are saved has .yml with the code
- Alternative to pushing code to GITHub and then using Worflow is:
  - push code directly to Web App
  - there is an automatic build under Deployment area [Oryx](https://github.com/microsoft/Oryx/tree/main)
  - setup your deployment/git options if need be 

### App Configuration
the simplest app configuration is just to use the "Configuration" tab in a Wep App blade.

alternative is to use the fully featured App Configuration service.
- add using the portal
- save the connection string to secrets manager and add reference using:
 ```
dotnet user-secrets init
dotnet user-secrets set ConnectionStrings:AppCondig "<url here>"
dotnet add package Microsoft.Azure.AppConfiguration.AspNetCore
```
- remember to use this on server you'll need to add the AppConfig endpoint under the App Settings, Connection string area

in the VS project
- add a model for the Settings
- read the connection string, load configuration, add bind to model
```
// Retrieve the connection string
string connectionString = builder.Configuration.GetConnectionString("AppConfig");

// Load configuration from Azure App Configuration
builder.Configuration.AddAzureAppConfiguration(connectionString);

// Bind configuration "TestApp:Settings" section to the Settings object
```

### Secrets Manager
- use the secrets manager to save secrets in development environment to local json file

### Script to create basic App Service
```
az group create --name myResourceGroup --location "West Europe"
az appservice plan create --name myAppServicePlan --resource-group myResourceGroup --sku B1 --is-linux
az webapp create --resource-group myResourceGroup --plan myAppServicePlan --name "BillAzureMonitorTestDebug" --runtime "PHP|8.1" --deployment-local-git
az webapp config appsettings set --name "BillAzureMonitorTestDebug" --resource-group myResourceGroup --settings DEPLOYMENT_BRANCH='main'
git clone https://github.com/Azure-Samples/App-Service-Troubleshoot-Azure-Monitor
cd App-Service-Troubleshoot-Azure-Monitor
git branch -m main
git remote add azure https://bill.tierney2@billazuremonitortestdebug.scm.azurewebsites.net/BillAzureMonitorTestDebug.git
git push azure main
```
