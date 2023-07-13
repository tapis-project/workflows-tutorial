# Tapis Workflows

### What is Tapis Workflows?

The Workflows Service is an API and workflow engine that enables users to automate and execute their research computing tasks in the Tapis Ecosystem.

Full documentation is available on ReadTheDocs: https://tapis.readthedocs.io/en/latest/technical/workflows.html

### Important Concepts

Tapis Workflows introduces some new concepts to the Tapis framework that are essential to understand before creating your first workflow.

* **Group**: A group is a collection of Tapis users that own or have access to workflow resources. In order to create your first workflow, you must first belong to, or create your own group.

* **Task**: Tasks are discrete units of work performed during the execution of a workflow. They can be represented as nodes on a directed acyclic graph (DAG), with the order of their execution determined by their dependencies, and where all tasks without dependencies are executed first. There are currently 6 different types of tasks that users can leverage to perform diffent types of work.

  * `image_build` - Builds Docker and Singularity images from recipe files and pushes them to repositories or stores the resultant image in some archive(specified in the pipeline definition)
  * `application` (formerly `container_run`) - Runs a container based on the provided image and tag.
  * `function` - runs user-defined code in a chosen language and runtime environment (only Python support at this time)
  * `request` - Sends requests using various protocols to resources external to the workflow (Only HTTP protocol and GET currently fully supported)
  * `tapis_job` - Submits an HPC Job via the Tapis Jobs Service
  * `tapis_actor` - Executes an Actor via the Abaco(Tapis Actors Service)

For this tutorial, we will be focusing on the `image_build` and `tapis_job` task types.

A detailed list of these task types and their capabilities can be found on the Tapis ReadTheDocs: https://tapis.readthedocs.io/en/latest/technical/workflows.html#task-types 

* **Pipeline**: A pipeline is a collection of tasks and a set of rules governing how those tasks are to be executed.

* **Archive**: An archive is the storage medium for the results created during a pipeline run. By default, the results produced by each task are deleted at the end of a pipeline run.

[Next-> Systems](./02-systems.md)

