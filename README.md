# Automate ACM Apps Ansible
_This repo is meant to practice automation deploying applications and policy on Red Hat Advanced Cluster Manager._

## Deploy Apps
```
ansible-playbook ansible/deploy-apps.yaml
```

output
```
➜  acm-automate-ansible git:(main) ansible-playbook ansible/deploy-apps.yaml

PLAY [deploy httpbin app] *********************************************************

TASK [deploy-apps : Apply HTTPBIN manifests ACM Hub] ******************************
[WARNING]: Platform darwin on host localhost is using the discovered Python
interpreter at /usr/bin/python, but future installation of another Python
interpreter could change the meaning of that path. See
https://docs.ansible.com/ansible-
core/2.11/reference_appendices/interpreter_discovery.html for more information.
changed: [localhost]

TASK [deploy-apps : Display HTTPBIN Output] ***************************************
ok: [localhost] => {
    "msg": {
        "ansible_facts": {
            "discovered_interpreter_python": "/usr/bin/python"
        },
        "changed": true,
        "failed": false,
        "result": {
            "results": [
                {
                    "changed": true,
                    "method": "create",
                    "result": {
                        "apiVersion": "apps.open-cluster-management.io/v1",
                        "kind": "Channel",
                        "metadata": {
                            "annotations": {
                                "open-cluster-management.io/user-group": "c3lzdGVtOmF1dGhlbnRpY2F0ZWQ6b2F1dGgsc3lzdGVtOmF1dGhlbnRpY2F0ZWQ=",
                                "open-cluster-management.io/user-identity": "YWRtaW4="
                            },
                            "creationTimestamp": "2021-10-20T17:05:10Z",
                            "generation": 1,
                            "managedFields": [
                                {
                                    "apiVersion": "apps.open-cluster-management.io/v1",
                                    "fieldsType": "FieldsV1",
                                    "fieldsV1": {
                                        "f:spec": {
                                            ".": {},
                                            "f:pathname": {},
                                            "f:type": {}
                                        }
                                    },
                                    "manager": "OpenAPI-Generator",
                                    "operation": "Update",
                                    "time": "2021-10-20T17:05:10Z"
                                }
                            ],
                            "name": "httpbin-app-latest",
                            "namespace": "default",
                            "resourceVersion": "439035",
                            "uid": "52912a82-000f-4ff1-9798-1283000de172"
                        },
                        "spec": {
                            "pathname": "https://github.com/cmwylie19/bookinfo-acm.git",
                            "type": "GitHub"
                        }
                    }
                },
                {
                    "changed": true,
                    "method": "create",
                    "result": {
                        "apiVersion": "app.k8s.io/v1beta1",
                        "kind": "Application",
                        "metadata": {
                            "annotations": {
                                "open-cluster-management.io/user-group": "c3lzdGVtOmF1dGhlbnRpY2F0ZWQ6b2F1dGgsc3lzdGVtOmF1dGhlbnRpY2F0ZWQ=",
                                "open-cluster-management.io/user-identity": "YWRtaW4="
                            },
                            "creationTimestamp": "2021-10-20T17:05:10Z",
                            "generation": 1,
                            "managedFields": [
                                {
                                    "apiVersion": "app.k8s.io/v1beta1",
                                    "fieldsType": "FieldsV1",
                                    "fieldsV1": {
                                        "f:spec": {
                                            ".": {},
                                            "f:componentKinds": {},
                                            "f:descriptor": {},
                                            "f:selector": {
                                                ".": {},
                                                "f:matchExpressions": {}
                                            }
                                        }
                                    },
                                    "manager": "OpenAPI-Generator",
                                    "operation": "Update",
                                    "time": "2021-10-20T17:05:10Z"
                                }
                            ],
                            "name": "httpbin-app",
                            "namespace": "default",
                            "resourceVersion": "439042",
                            "uid": "28c5aae9-dc84-4694-959f-30fbba8daaf5"
                        },
                        "spec": {
                            "componentKinds": [
                                {
                                    "group": "apps.open-cluster-management.io",
                                    "kind": "Subscription"
                                }
                            ],
                            "descriptor": {},
                            "selector": {
                                "matchExpressions": [
                                    {
                                        "key": "app",
                                        "operator": "In",
                                        "values": [
                                            "httpbin-app"
                                        ]
                                    }
                                ]
                            }
                        }
                    }
                },
                {
                    "changed": true,
                    "method": "create",
                    "result": {
                        "apiVersion": "apps.open-cluster-management.io/v1",
                        "kind": "Subscription",
                        "metadata": {
                            "annotations": {
                                "apps.open-cluster-management.io/git-branch": "main",
                                "apps.open-cluster-management.io/github-path": "resources/httpbin",
                                "open-cluster-management.io/user-group": "c3lzdGVtOmF1dGhlbnRpY2F0ZWQ6b2F1dGgsc3lzdGVtOmF1dGhlbnRpY2F0ZWQ=",
                                "open-cluster-management.io/user-identity": "YWRtaW4="
                            },
                            "creationTimestamp": "2021-10-20T17:05:10Z",
                            "generation": 1,
                            "labels": {
                                "app": "httpbin-app"
                            },
                            "managedFields": [
                                {
                                    "apiVersion": "apps.open-cluster-management.io/v1",
                                    "fieldsType": "FieldsV1",
                                    "fieldsV1": {
                                        "f:metadata": {
                                            "f:annotations": {
                                                ".": {},
                                                "f:apps.open-cluster-management.io/git-branch": {},
                                                "f:apps.open-cluster-management.io/github-path": {}
                                            },
                                            "f:labels": {
                                                ".": {},
                                                "f:app": {}
                                            }
                                        },
                                        "f:spec": {
                                            ".": {},
                                            "f:channel": {},
                                            "f:placement": {
                                                ".": {},
                                                "f:placementRef": {
                                                    ".": {},
                                                    "f:kind": {},
                                                    "f:name": {}
                                                }
                                            }
                                        }
                                    },
                                    "manager": "OpenAPI-Generator",
                                    "operation": "Update",
                                    "time": "2021-10-20T17:05:10Z"
                                }
                            ],
                            "name": "httpbin-app",
                            "namespace": "default",
                            "resourceVersion": "439053",
                            "uid": "e1ae1e4d-faed-44b9-9c09-c511ecb8fdca"
                        },
                        "spec": {
                            "channel": "default/httpbin-app-latest",
                            "placement": {
                                "placementRef": {
                                    "kind": "PlacementRule",
                                    "name": "dev-clusters"
                                }
                            }
                        }
                    }
                }
            ]
        },
        "warnings": [
            "Platform darwin on host localhost is using the discovered Python interpreter at /usr/bin/python, but future installation of another Python interpreter could change the meaning of that path. See https://docs.ansible.com/ansible-core/2.11/reference_appendices/interpreter_discovery.html for more information."
        ]
    }
}

TASK [deploy-apps : Apply Placement manifests ACM Hub] ****************************
changed: [localhost]

TASK [deploy-apps : Display Placement Output] *************************************
ok: [localhost] => {
    "msg": {
        "changed": true,
        "failed": false,
        "method": "create",
        "result": {
            "apiVersion": "apps.open-cluster-management.io/v1",
            "kind": "PlacementRule",
            "metadata": {
                "annotations": {
                    "open-cluster-management.io/user-group": "c3lzdGVtOmF1dGhlbnRpY2F0ZWQ6b2F1dGgsc3lzdGVtOmF1dGhlbnRpY2F0ZWQ=",
                    "open-cluster-management.io/user-identity": "YWRtaW4="
                },
                "creationTimestamp": "2021-10-20T17:05:12Z",
                "generation": 1,
                "managedFields": [
                    {
                        "apiVersion": "apps.open-cluster-management.io/v1",
                        "fieldsType": "FieldsV1",
                        "fieldsV1": {
                            "f:spec": {
                                ".": {},
                                "f:clusterConditions": {},
                                "f:clusterSelector": {
                                    ".": {},
                                    "f:matchLabels": {
                                        ".": {},
                                        "f:env": {}
                                    }
                                }
                            }
                        },
                        "manager": "OpenAPI-Generator",
                        "operation": "Update",
                        "time": "2021-10-20T17:05:12Z"
                    }
                ],
                "name": "dev-clusters",
                "namespace": "default",
                "resourceVersion": "439148",
                "uid": "c85c0fb1-7445-4bab-8f04-260b857ef7cf"
            },
            "spec": {
                "clusterConditions": [
                    {
                        "status": "True",
                        "type": "ManagedClusterConditionAvailable"
                    }
                ],
                "clusterSelector": {
                    "matchLabels": {
                        "env": "dev"
                    }
                }
            }
        }
    }
}

PLAY RECAP ************************************************************************
localhost                  : ok=4    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0 
```

## Destroy Apps
```
ansible-playbook ansible/destroy-apps.yaml
```

output
```
➜  acm-automate-ansible git:(main) ansible-playbook ansible/destroy-apps.yaml 

PLAY [deploy httpbin app] *********************************************************

TASK [destroy-apps : Destroy HTTPBIN manifests ACM Hub] ***************************
[WARNING]: Platform darwin on host localhost is using the discovered Python
interpreter at /usr/bin/python, but future installation of another Python
interpreter could change the meaning of that path. See
https://docs.ansible.com/ansible-
core/2.11/reference_appendices/interpreter_discovery.html for more information.
changed: [localhost]

TASK [destroy-apps : HTTPBIN Output] **********************************************
ok: [localhost] => {
    "msg": {
        "ansible_facts": {
            "discovered_interpreter_python": "/usr/bin/python"
        },
        "changed": true,
        "failed": false,
        "result": {
            "results": [
                {
                    "changed": true,
                    "method": "delete",
                    "result": {
                        "apiVersion": "v1",
                        "details": {
                            "group": "apps.open-cluster-management.io",
                            "kind": "channels",
                            "name": "httpbin-app-latest",
                            "uid": "2c240d4b-455b-480c-9c21-32bbc0ba38e0"
                        },
                        "kind": "Status",
                        "metadata": {},
                        "status": "Success"
                    }
                },
                {
                    "changed": true,
                    "method": "delete",
                    "result": {
                        "apiVersion": "v1",
                        "details": {
                            "group": "app.k8s.io",
                            "kind": "applications",
                            "name": "httpbin-app",
                            "uid": "c7c5c02b-65a2-4fab-aad3-e5ec343f2936"
                        },
                        "kind": "Status",
                        "metadata": {},
                        "status": "Success"
                    }
                },
                {
                    "changed": true,
                    "method": "delete",
                    "result": {
                        "apiVersion": "v1",
                        "details": {
                            "group": "apps.open-cluster-management.io",
                            "kind": "subscriptions",
                            "name": "httpbin-app",
                            "uid": "e361413e-3445-4b38-b2c1-38605716efea"
                        },
                        "kind": "Status",
                        "metadata": {},
                        "status": "Success"
                    }
                }
            ]
        },
        "warnings": [
            "Platform darwin on host localhost is using the discovered Python interpreter at /usr/bin/python, but future installation of another Python interpreter could change the meaning of that path. See https://docs.ansible.com/ansible-core/2.11/reference_appendices/interpreter_discovery.html for more information."
        ]
    }
}

TASK [destroy-apps : Destroy Placement manifests ACM Hub] *************************
changed: [localhost]

TASK [destroy-apps : Placement Output] ********************************************
ok: [localhost] => {
    "msg": {
        "changed": true,
        "failed": false,
        "method": "delete",
        "result": {
            "apiVersion": "v1",
            "details": {
                "group": "apps.open-cluster-management.io",
                "kind": "placementrules",
                "name": "dev-clusters",
                "uid": "527ddf75-ae7a-4560-8cad-a19b804a481d"
            },
            "kind": "Status",
            "metadata": {},
            "status": "Success"
        }
    }
}

PLAY RECAP ************************************************************************
localhost                  : ok=4    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
```

