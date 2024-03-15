# jenkins-pr-auto-build-pipeline

Agenda:
-------
we need to trigger a jenkins build when developer raises PR for a branch

```
github posts json events with branch and pr details to jenkins pipeline. pipeline parses json of github api and triggers the branch and creates PR

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
