---
layout: default
title: "HP Helion OpenStack: Sample LDAP Server Connection Settings File"
permalink: /helion/openstack/install/connections-json/
product: commercial.ga
product-version1: HP Helion OpenStack 1.1
role1: Storage Administrator
role2: Storage Architect
authors: Michael B, 

---
<!--UNDER REVISION-->


<script>

function PageRefresh {
onLoad="window.refresh"
}

PageRefresh();

</script>


<p style="font-size: small;"> <a href="/helion/openstack/services/identity/integrate-ldap/"> &#9650; Integrate the Identity Service (Keystone) with LDAP/AD</a></p> 

<!-- Based on https://wiki.hpcloud.net/display/csbu/Integrating+Keystone+with+LDAP+in+Helion+1.1 -->

# HP Helion OpenStack&reg;: Sample LDAP Server Connection Settings JSON File

The following is a sample LDAP Server connection settings JSON file with typical values entered. This example is to demonstrate how to complete the JSON values and is not intended for users to copy the values into their cloud.

See [Integrate the Identity Service (Keystone) with LDAP/AD](/helion/openstack/services/identity/integrate-ldap/) for information on using and modifying this file.

	{
	    "keystone": {
	        "domains": {
	            "dept1": {
	                "description": "Dedicated domain for dept1 users",
	                "config": [
	                    {
	                        "section": "identity",
	                        "values": [
	                            {
	                                "option": "driver",
	                                "value": "keystone.identity.backends.ldap.Identity"
	                            }
	                        ]
	                    },
	                    {
	                        "section": "assignment",
	                        "values": [
	                            {
	                                "option": "driver",
	                                "value": "keystone.assignment.backends.sql.Assignment"
	                            }
	                        ]
	                    },
	                    {
	                        "section": "ldap",
	                        "values": [
	                            {
	                                "option": "url",
	                                "value": "ldap://openldap.myorg.com"
	                            },
	                            {
	                                "option": "suffix",
	                                "value": "dc=dept1,dc=myorg,dc=com"
	                            },
	                            {
	                                "option": "query_scope",
	                                "value": "sub"
	                            },
	                            {
	                                "option": "user_tree_dn",
	                                "value": "ou=users,dc=dept1,dc=myorg,dc=com"
	                            },
	                            {
	                                "option": "user_objectclass",
	                                "value": "posixAccount"
	                            },
	                            {
	                                "option": "user_id_attribute",
	                                "value": "uid"
	                            },
	                            {
	                                "option": "user_name_attribute",
	                                "value": "cn"
	                            },
	                            {
	                                "option": "user_enabled_default",
	                                "value": "False"
	                            },
	                            {
	                                "option": "user_allow_create",
	                                "value": "False"
	                            },
	                            {
	                                "option": "user_allow_update",
	                                "value": "False"
	                            },
	                            {
	                                "option": "user_allow_delete",
	                                "value": "False"
	                            },
	                            {
	                                "option": "tenant_allow_create",
	                                "value": "False"
	                            },
	                            {
	                                "option": "tenant_allow_update",
	                                "value": "False"
	                            },
	                            {
	                                "option": "tenant_allow_delete",
	                                "value": "False"
	                            },
	                            {
	                                "option": "role_allow_create",
	                                "value": "False"
	                            },
	                            {
	                                "option": "role_allow_update",
	                                "value": "False"
	                            },
	                            {
	                                "option": "role_allow_delete",
	                                "value": "False"
	                            },
	                            {
	                                "option": "group_tree_dn",
	                                "value": "ou=groups,dc=dept1,dc=myorg,dc=com"
	                            },
	                            {
	                                "option": "group_objectclass",
	                                "value": "posixGroup"
	                            },
	                            {
	                                "option": "group_id_attribute",
	                                "value": "gid"
	                            },
	                            {
	                                "option": "group_name_attribute",
	                                "value": "cn"
	                            },
	                            {
	                                "option": "group_allow_create",
	                                "value": "False"
	                            },
	                            {
	                                "option": "group_allow_update",
	                                "value": "False"
	                            },
	                            {
	                                "option": "group_allow_delete",
	                                "value": "False"
	                            },
	                            {
	                                "option": "use_tls",
	                                "value": "True"
	                            },
	                            {
	                                "option": "tls_cacertfile",
	                                "value": "/mnt/state/etc/keystone/ssl/certs/ca.pem"
	                            },
	                            {
	                                "option": "tls_req_cert",
	                                "value": "demand"
	                            }
	                        ]
	                    }
	                ]
	            },
	            "dept2": {
	                "description": "Dedicated domain for dept2 users",
	                "config": [
	                    {
	                        "section": "identity",
	                        "values": [
	                            {
	                                "option": "driver",
	                                "value": "keystone.identity.backends.ldap.Identity"
	                            }
	                        ]
	                    },
	                    {
	                        "section": "assignment",
	                        "values": [
	                            {
	                                "option": "driver",
	                                "value": "keystone.assignment.backends.sql.Assignment"
	                            }
	                        ]
	                    },
	                    {
	                        "section": "ldap",
	                        "values": [
	                            {
	                                "option": "url",
	                                "value": "ldap://adldap.myorg.com"
	                            },
	                            {
	                                "option": "suffix",
	                                "value": "dc=dept2,dc=myorg,dc=com"
	                            },
	                            {
	                                "option": "user_tree_dn",
	                                "value": "cn=Users,dc=dept2,dc=myorg,dc=com"
	                            },
	                            {
	                                "option": "user",
	                                "value": "cn=ldap_admin,cn=Users,dc=dept2,dc=myorg,dc=com"
	                            },
	                            {
	                                "option": "password",
	                                "value": "ldap_admin_password"
	                            },
	                            {
	                                "option": "user_objectclass",
	                                "value": "user"
	                            },
	                            {
	                                "option": "user_id_attribute",
	                                "value": "cn"
	                            },
	                            {
	                                "option": "user_name_attribute",
	                                "value": "cn"
	                            },
	                            {
	                                "option": "user_allow_create",
	                                "value": "False"
	                            },
	                            {
	                                "option": "user_allow_update",
	                                "value": "False"
	                            },
	                            {
	                                "option": "user_allow_delete",
	                                "value": "False"
	                            },
	                            {
	                                "option": "group_tree_dn",
	                                "value": "cn=Groups,dc=dept2,dc=myorg,dc=com"
	                            },
	                            {
	                                "option": "group_objectclass",
	                                "value": "posixGroup"
	                            },
	                            {
	                                "option": "group_id_attribute",
	                                "value": "gid"
	                            },
	                            {
	                                "option": "group_name_attribute",
	                                "value": "cn"
	                            },
	                            {
	                                "option": "group_allow_create",
	                                "value": "False"
	                            },
	                            {
	                                "option": "group_allow_delete",
	                                "value": "False"
	                            },
	                            {
	                                "option": "group_allow_update",
	                                "value": "False"
	                            },
	                            {
	                                "option": "use_tls",
	                                "value": "True"
	                            },
	                            {
	                                "option": "tls_req_cert",
	                                "value": "demand"
	                            },
	                            {
	                                "option": "tls_cacertfile",
	                                "value": "/mnt/state/etc/keystone/ssl/certs/ca.pem"
	                            },
	                            {
	                                "option": "use_pool",
	                                "value": "True"
	                            }
	                        ]
	                    }
	                ]
	            }
	        }
	    }
	}


<a href="#top" style="padding:14px 0px 14px 0px; text-decoration: none;"> Return to Top &#8593; </a>