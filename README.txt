Azure Settings

1. Resource Group
- Resource Group Name: 

2. SQL Database
- DB name: 
- Server: 
- DB region: 
- Admin login: 
- Admin password: 
- Resource group: 
- DB workload env: 
- DB compute + storage: 
- Press the "Next: Networking" button, then select "Public Endpoint", and set both of the Firewall rules that appear to "Yes".
- Set everything else to default
Run SQL queries in sql_scripts/ directory after completion, starting from the users table. Don't forget to take screenshots.

3. Storage Account
- Resource group: 
- Storage account name:  (needs to be unique)
- Advanced - Allow enabling anonymous access on individual containers: Enable
- Advanced - Access tier: Cool
- Network access: Enable public access from all networks (the default)
- Create container named "images". Set its access level to Container.
- From Security + networking > Access keys:
- Blob Storage key: 
- Blob connection string: DefaultEndpointsProtocol=https;AccountName=cms1321;AccountKey=xR5Gjh49yb94o6o+yY1Cc1cJkOs05HRQvw8rSSd5sTxLD7Vi0E3kSaJUodWLVvXY9ZeMG6Q5nilq+AStsiI9Bw==;EndpointSuffix=core.windows.net
4. Microsoft Entra ID
4.1. App Registration
- Name: 
- Who can use? "Accounts in any organizational directory (Any Microsoft Entra ID tenant - Multitenant) and personal Microsoft accounts (e.g. Skype, Xbox)"
4.2. Secret Creation
- Secret description: 
- Secret Key: 
- Client Secret: 
- Application (client) ID: 

5. Web App
- Name: 
- Runtime stack: Python 3.10
- Pricing Plan: Free F1
- If you are getting a "Validation failed for a resource" error, pick a different region.

After creation:
- Settings -> Environment variables - Add the following variables (sample values are included, replace them with your values):
- BLOB_ACCOUNT: 
- BLOB_CONTAINER: 
- BLOB_STORAGE_KEY: 
`- BLOB_CONNECTION_STRING: DefaultEndpointsProtocol=https;AccountName=cms1321;AccountKey=xR5Gjh49yb94o6o+yY1Cc1cJkOs05HRQvw8rSSd5sTxLD7Vi0E3kSaJUodWLVvXY9ZeMG6Q5nilq+AStsiI9Bw==;EndpointSuffix=core.windows.net`
- SQL_SERVER: 
- SQL_DATABASE: 
- SQL_USER_NAME: 
- SQL_PASSWORD: 
- CLIENT_SECRET: 
- SECRET_KEY: 
- CLIENT_ID: 5
Deployment Center
- Source: GitHub
- Pick the repo that contains the starter files.

6. Setting up OAuth2
At this point, your application should already be running. You should already be able to log in with username admin and password pass and you can create new posts or update existing ones.

- The next part is getting the OAuth2 login to work.

- Go to Microsoft Entra ID > App Registrations, click on the App Registration created earlier, and then pick Authentication from the left sidebar.

6.1. Microsoft Entra ID - Authentication - Add a Platform - Web
- Redirect URIs: https://[IP ADDRESS FROM VM or WEB APP ADDRESS]/getAToken
- logout URL: https://[IP ADDRESS FROM VM or WEB APP ADDRESS]/login