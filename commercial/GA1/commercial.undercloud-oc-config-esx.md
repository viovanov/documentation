---
layout: default
title: "HP Helion OpenStack: Working with ESX Clusters"
permalink: /helion/openstack/ga/undercloud/oc/config/esx/
product: commercial.ga

---
<!--UNDER REVISION-->


<script>

function PageRefresh {
onLoad="window.refresh"
}

PageRefresh();

</script>

<!---
<p style="font-size: small;"> <a href="/helion/openstack/install-beta/prereqs/">&#9664; PREV</a> | <a href="/helion/openstack/install-beta-overview/">&#9650; UP</a> | <a href="/helion/openstack/install-beta/vsa/">NEXT &#9654;</a> </p> --->

##Working with EXS Clusters
 
In the UnderCloud, you register your vCenter and import the clusters from the EON data of the registered vCenter. These resources are available in your cloud after registration and it can be allocated for the usage of cloud. Based on your preference and usage you can select the available clusters and activate it. 

 
##Activate clusters

Perform the following steps to activate clusters:

1. In the Horizon Undercloud Dashboard, click the **Resource** Tab in the left panel.<br> The tab displays an option in the left panel.

2. Click **Overcloud** and then select **Configure** to open Configured Cloud page. 

3. Click **Activate Clusters** on the top right corner of the page to configure the clusters for the cloud. The page navigates to Configure ESX Computes page.

4. Select the desired cluster(s) from the **Available vCenter Choices** box list. The selected cluster(s) is displayed in the **Selected vCenter Choices** box.

5. (Optional) Click **Choose All** displayed below the **Available vCenter Choices** box to select all the  displayed clusters.

6. Click  &rarr; to move the selected clusters in the **Selected vCenter Choices** box list. 

7. (Optional) Click **Remove All** displayed  below the **Selected vCenter Choices** box to remove all the listed clusters. <br>OR<br> Select the desired cluster(s) from the **Selected vCenter Choices** box list and click &larr; to move the selected cluster (s) in the **Available vCenter Choices** box.

5. Click **Configure**. After successful configuration of clusters a message is displayed. <br>The configured cluster(s) get listed in the in the **Activated Clusters** table.



<a href="#top" style="padding:14px 0px 14px 0px; text-decoration: none;"> Return to Top &#8593; </a>

----
####OpenStack trademark attribution
*The OpenStack Word Mark and OpenStack Logo are either registered trademarks/service marks or trademarks/service marks of the OpenStack Foundation, in the United States and other countries and are used with the OpenStack Foundation's permission. We are not affiliated with, endorsed or sponsored by the OpenStack Foundation, or the OpenStack community.*