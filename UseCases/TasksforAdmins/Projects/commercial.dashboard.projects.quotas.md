---
layout: default
title: "HP Helion OpenStack&#174; Managing project quotas"
permalink: /helion/commercial/dashboard/managing/projects/quotas/
product: commercial.ga

---
<!--UNDER REVISION-->

<script>

function PageRefresh {
onLoad="window.refresh"
}

PageRefresh();

</script>

<!--
<p style="font-size: small;"> <a href="/helion/commercial/ga1/install/">&#9664; PREV</a> | <a href="/helion/commercial/ga1/install-overview/">&#9650; UP</a> | <a href="/helion/commercial/ga1/">NEXT &#9654;</a> 
-->

# HP Helion OpenStack&#174; Managing project quotas

Quotas are operational limits enforced on each project. 

To prevent system capacities from being exhausted without notification, you can set up quotas. 

For example, the number of gigabytes allowed per project can be controlled to make sure that a single project does not consume all of the disk space. 

### Modify a quotas ### {#quotamod}

1. [Launch the HP Helion OpenStack Helion Dashboard](/helion/openstack/dashboard/login/).

2. Click the **Projects** link on the **Admin** dashboard **Identity** panel.

3. For the project you want to modify, click **More &gt; Modify Quotas**. 

4. In the **Edit Project** screen, click the **Quota** tab (should be active).

5. Edit and of the following fields:

	* Metadata Items - Enter the maximum number of metadata items allowed for the project.</li>
	* VCPUs - Enter the maximum number of instance cores allowed for the project.</li>
	* Instances - Enter the maximum number of instances allowed for the project.</li>
	* Injected Files - Enter the maximum number of injected files allowed for the project.</li>
	* Injected File Content Bytes - Enter the maximum number of content bytes allowed per injected file  for the project.</li>
	* Volumes - Enter the maximum number of volumes allowed for the project.</li>
	* Volume Snapshots - Enter the maximum number of volume snapshots allowed for the project.</li>
	* Total Size of Volumes and Snapshots- Enter the maximum total size for all volumes and snapshots allowed for the project.</li>
	* RAM - Enter the maximum megabytes of instance RAM allowed  for the project.</li>

6. Click **Save**.<br>

	A message is displayed on successful modification.

<p><a href="#top" style="padding:14px 0px 14px 0px; text-decoration: none;"> Return to Top &#8593; </a>


----