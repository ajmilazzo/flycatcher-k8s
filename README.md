# flycatcher-k8s
k3os + security tools

## Overview
This is a collection of security tools customized for use in k3os.

## Usage
See [pwn-k8s](https://github.com/ajmilazzo/pwn-k8s) for an exploitable example to trigger a number of security rules

## Gatekeeper
### Add Repo
```
helm repo add gatekeeper https://open-policy-agent.github.io/gatekeeper/charts
helm repo update
```

### Install
```
helm install gatekeeper/gatekeeper --name-template=gatekeeper --namespace gatekeeper-system --create-namespace
```

### Uninstall
```
helm uninstall gatekeeper --namespace gatekeeper-system 
```

### Policies
```
kubectl apply -f https://raw.githubusercontent.com/open-policy-agent/gatekeeper-library/master/library/general/disallowanonymous/template.yaml
```

## Kyverno
### Add Repo
```
helm repo add kyverno https://kyverno.github.io/kyverno/
helm repo update
```

### Install
```
helm install kyverno kyverno/kyverno -n kyverno --create-namespace --set replicaCount=1
```

### Uninstall
```
helm uninstall kyverno kyverno/kyverno --namespace kyverno
```

### Policies
```
helm install kyverno-policies kyverno/kyverno-policies -n kyverno
```

## Falco
### Add Repo
```
helm repo add falcosecurity https://falcosecurity.github.io/charts
helm repo update
```

### Install
```
helm install falco falcosecurity/falco --namespace falco --create-namespace -f ./values.yaml
```

### Upgrade
```
helm upgrade falco falcosecurity/falco --namespace falco --create-namespace -f ./values.yaml
```

### Uninstall
```
helm uninstall falco --namespace falco
```
