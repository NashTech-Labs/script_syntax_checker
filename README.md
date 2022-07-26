# Script Checker for GitLab Pipelines

## Prerequisites:
- A GitLab account
- Python and shell scripts to check on

## Explanation of gitlab-ci.yml
- GitLab has its own runners and they can be used to run our pipelines or we can define them also according to our needs like we want the runner to access some artifactory for pushing and pulling the builds from. 
The deafults section contains the runner which is going to be used to run the pipeline. We can remove that section too and GitLab will use its own self-hosted runner.

- Next we have Stages section and under that we declare the stages to be used in the pipeline. And here we have defined the test stage in which the testing of scripts will happen. Here the order of declaration doesn't matter.

- Next we've to define the stage. Here the branch has to be mentioned from which the code will be taken for testing. After changes in the directories will be defined as in which directory changes has to checked for testing.
After that we'll update the gitlab runner and and install the tools in it required for checking the scripts. 

## How to use this template?
- Firstly, if you are using your own custom runner then you have to specify the runner name under the tags section by replacing `<RUNNER_NAME(IF ANY)>` with your runner name. Otherwise you can remove the defaults section and GitLab will run the pipeline using it's own self-hosted runner.

- Then you have to specify the branch name under the refs section by replacing `<BRANCH_NAME>` with your branch name on which you would push your scripts to get a check on.

- After that, you just have to copy you scripts into the specific directories that are present in the root directory.

- In the last when you are done copying the scripts, you just have to commit the changes and make a push and the pipeline will get triggered. If the scripts have some syntax errors, the pipeline will show the error logs and you can find that in the CI/CD >> Pipelines section.