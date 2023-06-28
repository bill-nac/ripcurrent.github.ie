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

#### App Configuration
- add using the portal
- for a visual studio project, connect this service to the projects. Right click project and select connected services
- use the secrets manager to save secrets in development environment to local json file
