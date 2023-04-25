## Best Practices of CI/CD for High Performance Computation with Tapis Workflows API

## Part 1: Welcome and Background
* [Welcome](./welcome/intro.md)

## Schedule

* x:xxAM - Introduction To Tapis
* x:xxAM - Introduction Tapis Workflows
* x:xxAM - Creating Systems, Apps, and Jobs (Jupyter Notebook)
* x:xxAM - Creating a Workflow using TapisUI (Image Build)
* x:xxAM - Break
* x:xxPM - Adding Tasks to a Workflow using TapisUI (Tapis Job Task)

## Workshop Introduction
Presenters: 
* Joe Stubbs (TACC)
* Anagha Jamthe (TACC)
* Nathan Freeman (TACC)
* Sean Cleveland
* Steve Black
* Mike Packard

The resources you will be using today are provided by funding from the National Science Foundation:

* [Jetstream](https://jetstream-cloud.org/) is a cloud service for research that provides on-demand, user-controled, Virtual Machines (VMs) - you can request and account after the workshop using these [instructions](https://iujetstream.atlassian.net/wiki/spaces/JWT/pages/76150553/Get+a+Jetstream+Trial+Access+account).  
* Stampede2 is the flagship supercomputer at The University of Texas at Austin's Texas Advanced Computing Center (TACC). A strategic national resource, Stampede2 provides high-performance computing capabilities to thousands of researchers across the U.S.  To gain access after the workshop you need to request a [startup allocation](https://portal.xsede.org/allocations/startup) with an XSEDE portal account, you can [Request and Account](https://portal.xsede.org/my-xsede?p_p_id=58&p_p_lifecycle=0&p_p_state=maximized&p_p_mode=view&_58_struts_action=%2Flogin%2Fcreate_account) and then [Submit an Allocation request](http://portal.xsede.org/submit-request) - If you have question please contact us via the TACC-Cloud slack channel.

You should have recieved a paper with a training account for Stampede2 and a slip of paper with a Jetstream Virtual Machine(VM) IP with username and password for that VM.  These are the credentials that we will use today and are only valid for todays workshop.

The Jetstream VMs all have the same configuration running Ubuntu 18 with all required software (Docker, Singularity, Tapis-CLI, Tapis PY and Jupyterhub).

## Tapis
* [Intro to Tapis](./block1/01-intro-to-tapis.md)
  * [Intro to Tapis Systems](./block1/02-systems.md)
  * [Intro to Tapis Apps](./block1/03-apps.md)
  * [Intro to Tapis Jobs](./block1/04-jobs.md)
  * [Link to Templates](./block1/templates)


## Workflows
* [Intro to Tapis Workflows](./block1/05-intro-to-workflows.md)
  * [Creating a Pipeline](./block1/06-creating-a-pipeline-and-task-with-tapisui.md)
