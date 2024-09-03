# jenkins-pr-auto-build-pipeline-using-plugin

Agenda:
-------
we need to trigger a jenkins build when developer raises PR for a branch

Why do we need a pull request workflow?
----------------------------------------

A pull request workflow is a process that helps developers collaborate on code changes in a safe and efficient way. It typically involves the following steps:

```
A developer creates a new branch and makes their changes.
They submit a pull request to merge their changes into the main branch.
Other developers review the pull request and provide feedback.
Once the pull request is approved, it is merged into the main branch.
A pull request workflow can help to improve the quality of code, reduce the risk of errors, and make it easier to track changes.
```

This workflow will automatically kick off a Jenkins pipeline when a developer opens a pull request. The pipeline will build and test the code changes, and then send a status update back to GitHub. If the pipeline passes, the pull request will be ready to be merged. If the pipeline fails, using branch protection rules, will prevent the pull request from merging. The developer must fix the issues and add new commits to the pull request, which will retrigger the same pipeline.

Benefits of using a pull request workflow with Jenkins

There are many benefits to using a pull request workflow with Jenkins, including:

```
Improved code quality: Jenkins can help to improve the quality of code by automatically building and testing code changes before they are merged into the main branch.
Reduced risk of errors: Jenkins can help to reduce the risk of errors by automatically running tests and checks on code changes.
Easier to track changes: Jenkins can make it easier to track changes by providing a centralized view of all pull requests and their status.
Increased collaboration: Jenkins can help to increase collaboration by allowing developers to review and comment on code changes before they are merged into the main branch.
```


GHPRB: GitHub Pull Request Builder 
==================================

![image](https://github.com/vijay2181/jenkins-pr-auto-build-pipeline/assets/66196388/79e93783-192e-49a9-8cfc-c3e0b7e86d11)


configure GHPRB:
----------------

![image](https://github.com/vijay2181/jenkins-pr-auto-build-pipeline/assets/66196388/973b6375-24b3-4586-9565-fc5e6f1d0a3a)

![image](https://github.com/vijay2181/jenkins-pr-auto-build-pipeline/assets/66196388/63c90c2e-3a7d-4f6e-8347-d6816dbea4d3)

- Apply and Save


Configure github webhook:
-------------------------

![image](https://github.com/vijay2181/jenkins-pr-auto-build-pipeline/assets/66196388/2ad57f62-f585-43c1-808e-eed4380b71e5)

![image](https://github.com/vijay2181/jenkins-pr-auto-build-pipeline/assets/66196388/70d61591-2a4f-41fb-814c-cbca7f835b35)

![image](https://github.com/vijay2181/jenkins-pr-auto-build-pipeline/assets/66196388/71e7b66f-0a39-453a-8b4f-0651f25056f2)

![image](https://github.com/vijay2181/jenkins-pr-auto-build-pipeline/assets/66196388/88230fa4-8668-4a1f-97c1-4cc5a2542257)

![image](https://github.com/vijay2181/jenkins-pr-auto-build-pipeline/assets/66196388/2ff07f42-c7dc-4800-ab8d-b0faf92b5109)

![image](https://github.com/vijay2181/jenkins-pr-auto-build-pipeline/assets/66196388/bd829972-ec8d-4c8d-b2b7-eb3b2e01c809)


webhook-pr-freestyle-job:
-------------------------

![image](https://github.com/vijay2181/jenkins-pr-auto-build-pipeline/assets/66196388/70e892fc-7116-4ddb-9472-3018960b6b64)

![image](https://github.com/vijay2181/jenkins-pr-auto-build-pipeline/assets/66196388/0c4e45b9-05d9-44a1-979f-05800198bc80)

- apply and save

  

























## FROM JENKINS PIPELINE
github posts json events with branch and pr details to jenkins pipeline. pipeline parses json of github api and triggers the branch and creates PR

```

Using Branch Name:
-----------------
If you're interested in building the branch itself that is associated with the pull request, then you'd use the branch name. This is useful if your workflow involves testing changes directly from the branch before merging.
You can retrieve the branch name from the environment variable or through Git commands (git rev-parse --abbrev-ref HEAD or git rev-parse --abbrev-ref <commit-ish> where <commit-ish> can be something like origin/branch_name).
The branch name approach is straightforward and suitable if your tests/builds are directly related to the branch content.

Using Pull Request Number:
--------------------------
If your workflow involves testing the changes that are proposed in the pull request before merging, you might want to use the pull request number.
Using the pull request number, you can fetch the pull request details and checkout the associated branch or specific commit.
This approach allows you to specifically target the changes proposed in the pull request and test them in isolation, which can be useful for larger teams or complex changes.
Both approaches have their merits, and the choice depends on your workflow and specific requirements. If you need to build based on the content of the pull request itself, using the pull request number to fetch the associated changes might be more appropriate. However, if your focus is on testing the branch as a whole, then using the branch name directly could suffice.

```
