LAB - Basic Bash Scripting
=====================

A workshop for learning basic bash scripting.

If you already have the Educates operator installed and configured, to
deploy and view this basic bash scripting workshop, run:

```
kubectl apply -f workshop.yaml
kubectl apply -f training-portal.yaml
```

This will deploy a training portal hosting just this workshop. To get the
URL for accessing the training portal run:

```
kubectl get trainingportal/lab-bash-scripting
```

The training portal is configured to allow anonymous access.
