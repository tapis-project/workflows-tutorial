# Tapis Systems
---

A Tapis system represents a server or collection of servers exposed through a single host name or IP address. Each system is associated with a specific tenant. A system can be used for the following purposes:

* Running a job, including:

* Staging files to a system in preparation for running a job.

* Executing a job on a system.

* Archiving files and data on a remote system after job execution.

* Storing and retrieving files and data.

Each system is of a specific type (such as LINUX or S3) and owned by a specific user who has special privileges for the system. The system definition also includes the user that is used to access the system, referred to as effectiveUserId. This access user can be a specific user (such as a service account) or dynamically specified as ${apiUserId}. For the case of ${apiUserId}, the username is extracted from the identity associated with the request to the service.

```json
{
  "id":"tacc-sample-<userid>",
  "description":"My storage system",
  "host":"tapis-vm.tacc.utexas.edu",
  "systemType":"LINUX",
  "defaultAuthnMethod":"PKI_KEYS",
  "effectiveUserId":"${apiUserId}",
  "rootDir":"/",
  "canExec": false
}
```


Complete reference information is located here:
https://tapis.readthedocs.io/en/latest/technical/systems.html

# Managing systems
---

The Tapis API provides a way to access and manage the data storage and compute resources you already use (or maybe the systems you want to use), but first you have to tell Tapis where they are, how to login, and how to communicate with that system.  That is done by giving Tapis a short JSON description for each system. 

### Hands-on (We have already provisioned this execution system for this workshop for you. Skip for the workshop.)
