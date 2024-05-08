1. Create Service Principal
Run below and note JSON output
```
az ad sp create-for-rbac --name "cicd for rukasakurai/azure-search-openai-demo"
```

JSON output will look like the below
```
{
  "appId": "***",
  "displayName": "***",
  "password": "***",
  "tenant": "***"
}
```

2. Save the following JSON in a GitHub Secret named `AZURE_CREDENTIALS`
```
{
    "clientSecret":  <'password' from the JSON output of az ad sp create-for-rbac>,
    "subscriptionId":  <Azure Subscription ID>,
    "tenantId":  <'tenant' from the JSON output of az ad sp create-for-rbac>,
    "clientId":  <'appId' from the JSON output of az ad sp create-for-rbac>
}
```

3. Assign roles to Service Principal
- Contributor
- Role Based Access Control Administrator

4. Write workflow yaml if it does not exist
Use .github/workflows/cicd.yaml or write your own

## Troubleshotting
### azd up completes, but code deployement failed
#### Error Message (UI)
```
:( Application Error
If you are the application administrator, you can access the diagnostic resources.
```
#### Error Message (Azure Web App Log Stream)
```
[Error] Middleware: Failed to forward request to http://xxx.xxx.xxx.x:8000. Encountered a System.Net.Http.HttpRequestException exception after 220.561ms with message: Connection refused (xxx.xxx.xxx.x:8000). Check application logs to verify the application is properly handling HTTP traffic.
...
ModuleNotFoundError: No module named 'main'
```
#### Solution
Reran the GitHub Action that does azd up. Not sure what the issue was, but perhaps it was a trasient issue.