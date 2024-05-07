1. Create Service Principal
Run below and note JSON output
```
az ad sp create-for-rbac --name "cicd for rukasakurai/azure-search-openai-demo"
```

2. Save noted JSON in GitHub Secret

3. Assign roles to Service Principal
- Contributor
- Role Based Access Control Administrator

4. Write workflow yaml if it does not exist

