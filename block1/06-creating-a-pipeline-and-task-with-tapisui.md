# Creating a Pipeline

For this section, we will be using TapisUI to create our workflow resources.\
TapisUI can be found at the following URL: [https://training.tapis.io/tapis-ui/#/](https://training.tapis.io/tapis-ui/#/)

---

## Step 1: Log In and Explore

Click the `Proceed to login` link on the home page, fill out the login form with your TACC credentials(username and password), and click `Log In`

<image alt="Login" src="../images/01-login.png" style="width: 400px">

In the left sidebar of the Dashboard page, you will see tabs to pages where you will find listings of the Tapis resources your created in the previous steps. Take some time to expore the Systems and Apps section by clicking on their respective tabs.

<image alt="tutorial-image" src="../images/02-navbar.png" style="width: 400px">


## Step 2: Create a Group

In order to create your first `Pipeline`, you must first belong to a `Group`

`Groups` are collections of users that own workflow resources. The user creating the group will be added to the user list by default with `owner` permissions and has total control over all resources owned by it. 

Additional users can be added to the group with either basic or administrative permissions. Basic users can create their own pipelines, tasks, archives, etc, and run the other pipelines in the group. Administrators can delete pipelines owned by other users but cannot delete the group.

### How to Create a Group

Click the `Workflows` tab to navigate to the Workflows page. This is the dashboard where you can access all of your workflow resources. On this page, click the add group button in the toolbar below the workflows navbar.

<image alt="tutorial-image" src="../images/03-click-create-group.png" style="width: 400px">

---

A modal will pop up with the form to create your group. Give the group a unique id and click the `Create Group` button at the bottom. Once you have successfully created it, exit out of the modal by click the `X` at the top.

NOTE: For this demonstration, we do not need to add any additional users to the group.

<image alt="tutorial-image" src="../images/04-create-group.png" style="width: 400px">

Now that you have a group, it's time to create a `Pipeline`.

---

## Step 3: Create a Pipeline

`Pipelines` are collections of tasks and a set of rules that govern how those tasks are to be executed.

To create your first pipeline, click the `Pipelines` button at the top of the workflows dashboard. This will take you to a page with a listing of all the groups you belong to.

<image alt="tutorial-image" src="../images/05-navigate-to-pipeline.png" style="width: 400px">

Select the group that you just created. This will display a list of all the pipelines that belong to this group(none as of yet) as well as a button to create a pipeline. Click the `+ New Pipeline` button.


<image alt="tutorial-image" src="../images/06-click-create-pipeline.png" style="width: 400px">

Fill out the form. Once complete, click the `Create Pipeline` button at the bottom right. Once created, exit out of the modal back to the pipelines page.

<image alt="tutorial-image" src="../images/07-create-pipeline.png" style="width: 400px">

You should now see the pipeline you created. It's now time to create the first `Task` for the pipeline.

---

## Step 4: Add an 'image_build' Task to the Pipeline

The next step is to use an `image_build` task to pull the Material Point Method application code from a Github, build an image from the Dockerfile, and push it to your personal Dockerhub repository.

NOTE: This next step will require that you have an account on [dockerhub](https://https://hub.docker.com/). You will also need to create an `access token` with push permissions.

### How to create your first task

From the `Pipelines` page, click the edit button on the pipeline that you just created. This will take you to the details page for that pipeline.

<image alt="tutorial-image" src="../images/08-edit-pipeline.png" style="width: 400px">

On this page, click the `+ New Task` button, this will generate a modal with a dropdown containing task types

<image alt="tutorial-image" src="../images/09-click-add-task.png" style="width: 400px">

Choose the `image_build` option and click the `Next >` button

<image alt="tutorial-image" src="../images/10-select-image-build.png" style="width: 400px">

Fill out the `task id` and `description` fields. Then for the builder dropdown, select the `kaniko` option. Kaniko is a containerized image builder that allows you to create OCI compliant images from within a container without Docker.

<image alt="tutorial-image" src="../images/11-select-builder.png" style="width: 400px">

The next step is to set up the image build `context` aka the source of the image build. Once finished, the context will contain all of the data needed to access and pull the MPM source from Github.

First, select `github` option from the `source` dropdown. This will generate some new fields. Fill them out with the exact values below:
* **url** `joestubbs/mpm-container`
* **branch** `master`
* **build file path** `Dockerfile`
* **sub path** LEAVE EMPTY!

<image alt="tutorial-image" src="../images/12-github-context.png" style="width: 400px">

In the `Visibility and Credentials` section of the context, select the `public` option

<image alt="tutorial-image" src="../images/13-context-visibility.png" style="width: 400px">

Next, we will need to create the `Destination` of the image. This will be the Dockerhub repository that you set up beforehand.

NOTE: This step requires that you have a Dockerhub repository and have created an access token with write/push permissions that will allow the Workflow Engine to push the image on your behalf.

Select the `dockerhub` option from the destination dropdown.\

In the **url** field, put the url to your repository and image. It will follow the format `<repository>/<image_name>`.\

In the **image_tag** field, put any tag you want. `dev` or `latest` would be sufficient for this tutorial.\

In the `Credential Source` section, select the `Provide credentials` radio button. This will generate 2 new fields: **username** and **access token**. For **username**, put your Dockerhub username, and for **access_token** put the Dockerhub access token.

Once all fields are populated, click the `Create Task` button at the bottom right and close the modal once the task is successfully created.

<image alt="tutorial-image" src="../images/14-destination.png" style="width: 400px">

Now that the first task has been created, we can do an initial run of the pipeline. Click the `Run Pipeline` button in the toolbar on the `Pipeline` page. This will trigger a modal with which you can trigger your workflow

<image alt="tutorial-image" src="../images/15-task-created.png" style="width: 400px">

Run the pipeline by clicking the `Run Pipeline` button at the bottom of the modal. Once the button is pressed, the workflow definition is submitted to the Workflow Engine and the image build will start.

<image alt="tutorial-image" src="../images/16-run-pipeline.png" style="width: 400px">

You can view the status of the pipeline run by navigating to the `Pipeline Run` page for this pipeline. Click the `view` link in the `runs` column of the pipeline details table.

<image alt="tutorial-image" src="../images/17-view-runs.png" style="width: 400px">

Note that the pipeline run status is active. That mean the pipeline has successfully been submitted and the workflow engine is being processed.

To view the task executions for a particular pipeline run, click the `view` link on the `executions` column of the pipeline run details table.

<image alt="tutorial-image" src="../images/18-view-task-executions.png" style="width: 400px">

You should see that your image build task is currently active. Once the build completes, we can move on to the next step of adding 2 tasks to that pipeline that will run `mpm` and benchmarks using the new image to ensure it was built correctly.

Click the name of the pipeline in the breadcrumbs located at the top of the page to navigate back to the pipeline details page.

<image alt="tutorial-image" src="../images/19-task-executions.png" style="width: 400px">

The first of these tasks will be a Tapis Job executed via the Workflow Engine in which we simply run the `mpm` command using our new image. This task will ensure that MPM was correctly compiled.

Navigate back to the pipeline page and click the `+ New Task` button.

<image alt="tutorial-image" src="../images/20-new-task.png" style="width: 400px">

Select a the `tapis_job` option from the task type drop down and click the `Next >` button.

<image alt="tutorial-image" src="../images/21-select-tapis-job.png" style="width: 400px">

Add an `id` and `description`

<image alt="tutorial-image" src="../images/22-fields.png" style="width: 400px">

Now that we have an existing task in the pipleine, we can use the `Dependencies` section to create relationships between our tasks. Expand the `Dependencies` section by clicking the expand button at the top right of the section, click the `+ Add dependency` button, and choose the id of the first `image_build` task that was created.

<image alt="tutorial-image" src="../images/23-add-deps.png" style="width: 400px">

Copy and paste the Tapis Job JSON definition from the JSON file titled `job-mpm-run.json` from link below into the `tapis job def` JSON editor.

[https://github.com/tapis-project/workflows-tutorial/tree/main/block1/](https://github.com/tapis-project/workflows-tutorial/tree/main/block1/)

Be sure to replace the `execSystemId` property with the Tapis System id provided in the beginning of the tutorial.

Once the definition is complete, click the `Create Task` button.

<image alt="tutorial-image" src="../images/24-job-def-and-create.png" style="width: 400px">

Navigate back to the pipeline page and add another `tapis_job` task for the uniaxial traction benchmark.

<image alt="tutorial-image" src="../images/25-fields.png" style="width: 400px">

When adding dependencies to this task, choose the first image build task we created. When this pipeline runs, The image build will run first, and once that completes successfully, both Tapis Job tasks will run concurrently. 

<image alt="tutorial-image" src="../images/26-deps.png" style="width: 400px">

Copy and paste the Tapis Job JSON definition from the JSON file titled `job-mpm-uniaxial-traction.json` from link below into the `tapis job def` JSON editor.

[https://github.com/tapis-project/workflows-tutorial/tree/main/block1/](https://github.com/tapis-project/workflows-tutorial/tree/main/block1/)

Be sure to replace the `execSystemId` property with the Tapis System id provided in the beginning of the tutorial.

Once the definition is complete, click the `Create Task` button.

<image alt="tutorial-image" src="../images/27-job-def.png" style="width: 400px">

Now that all of our tasks have been created, we can submit the complete pipeline for processing.

<image alt="tutorial-image" src="../images/28-view-tasks.png" style="width: 400px">

Click the `Run Pipeline` button to trigger the modal, then submit the pipeline.

<image alt="tutorial-image" src="../images/29-final-run.png" style="width: 400px">



