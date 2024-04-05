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

Allows the Argocd service to deploy in the application namespace

```bash
oc adm policy add-role-to-user admin system:serviceaccount:openshift-gitops:openshift-gitops-argocd-application-controller -n pida-diego
```

# Tekton secret.yaml

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

# Argocd secret.yaml
```bash
kind: Secret
apiVersion: v1
metadata:
  name: git-credentials
  namespace: openshift-gitops
  labels:
    argocd.argoproj.io/secret-type: repository
data:
  # Github
  name: R2l0aHVi
  # cat ~/.ssh/known_hosts | base64 -w 0
  sshPrivateKey:
  # git
  type: Z2l0
  # Z2l0QGdpdGh1Yi5jb206ZGllZ29tYWNpZWxwL3Rla3Rvbi1waXBlbGluZS5naXQ=
  url: Z2l0QGdpdGh1Yi5jb206ZGllZ29tYWNpZWxwL3Rla3Rvbi1waXBlbGluZS5naXQ=
type: Opaque
```