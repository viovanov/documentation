---
layout: default-devplatform
title: "HP Helion 1.2 Development Platform: Building and Deploying Windows and SQL Server Express Images"
permalink: /helion/devplatform/1.2/windows/building_windows
product: devplatform
product-version1: HP Helion Development Platform
product-version2: HP Helion Development Platform 1.2
role1: Systems Administrator 
role2: System Engineer
role3: Cloud Administrator
role4: Network Administrator
role5: Application Developer
Role6: Security Engineer
role7: Application Developer 
role8: ISV Developer
role9: Service Developer
authors: Patrick F

---
<!--UNDER REVISION-->

# HP Helion 1.2 Development Platform: Building and Deploying Windows and SQL Server Express Images

This document demonstrates how to create and deploy a Windows image in an HP Helion OpenStack environment to be used in Helion Development Plaftorm. Image creation is needed to enable Windows support in HDP. This process can take several hours (approximately 7hrs depending on hardware and network) and in most of the cases can be left unattended once the scripts get executed.

## Prerequsites

### Host Prerequisites

The following requirements pertain to the system where the Windows image will be created.

* MacOS X or Linux (Ubuntu recommended) non-virtualized environment. (i.e. the image cannot be created in a virtual machine).
* Virtualization support enabled
* 16 GB RAM recommended.
* 100 GB available disk space
* Connectivity to the Internet and the HOS environment where the Windows image will be deployed

### Software Prerequisites

* A Windows Server 2012R2 ISO image (Volume-licensed images can be obtained through MSDN for development or test; volume-licensed production images must be obtained through the OEM channel).
	* The ISO must be a retail (non-evaluation) image
	* The ISO must be an English-language version.
	* The name of the ISO file must be <code>en\_windows\_server\_2012\_r2\_with\_update\_x64\_dvd\_6052708.iso</code> <span style="color:red">Vlad, did we remove the name check?</span>
* Virtual Box version 4.3.26 or later: <a href="https://www.virtualbox.org/wiki/Downloads">Download</a>
* Virtio drivers version 0.1-81: <a href="http://alt.fedoraproject.org/pub/alt/virtio-win/stable/virtio-win-0.1-81.iso">Download</a>
* Download and extract the Glazier tool: <a href="https://drive.google.com/a/hp.com/folderviewid=0By3HV5Aek7gYfjg3TUVGT1RxeGhhZTBvN2JBR3Y4UWZZWXkycEprUGhSc0J3a19XcHJaTXM&usp=sharing">Download</a><span style="color:red"> this link is incorrect, need production link.</span> For more information about Glazier, see the <a href="/helion/devplatform/1.2/windows/glazier/">Glazier Reference Guide</a>.



### Setup Information Needed

* A Windows product key for Windows Server 2012R2. A volume license is strongly recommended, as temporary instances will be created that need product keys.
* The RC file for the target HOS environment. This can be downloaded from the Horizon interface, under **Project-&gt;Compute-&gt;Access & Security-&gt;API Access-&gt;Download OpenStack RC File**.
* The certificate for the target HOS environment. This can be found on the seed node, under /usr/local/share/ca-certificates/ephemeralca-cacert.crt.

## Creating and uploading images

### Step 1: Create a Glazier Virtual Machine

This VM is used to create the images for the guest OS.

1. Open Terminal and change to the Glazier directory where you extracted the tool.
2. Run the <code>create-glazier</code> command (To verify your parameters before starting the tool, you can use the <code>--dry-run</code> command line switch.)

	<pre>
	./create-glazier \
		--windows-iso &lt;path to Windows Server 2012R2 iso&gt; \
		--virtio-iso &lt;path to VirtIO iso&gt; \
		--product-key &lt;Windows Product Key&gt; \
		--os-network-id &lt;os network ID; found in Horizon on the Network Detail page under Project -&gt; Network -&gt; Networks -&gt; (select network name) &gt; \
		--os-key-name &lt;os region name; e.g. RegionOne&gt; 
		--os-security-group &lt;os security group; e.g Default&gt; \
		--os-flavor &lt;os flavor name: e.g. m1.small&gt; \
	</pre>
3. When the tool finishes, you will see a command prompt open in a Virtual Box instance. 
	
<span style="color:red">Need screenshot(s?) Should there be several screenshots here showing various steps of the Windows install process, plus the command prompt?</span>

### Step 2: Create and Initialize the OS Windows DEA Image

1. In the Glazier VM command prompt that opens after the end of the previous step, run the following command:

		New-Image -name "windows2012r2-windea" -GlazierProfilePath "windea"
2. Once the image gets created, run the following command to initialize it:
3. 
		Initialize-Image -Qcow2ImagePath "c:\workspace\windows2012r2-windea -ImageName "windea_snapshot"

### Step 3: Create and Initialize the OS SQL Server Express 2012 Image (Optional)

1. In the Glazier VM command prompt, run the following command:
	
		New-Image -name "windows 2012r2-sql2012" -GlazierProfilePath "mssql2012"

2. Once the image gets created, run the following command to initialize it:

		Initialize-Image -Qcow2ImagePath "c:\workspace\windows2012r2-sql2012" -ImageName "msssql2012_snapshot"

### Step 4: Create and Initialize the OS SQL Server Express 2014 Image (Optional)

1. In the Glazier VM command prompt, run the following command:
	
		New-Image -name "windows 2012r2-sql2014" -GlazierProfilePath "mssql2014"

2. Once the image gets created, run the following command to initialize it:

		Initialize-Image -Qcow2ImagePath "c:\workspace\windows2012r2-sql2014" -ImageName "msssql2014_snapshot"

## Enabling Windows and SQL Server in your ALS cluster
### Add Windows DEA

1. Create a yml file to add (e.g. <code>manifest.yml</code>)

		version: 1.2
		constructor-image-name: {?}
		seed-node-image-name: {Windows DEA Image Name}
		cluster-title: Win2012R2
		cluster-prefix: Win2012R2
		az: {az name}
		constructor-flavor: standard.medium
		flavor: standard.medium
		keypair-name: {key name}
		stack: win2012r2
		max-cluster-wait-duration: 30m
		network-name: {network name}

2. Run this command

		cf-mgmt add-role dea --load <file name>.yml

### Add SQL Server 2012 service

1. Create a yml file to add (e.g. <code>manifest.yml</code>)

		version: 1.2
		constructor-image-name: {?}
		seed-node-image-name: {SQL Image Image Name}
		cluster-title: mssql2012
		cluster-prefix: mssql2012
		az: {az name}
		constructor-flavor: standard.medium
		flavor: standard.medium
		keypair-name: {key name}
		stack: mssql2012
		max-cluster-wait-duration: 30m
		network-name: {network name}

2. Run this command for SQL Server 2012

		cf-mgmt add-service mssql2012 --load <file name>.yml

### Add SQL Server 2014 service

1. Create a yml file to add (e.g. <code>manifest.yml</code>)

		version: 1.2
		constructor-image-name: {?}
		seed-node-image-name: {SQL Image Image Name}
		cluster-title: mssql2014
		cluster-prefix: mssql2014
		az: {az name}
		constructor-flavor: standard.medium
		flavor: standard.medium
		keypair-name: {key name}
		stack: mssql2012
		max-cluster-wait-duration: 30m
		network-name: {network name}

2. Run this command for SQL Server 2014

		cf-mgmt add-service mssql2014 --load <file name>.yml
## Activating Windows Images

When a Windows DEA or SQL Server image is added to an ALS server, these instances need to be activated to be compliant with <a href="https://www.microsoft.com/licensing/">Microsoft licensing</a>. You can activate by either connecting to them with Remote Desktop and activating Windows normally, or by using KVM. To activate an image with KVM, do the following:

1. <span style="color:red">Do we need anything special?</span>



		