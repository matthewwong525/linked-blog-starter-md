### Connecting to the OCI VM
1. Set permissions for private key on win ( One time setup)
```
The `ssh` command requires strict permissions on the private key file.
    
    - Right-click the private key file, select **Properties**, then go to the **Security** tab and click **Advanced**.
        
    - Click **Disable inheritance** and choose to **Convert inherited permissions into explicit permissions**.
        
    - Remove all permission entries except for your user account. Ensure your user account has **Full control**.
```

2. login to the vm from any terminal
```powershell
ssh -i C:\Users\Neuvillette\Downloads\ssh-key-2025-09-18.key ubuntu@141.148.203.129
```

### Traefik setup
[[Traefik]]

