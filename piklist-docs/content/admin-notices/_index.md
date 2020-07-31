---
title: "Admin Notices"
description: "Creating Admin Notices with Piklist is very easy, and can be done without writing any PHP."
weight: 110
---

{{% columns_2 %}}

1. Decide whether you are going to include your notice in a plugin or theme.
2. Create a `notices/` folder in your `parts/` folder (e.g. `/parts/notices/`).
3. Now, create a php file in your notices folder. This file will hold your notice code.
4. At the top of the file, add the following comment block which tells Piklist this is an “updated” type notice, and can be dismissible by the user.

### [View Tutorials &rightarrow;](/tutorials/admin-notices/)

{{% /columns_2 %}}

{{< columns_2 >}}

{{% folder %}}
/parts/notices/
{{% /folder %}}

{{< tabs >}}
{{< tab name="PHP" codelang="php" >}}
<?php
/*
Notice Type: updated
Dismiss: true
*/
?>
<p>This is my notice</p>
{{< /tab >}}
{{< tab name="CSS" codelang="css" >}}
println "This is tab 2."
{{< /tab >}}}
{{< /tabs >}}

{{< /columns_2 >}}