---
layout: default
title: "HP Helion OpenStack&#174; Edition: Manage Storage"
permalink: /helion/openstack/ga/sirius/cli/workflow/
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
<p style="font-size: small;"> <a href="/helion/openstack/install-beta/kvm/">&#9664; PREV</a> | <a href="/helion/openstack/install-beta-overview/">&#9650; UP</a> | <a href="/helion/openstack/install-beta/esx/">NEXT &#9654;</a> </p> -->


# Sirius CLI Workflow

This page describes the workflow for HP StoreVirtual and HP 3PAR StoreServ integration to your cloud using the Sirius CLI.

* [Before you begin](#before-you-begin)

* [Process flow](#process-flow)

* [Add and configure HP StoreVirtual to your cloud inventory](#add-configure-storevirtual)

* [Add and configure HP 3PAR StoreServ](#add-configure-storeserv) 

* [Reconfigure and update cloud](#reconfigure-update)

## Before you begin <a name="add-backend"></a>

Ensure the following prerequisites are fulfilled before start:

* HP Helion Cloud is deployed 

* The block storage devices (HP StoreVirtual, HP 3PAR StoreServ) are accessible from the Undercloud

##Process Flow

Configuration of block storage comprises of registering the resources to the cloud inventory, adding them as a backend, reconfiguring and updating the cloud. The following diagram provides a high level view of the process flow.

<a href="javascript:window.open('/content/documentation/media/sirius-cli-processflow.png','_blank','toolbar=no,menubar=no,resizable=yes,scrollbars=yes')">Process Flow Diagram (opens in a new window)</a>


## Add and configure HP StoreVirtual to your cloud inventory {#add-configure-storevirtual}

Perform the following steps to add and configure Storevirtual.

* [Register StoreVirtual clusters to the cloud inventory](#register-storeirtual)

* [Add StoreVirtual clusters as a backend for the cloud](#add-backend)

* [Preview the cinder configuration for the StoreVirtual cluster](#preview-cluster)

* [View the list of configured StoreVirtual backends](#view-configured-list) 


### Register StoreVirtual clusters to the cloud inventory{#register-storeirtual}

Ensure that the cluster details entered in the command correspond with the actual cluster details from the Centralized Management Console (CMC) tool.

To register StoreVirtual clusters, enter the following command

	sirius register-storevirtual-cluster –name=<CLUSTER_NAME> --hostname=<CLUSTER_IP_ADDRESS> --subnet=<SUBNET> --username=<USERNAME> --password=<PASSWORD> --port=<SSH_PORT>

The sample output of the above command is given below:


	  Property   | Value                                |
	+------------+--------------------------------------+
	| created_at | 2014-08-23 02:49:41.066854           |
	| deleted    | False                                |
	| hostname   | 10.1.192.47                          |
	| id         | 21372fc0-2a70-11e4-af1e-00cd664a1470 |
	| name       | skcluster01                          |
	| password   | <SANITIZED>                          |
	| port       | 16022                                |
	| status     | registered                           |
	| subnet     | 255.255.0.0                          |
	| updated_at | 2014-08-23 02:49:41.066921           |
	| username   | shausy                               |
	+------------+---------------------------------------


###Add StoreVirtual clusters as a backend for the cloud {#add-backend}

The VOLUME&#095;BACKEND&#095;NAME parameter allows you to map all the StoreVirtual clusters with the same VOLUME&#095;BACKEND&#095; value to a specific volume type, created in the overcloud. Adding a StoreVirtual cluster as a backend moves the cluster to  the 'reserved' state which implies that the cluster cannot be removed from the cloud unless the corresponding backends are removed.

To add a backend, enter the following command

	sirius add-storevirtual-backend <CLUSTER_ID> --backend-name <VOLUME_BACKEND_NAME>

The sample output of the above command is given below:

	+----------------------------------------------------------------------+
	| Property                      | Value                                                                |
	+-------------------------------+----------------------------------------------------------------------+
	| backend_id                    | cluster_8f45ef72-2a77-11e4-af1e-00cd664a1470                         			                    |
	| hplefthand_api_url            | https://10.1.192.47:8081/lhos                                       			                    |
	| hplefthand_clustername        | skcluster01                                                          			                    |
	| hplefthand_debug              | false                                                               			                    |
	| hplefthand_iscsi_chap_enabled | true                                                                 			                    |
	| hplefthand_password           | password                                                             		                     	|
	| hplefthand_username           | shausy                                                               			                    |
	| volume_backend_name           | lhn                                                                  		                      	|
	| volume_driver                 | cinder.volume.drivers.san.hp.hp_lefthand_iscsi.HPLeftHandISCSIDriver |
	+-------------------------------+----------------------------------------------------------------------+

###Preview the cinder configuration for StoreVirtual cluster{#preview-cluster}

To view the StoreVirtual cluster configuration, enter the following command

	sirius storevirtual-cluster-show <CLUSTER_ID> --backend-name <VOLUME_BACKEND_NAME>

The sample output of the cinder.conf is given below:

	[cluster_f2b30740-455a-11e4-a483-00b53da47ef7]
	hplefthand_iscsi_chap_enabled=true
	hplefthand_password=password
	hplefthand_clustername=skcluster01
	volume_backend_name=lhn
	volume_driver=cinder.volume.drivers.san.hp.hp_lefthand_iscsi.HPLeftHandISCSIDriver
	hplefthand_api_url=https://10.1.192.47:8081/lhos
	hplefthand_debug=false
	hplefthand_username=shausy

###View the list of configured StoreVirtual backends {#view-configured-list}

To view the list of configured StoreVirtual backends, enter the following command

	sirius storevirtual-backend-list

The sample output of the above command is given below:


	+----------------------------------------------+--------------+---------------------+
	| Backend ID                                   | Cluster Name | Volume Backend Name |
	+----------------------------------------------+--------------+---------------------+
	| cluster_8f45ef72-2a77-11e4-af1e-00cd664a1470 | skcluster01  | lhn                 |
	| cluster_f2b30740-455a-11e4-a483-00b53da47ef7 | skcluster02  | lhn                 |
	+----------------------------------------------+--------------+---------------------+

## Add and configure HP 3PAR StoreServ to your cloud inventory {#add-configure-storeserv}

Perform the following steps to add and configure StoreServ.

*  [Register StoreServ to the cloud inventory](#register-storeserv)

*  [Register StoreServ CPG to the cloud inventory](#register-inventory)

*  [Add StoreServ CPG as a backend for the cloud](#add-cpg)

*  [Preview the cinder configuration for the StoreServ CPG](#preview-storeserv-cpg)

*  [View the configured StoreServ backend list](#view-storeserv-list)  


###Register StoreServ to the cloud inventory {#register-storeserv}

To register StoreServ, enter the following command

	sirius register-storeserv --name <STORESERV_NAME> --hostname <STORESERV_IP> --username <USERNAME> --password <PASSWORD> --port <SSH_PORT> --san-ip <SAN_IP> --san-username <SAN_USERNAME> --san-password <SAN_PASSWORD> --device-type <DEVICE_TYPE>

*Additional arguments*: --iscsi-ip <ISCSI_IP> [required for iSCSI type devices].


The sample output of the above command is given below:

	+--------------+--------------------------------------+
	| Property     | Value                                |
	+--------------+--------------------------------------+
	| created_at   | 2014-08-23 03:00:30.503326           |
	| deleted      | False                                |
	| device_type  | iscsi                                |
	| hostname     | 15.214.241.21                        |
	| id           | a438b0b4-2a71-11e4-af1e-00cd664a1470 |
	| iscsi_ip     | 10.1.2.200                           |
	| name         | storeserv01                          |
	| password     | <SANITIZED>                          |
	| port         | 8080                                 |
	| san_ip       | 15.214.241.21                        |
	| san_password | 3pardata                             |
	| san_username | 3paradm                              |
	| status       | registered                           |
	| updated_at   | 2014-08-23 03:00:30.503439           |
	| username     | 3paradm                              |
	+--------------+--------------------------------------+

###Register StoreServ CPG to the cloud inventory{#register-inventory}

List the available CPGs in the StoreServ device. From the available CPG list identify the ones to be registered to the cloud using the following command

	sirius storeserv-show <STORESERV_ID> --cpg-list true

The sample output of the above command is as below:

	+--------------------------------------+------------+-------+------+
	| UUID                                 | Name       | State | RAID |
	+--------------------------------------+------------+-------+------+
	| 6287cd1a-f8fb-4e10-93b0-88152db3b5df | 3par_iscsi | 1     | 2    |
	| b86f8f87-d546-40b6-9ac5-3fa5169958dd | 3par_FC    | 1     | 4    |
	| db8b945c-b4f1-464d-9790-554d9b8c321e | FC_r1      | 1     | 2    |
	| f3740765-119f-4d0d-9bc5-c254cd0209f4 | FC_r61     | 1     | 4    |
	+--------------------------------------+------------+-------+------+

Register the CPG(s) under the StoreServ using the following command. Multiple CPGs can be registered at a time for a given StoreServ device


	sirius register-cpg <STORESERV_ID> --cpgs [<CPG_ID> <CPG_ID>]


Verify the registered CPG list

	sirius cpg-list <STORESERV_ID>

The sample output of the above command is as below:

		+--------------------------------------+---------+-------+------+------------+
		| ID                                   | Name    | State | RAID | Status     |
		+--------------------------------------+---------+-------+------+------------+
		| b86f8f87-d546-40b6-9ac5-3fa5169958dd | 3par_FC | 1     | 4    | registered |
		| db8b945c-b4f1-464d-9790-554d9b8c321e | FC_r1   | 1     | 2    | registered |
		+--------------------------------------+---------+-------+------+------------+

### Add StoreServ CPG as a backend for the cloud {#add-cpg}

The VOLUME&#095;BACKEND&#095;NAME parameter allows you to map all the StoreServ CPGs with the same VOLUME&#095;BACKEND&#095;NAME value to a specific volume type, created in the overcloud.
Adding a StoreServ CPG as a backend will move the CPG to 'reserved' state which implies that the CPG cannot be removed from the cloud unless the corresponding backend is removed.

To add the StoreServ CPG as backend, enter the following command

	sirius add-storeserv-backend <STORESERV_ID> --cpg-id <CPG_ID> --backend-name <VOLUME_BACKEND_NAME>

The sample output of the above command is given below:

	+---------------------+--------------------------------------------------------+
	| Property            | Value                                                  |
	+---------------------+--------------------------------------------------------+
	| backend_id          | CPG_b86f8f87-d546-40b6-9ac5-3fa5169958dd               |
	| hp3par_api_url      | https://15.214.241.21:8080/api/v1                      |
	| hp3par_cpg          | 3par_FC                                                |
	| hp3par_password     | 3pardata                                               |
	| hp3par_username     | 3paradm                                                |
	| san_ip              | 15.214.241.21                                          |
	| san_login           | 3paradm_1                                              |
	| san_password        | 3pardata                                               |
	| volume_backend_name | 3par                                                   |
	| volume_driver       | cinder.volume.drivers.san.hp.hp_3par_fc.HP3PARFCDriver |
	+---------------------+--------------------------------------------------------+

### Preview the cinder configuration for the StoreServ CPG{#preview-storeserv-cpg}

To view the cinder configuration for the StoreServ CPG, enter the following command 

	sirius cpg-show <STORESERV_ID> --cpg-id <CPG_ID> --backend-name <VOLUME_BACKEND_NAME>

### View the configured StoreServ backend list{#view-storeserv-list}

To view the list of configured StoreServ backends, enter the following command

	sirius storeserv-backend-list

The sample output of the above command is given below:

	+------------------------------------------+----------+---------------------+
	| Backend ID                               | CPG Name | Volume Backend Name |
	+------------------------------------------+----------+---------------------+
	| CPG_b86f8f87-d546-40b6-9ac5-3fa5169958dd | 3par_FC  | 3par                |
	| CPG_db8b945c-b4f1-464d-9790-554d9b8c321e | FC_r1    | 3par                |
	+------------------------------------------+----------+---------------------+

##Reconfigure and update cloud](#reconfigure-update)

* [Generate StoreVirtual backend configuration JSON](#generate-storevirtual-config)

* [Generate StoreServ backend configuration JSON](#generate-storeserv-config)

* [Load the configuration and export required environment variables to prepare for updating cloud](#load-config-export)

* [Update Overcloud](#update-cloud) 

The backends configured in the Undercloud Sirius database will not be effective until the Overcloud Cinder configuration is not updated.

### Generate StoreVirtual backend configuration JSON {generate-storevirtual-config}
You can download the Cinder configuration relevant to HP StoreVirtual for your cloud once you create the backend.

To generate StoreVirtual backend configuration JSON, enter the following command

	sirius storevirtual-backend-list --format json

The sample output of the above command is given below:

	{
	    "DEFAULT": {
	        "enabled_backends": [
	            "cluster_8f45ef72-2a77-11e4-af1e-00cd664a1470",
	            "cluster_f2b30740-455a-11e4-a483-00b53da47ef7"
	        ]
	    },
	    "cluster_8f45ef72-2a77-11e4-af1e-00cd664a1470": {
	        "hplefthand_iscsi_chap_enabled": "true",
	        "hplefthand_password": "password",
	        "hplefthand_clustername": "skcluster01",
	        "volume_backend_name": "lhn",
	        "volume_driver": "cinder.volume.drivers.san.hp.hp_lefthand_iscsi.HPLeftHandISCSIDriver",
	        "hplefthand_api_url": "https://10.1.197.47:8081/lhos",
	        "hplefthand_debug": "false",
	        "hplefthand_username": "shausy"
	    },
	    "cluster_f2b30740-455a-11e4-a483-00b53da47ef7": {
	        "hplefthand_iscsi_chap_enabled": "true",
	        "hplefthand_password": "password"
	        "hplefthand_clustername": "skcluster02",
	        "volume_backend_name": "lhn",
	        "volume_driver": "cinder.volume.drivers.san.hp.hp_lefthand_iscsi.HPLeftHandISCSIDriver",
	        "hplefthand_api_url": "https://10.1.244.41:8081/lhos",
	        "hplefthand_debug": "false",
	        "hplefthand_username": "user"
	    }   
	}


### Generate StoreServ backend configuration JSON {generate-storeserv-config}

You can download the Cinder configuration relevant to HP StoreServ for your cloud once you create the backend.

To generate StoreServ backend configuration JSON, enter the following command

	sirius storeserv-backend-list --format json

The sample output of the above command is given below:

		{
		    "DEFAULT": {
		        "enabled_backends": [
		            "CPG_db8b945c-b4f1-464d-9790-554d9b8c321e",
		            "CPG_b86f8f87-d546-40b6-9ac5-3fa5169958dd"
		        ]
		    },
		    "CPG_db8b945c-b4f1-464d-9790-554d9b8c321e": {
		        "san_password": "3pardata",
		        "hp3par_username": "3paradm",
		        "volume_backend_name": "3par",
		        "san_login": "3paradm_1",
		        "hp3par_api_url": "https://15.214.241.21:8080/api/v1",
		        "volume_driver": "cinder.volume.drivers.san.hp.hp_3par_fc.HP3PARFCDriver",
		        "hp3par_password": "3pardata",
		        "hp3par_cpg": "FC_r1",
		        "san_ip": "15.214.241.21"
		    },
		    "CPG_b86f8f87-d546-40b6-9ac5-3fa5169958dd": {
		        "san_password": "3pardata",
		        "hp3par_username": "3paradm",
		        "volume_backend_name": "3par",
		        "san_login": "3paradm_1",
		        "hp3par_api_url": "https://15.214.241.21:8080/api/v1",
		        "volume_driver": "cinder.volume.drivers.san.hp.hp_3par_fc.HP3PARFCDriver",
		        "hp3par_password": "3pardata",
		        "hp3par_cpg": "3par_FC",
		        "san_ip": "15.214.241.21"
		    }
		}


### Update Overcloud configuration JSON {update-overcloud}

Update the `/root/overcloud-config.json` in the Seed node with the generated backend data. Add the StoreVirtual backend configuration as a JSON key-pair with key **'vsa'** and StoreServ backend configuration with key **'3par'** to the existing JSON.

A sample of the file is before and after the update is give below:

**Before the update:**

	{
	  "cloud_type": "KVM",
	  "compute_scale": 1,
	  "vsa_scale": 0,
	  "vsa_ao_scale": 0,
	  "so_swift_storage_scale": 0,
	  "so_swift_proxy_scale": 0,
	  "bridge_interface": "eth0",
	  "ntp": {
	    "overcloud_server": "",
	    "undercloud_server": ""
	  }
	}

**After the update:**

		{
		  "cloud_type": "KVM",
		  "compute_scale": 1,
		  "vsa_scale": 0,
		  "vsa_ao_scale": 0,
		  "so_swift_storage_scale": 2,
		  "so_swift_proxy_scale": 1,
		  "bridge_interface": "eth0",
		  "ntp": {
		    "overcloud_server": "",
		    "undercloud_server": ""
		  },
		  "vsa": {
		    "DEFAULT": {
		        "enabled_backends": [
		            "cluster_8f45ef72-2a77-11e4-af1e-00cd664a1470",
		            "cluster_f2b30740-455a-11e4-a483-00b53da47ef7"
		        ]
		    },
		    "cluster_8f45ef72-2a77-11e4-af1e-00cd664a1470": {
		        "hplefthand_iscsi_chap_enabled": "true",
		        "hplefthand_password": "password",
		        "hplefthand_clustername": "skcluster01",
		        "volume_backend_name": "lhn",
		        "volume_driver": "cinder.volume.drivers.san.hp.hp_lefthand_iscsi.HPLeftHandISCSIDriver",
		        "hplefthand_api_url": "https://10.1.197.47:8081/lhos",
		        "hplefthand_debug": "false",
		        "hplefthand_username": "shausy"
		    },
		    "cluster_f2b30740-455a-11e4-a483-00b53da47ef7": {
		        "hplefthand_iscsi_chap_enabled": "true",
		        "hplefthand_password": "password"
		        "hplefthand_clustername": "skcluster02",
		        "volume_backend_name": "lhn",
		        "volume_driver": "cinder.volume.drivers.san.hp.hp_lefthand_iscsi.HPLeftHandISCSIDriver",
		        "hplefthand_api_url": "https://10.1.244.41:8081/lhos",
		        "hplefthand_debug": "false",
		        "hplefthand_username": "user"
		    }   
		  }
		  "3par": {
		    "DEFAULT": {
		        "enabled_backends": [
		            "CPG_db8b945c-b4f1-464d-9790-554d9b8c321e",
		            "CPG_b86f8f87-d546-40b6-9ac5-3fa5169958dd"
		        ]
		    },
		    "CPG_db8b945c-b4f1-464d-9790-554d9b8c321e": {
		        "san_password": "3pardata",
		        "hp3par_username": "3paradm",
		        "volume_backend_name": "3par",
		        "san_login": "3paradm_1",
		        "hp3par_api_url": "https://15.214.241.21:8080/api/v1",
		        "volume_driver": "cinder.volume.drivers.san.hp.hp_3par_fc.HP3PARFCDriver",
		        "hp3par_password": "3pardata",
		        "hp3par_cpg": "FC_r1",
		        "san_ip": "15.214.241.21"
		    },
		    "CPG_b86f8f87-d546-40b6-9ac5-3fa5169958dd": {
		        "san_password": "3pardata",
		        "hp3par_username": "3paradm",
		        "volume_backend_name": "3par",
		        "san_login": "3paradm_1",
		        "hp3par_api_url": "https://15.214.241.21:8080/api/v1",
		        "volume_driver": "cinder.volume.drivers.san.hp.hp_3par_fc.HP3PARFCDriver",
		        "hp3par_password": "3pardata",
		        "hp3par_cpg": "3par_FC",
		        "san_ip": "15.214.241.21"
		    }
		  }
		}

### Load the configuration and export required environment variables to prepare for updating cloud{#load-config-export}
	
Enter the following command

    source tripleo/tripleo-incubator/scripts/hp_ced_load_config.sh /root/overcloud-config.json

###Update Overcloud{#update-overcloud}

Enter the following command to update the Overcloud

	bash -x tripleo/tripleo-incubator/scripts/hp_ced_installer.sh --update-overcloud

On completion of update, the Overcloud cinder will be configured with the StoreVirtual clusters and StoreServ CPG as backends

##More Information {#more-information}

For the complete list of Sirius CLI commands, refer to [Sirius Manual]( /helion/openstack/ga/sirius-cli/).


<a href="#top" style="padding:14px 0px 14px 0px; text-decoration: none;"> Return to Top &#8593; </a>

----
####OpenStack trademark attribution
*The OpenStack Word Mark and OpenStack Logo are either registered trademarks/service marks or trademarks/service marks of the OpenStack Foundation, in the United States and other countries and are used with the OpenStack Foundation's permission. We are not affiliated with, endorsed or sponsored by the OpenStack Foundation, or the OpenStack community.*