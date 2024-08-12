---
title: Deploy the Workshop
---

To deploy the workshop from the current directory we now need to run:

```terminal:execute
command: educates deploy-workshop
```

This is similar to how we deployed a previously published workshop except that
since we are running it out of the directory for the workshop it will use the
version of the workshop we just published to the local image registry.

Hop back over to the web browser window where the training portal was running
and refresh the page, or once again run:

```terminal:execute
command: educates browse-workshops
```

Start the workshop for the newly created demo workshop to verify it is working
and to view the default workshop instructions.
