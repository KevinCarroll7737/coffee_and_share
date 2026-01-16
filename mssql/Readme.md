MSSQL Exploitation: Beyond `xp_cmdshell`
===

## Slides
<img width="2560" height="1305" alt="image" href="https://github.com/KevinCarroll7737/coffee_and_share/blob/main/mssql/Readme.md](https://github.com/KevinCarroll7737/coffee_and_share/blob/main/mssql/slides.html" src="https://github.com/user-attachments/assets/b5b16964-183e-4ff6-a51c-7e98e656a723" />

## Testing Environement

    # Status
    kubectl get pods -n pentest-lab

    # Delete and recreate
    kubectl delete deployment -n pentest-lab vulnerable-app
    kubectl apply -f mssql-pentest-lab.yaml

    # Forward port to access via browser & cli
    kubectl port-forward -n pentest-lab svc/vulnerable-app 5000:5000
    kubectl port-forward -n pentest-lab svc/mssql 1433:1433

    # Connect to the DB
    kubectl exec -it -n pentest-lab deployment/mssql -- /bin/bash
    /opt/mssql-tools18/bin/sqlcmd -S localhost -U sa -P 'YourStrong@Passw0rd' -C
    
    # Watch the logs
    kubectl logs -n pentest-lab -l app=vulnerable-app -f
