**Authentication**
- k8s has 2 types of user : 
    - humans -> (Users)
    - robots(other process/applications) -> service account
- k8 doesn't manage user account natively, it depends on external source like 
    - a file with user details or certificates
    - 3rd party identity service like LDAP
- so we cannot create/list users in k8 cluster

*Users auth*
- All user access to the cluster is managed by kubeapi-server wether it comes from kubectl or curl
- kubeapi-server authenticates the rerest before processing it
- below auth mechanism can be used
    - Static password files: list of username and password in a file. In this approch a csv with username and passwords is uploaded to kubeapiserver and whenever a user makes a request he need to add this "user:pass" in the request
    
    - Static token file: username and tokens in a file. In this approach a similar file but with token instead of password is uploaded to kubeapiserver and every time the user makes a request he need to add a --header "Bearer token"

    - Or authenticate using certificates
    - Or connect to 3rd party authentication protocols like LDAP, kurberos etc

- 
    
