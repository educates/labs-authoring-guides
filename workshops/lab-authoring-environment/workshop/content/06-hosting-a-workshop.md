---
title: Hosting a Workshop
---

We are now ready to deploy our first workshop.

For this we will use a previously published workshop by running the command:

```terminal:execute
command: educates deploy-workshop -f https://github.com/educates/lab-k8s-fundamentals/releases/latest/download/workshop.yaml
```

We will dig into what is happening under the covers later in the workshop, but
the effect of this command is to load the definition of the workshop into the
Kubernetes cluster, with the workshop then being made available through the
Educates training portal service.

To access the training portal service and browse the workshops hosted by it,
run the command:

```terminal:execute
command: educates browse-workshops
```

When the training portal service is ready, this should automatically open a new
web browser window. If you find that your web browser blocks opening of the new
window, then you can instead click on the link display in the terminal. Again
depending on the browser, clicking on the action block a second time after a few
seconds may also work to open a new window with the workshop. If you still have
issues, you can cut and paste the URL displayed in the terminal into a new
browser window yourself.

This is only an issue when trying to run Educates inside of Educates as we are
with this workshop. The underlying reason and a solution in this specific case
is still being investigated. If using these commands from your own local
computer with a separate Kubernetes cluster there should be no issue.
