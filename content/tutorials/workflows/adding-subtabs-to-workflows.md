---
title: Adding SubTabs to Workflows
description: Piklist Workflow tabs can be enhanced with subtabs.
hidden: true
weight: 2
---


Piklist Workflow tabs can be enhanced with unlimited subtabs, allowing you to create more complex, but easy to manage, user interfaces.

{{< show-tutorial-start-folders >}}

IMPORTANT: You should already have a Piklist Workflow system set up before using this tutorial. If you do not, you can reference [this tutorial](/tutorials/workflows/building-first-workflow/).

In this example, we are going to place a subtab under a tab called `My Tab`.
1. Create a file under the `/workflows` folder.
2. The file header can contain all the parameters you use for a normal Workflow file. Additionally, you will add a `Tab` parameter which defines which tab your subtab will display under.

The following code snippet will display a subtab titled `My Subtab`, under a tab called `My Tab` in the `My Workflow` Flow, and make it the default tab.

```
<?php
/*
Title: My Subtab
Order: 10
Flow: My Workflow
Tab: My Tab
Default: true
*/
?>
```
