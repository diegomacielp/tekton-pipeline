`Tekton Pipeline`
---------------


# Building and Running

To build the application run the following commands:

```bash
npm install
npm run build
```

Now you are ready to run the application from your workstation with:


```bash
npm run start
```

Test the application endpoint with `curl`:

```bash
curl 127.0.0.1:8080
```

# Permissions

Mounting Volumes on Privileged Pods:

```bash
oc adm policy add-scc-to-user privileged -z pipeline
```

Allow Tekton service user to run commands in Argocd namespace

```bash
oc adm policy add-role-to-user admin system:serviceaccount:pida-diego:pipeline -n openshift-gitops
```

# Manifest secret.yaml

```bash
apiVersion: v1
kind: Secret
metadata:
  name: git-credentials
data:
  # cat ~/.ssh/id_rsa | base64 -w 0
  id_rsa:
  # cat ~/.ssh/known_hosts | base64 -w 0
  known_hosts: 
  # cat ~/.ssh/config | base64 -w 0
  config:
```