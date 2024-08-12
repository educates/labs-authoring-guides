---
title: Starting a Workshop
---

From the training portal start up an instance of the workshop displayed.

In this configuration the workshop session will be created on demand, however
the training portal can be configured to pre-create a pool of reserved workshop
sessions ready for immediate allocation to users when requested.

Overall, even without reserved sessions, unless specific workshops have time
consuming setup steps, starting up a workshop session should be relatively quick
as only a container within the Kubernetes cluster needs to be created, in
comparison to a full virtual machine as is typical with other training systems.

Since the purpose of this workshop is to learn about using Educates and not to
actually complete the workshop you deployed in this exercise, you can exit the
workshop by selecting "Terminate Session" from the drop down menu top right of
the workshop session dashboard of the separate web browser window which was
created. Don't terminate the workshop session here in this dashboard though as
otherwise you will need to start over.

So that we have sufficient resources to complete later steps of this workshop,
also delete the workshop you just deployed by running:

```terminal:execute
command: educates delete-workshop -f https://github.com/educates/lab-k8s-fundamentals/releases/latest/download/workshop.yaml
```
