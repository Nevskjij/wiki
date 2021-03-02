you need to have [azure CLI](https://docs.microsoft.com/en-us/cli/azure/)

here is script for powershell that will create new storage

```powershell
# Change these four parameters as needed
$ACI_PERS_RESOURCE_GROUP="test"
$ACI_PERS_STORAGE_ACCOUNT_NAME="<name>"
$ACI_PERS_LOCATION="eastus2"
$ACI_PERS_SHARE_NAME="acishare"

# Create the storage account with the parameters
az storage account create  --resource-group $ACI_PERS_RESOURCE_GROUP     --name $ACI_PERS_STORAGE_ACCOUNT_NAME     --location $ACI_PERS_LOCATION     --sku Standard_LRS

# Create the file share
az storage share create --name $ACI_PERS_SHARE_NAME   --account-name $ACI_PERS_STORAGE_ACCOUNT_NAME

$STORAGE_KEY=$(az storage account keys list --resource-group $ACI_PERS_RESOURCE_GROUP --account-name $ACI_PERS_STORAGE_ACCOUNT_NAME --query "[0].value" --output tsv)
echo $STORAGE_KEY
```

when you have your storage account, you can proceed to configure container:
1. create container config file: <name>.yaml
2. copy and paste from here
3. fill out missing info
```yaml
apiVersion: '2019-12-01'
location: eastus2
name: tf2autobot
properties:
  containers:
  - name: <container name>
    properties:
      environmentVariables:
        - name: 'NODE_ENV'
          value: 'production'
        - name: 'STEAM_ACCOUNT_NAME'
          value: ''
        - name: 'STEAM_PASSWORD'
          secureValue: ''
        - name: 'STEAM_SHARED_SECRET'
          secureValue: ''
        - name: 'STEAM_IDENTITY_SECRET'
          secureValue: ''
        - name: 'BPTF_ACCESS_TOKEN'
          secureValue: ''
        - name: 'BPTF_API_KEY'
          secureValue: ''
        - name: 'ADMINS'
          value: '["<your-steam-id>"]'
        - name: 'KEEP'
          value: ''
        - name: 'GROUPS'
          value: ''
        - name: 'ALERTS'
          value: '["trade"]'
        - name: 'SKIP_BPTF_TRADEOFFERURL'
          value: 'true'
        - name: 'SKIP_UPDATE_PROFILE_SETTINGS'
          value: 'true'
        - name: 'TIMEZONE'
          value: 'Europe/Bratislava'
        - name: 'CUSTOM_TIME_FORMAT'
          value: 'DD MMM YYYY, HH:mm:ss ZZ'
        - name: 'DEBUG'
          value: 'true'
        - name: 'DEBUG_FILE'
          value: 'true'
      image: tf2autobot/tf2autobot:bdaf043276fccd53f864dfb23c609fd8496ca2ad-14.16.0-alpine
      resources:
        requests:
          cpu: 1.0
          memoryInGB: 0.5
      volumeMounts:
      - mountPath: /app/files
        name: filesharevolume
  osType: Linux
  restartPolicy: Always
  volumes:
  - name: filesharevolume
    azureFile:
      sharename: acishare
      storageAccountName: <$ACI_PERS_STORAGE_ACCOUNT_NAME>
      storageAccountKey: <$STORAGE_KEY>
tags: {}
type: Microsoft.ContainerInstance/containerGroups
```
