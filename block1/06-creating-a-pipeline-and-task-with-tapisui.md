# Creating a Pipeline

For this section, we will be using TapisUI to create our workflow resources.
This UI can be found at the following URL: https://training.tapis.io/tapis-ui/#/

---

### Step 1: Log In and Explore

Click the `Proceed to login` link on the home page, fill out the login form with your TACC credentials(username and password), and click `Log In`

![Login](./images/01-login.png)

In the left sidebar of the Dashboard page, you will see tabs to pages where you will find listings of the Tapis resources your created in the previous steps. Take some time to expore the Systems and Apps section by clicking on their respective tabs.

![Workflows Nav](./images/02-navbar.png)


### Step 2: Create a Group

## Groups Overview

In order to create your first `Pipeline`, you must first belong to a `Group`

`Groups` are collections of users that own workflow resources. The user creating the group will be added to the user list by default with `owner` and has total control over all resources owned by it. 

Additional users can be added to the group with either basic or administrative permissions. Basic users can create their own pipelines, tasks, archives, etc, and run the other pipelines in the group. Administrators can delete pipelines owned by other users but cannot delete the group.

## How to Create a Group

Click the `Workflows` tab to navigate to the Workflows page. This is the dashboard where you can access all of your workflow resources. On this page, click the add group button in the toolbar below the workflows navbar.

![Workflows Nav](./images/03-click-create-group.png)

---

A modal will pop up with the form to create your group. Give the group a unique id and click the `Create Group` button at the bottom. Once you have successfully created it, exit out of the modal by click the `X` at the top.

NOTE: For this demonstration, we do not need to add any additional users to the group.

![Workflows Nav](./images/04-create-group.png)

Now that you have a group, it's time to create a `Pipeline`.

---

### Step 3: Create a Pipeline

`Pipelines` are collections of tasks and a set of rules that govern how those tasks are to be executed.

To create your first pipeline, click the `Pipelines` button at the top of the workflows dashboard. This will take you to a page with a listing of all the groups you belong to.

![Workflows Nav](./images/05-navigate-to-pipeline.png)

Select the group that you just created. This will display a list of all the pipelines that belong to this group(none as of yet) as well as a button to create a pipeline. Click the `+ New Pipeline` button.


![Workflows Nav](./images/06-click-create-pipeline.png)

---

![Workflows Nav](./images/07-create-pipeline.png)

---

### Step 4: Add an 'image_build' Task to the Pipeline

![Workflows Nav](./images/08-edit-pipeline.png)

---

![Workflows Nav](./images/09-click-add-task.png)

---

![Workflows Nav](./images/10-select-image-build.png)

---

![Workflows Nav](./images/11-select-builder.png)

---

![Workflows Nav](./images/12-github-context.png)

---

![Workflows Nav](./images/13-context-visibility.png)

---

![Workflows Nav](./images/14-destination.png)



