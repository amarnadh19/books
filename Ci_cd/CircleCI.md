# CircleCI

## CONCEPTS

### Projects

A CircleCI project shares the name of the associated code repository in your VCS (GitHub or Bitbucket).

On the Projects Dashboard, you can either:

- Set Up any project that you are the owner of in your VCS

- Follow any project in your organization to gain access to its pipelines and to subscribe to email notifications for the project’s status.

![](https://github.com/amarnadh19/books/blob/main/images/circle_learn_1.png?)


### Configuration

CircleCI believes in configuration as code. 

Your entire continuous integration and deployment process is orchestrated through a single file called ```config.yml```. 

The ```config.yml``` file is located in a folder called ```.circleci``` at the root of your project.

CircleCI uses the YAML syntax for config,

![](https://github.com/amarnadh19/books/blob/main/images/circle_learn_2.png?)

```config.yml``` is a powerful YAML file that defines the entire pipeline for your project.


The following terms, sorted in order of granularity and dependence, describe the components of most common CircleCI projects:

- **Pipeline:** Represents the entirety of your configuration. Available in CircleCI Cloud only.

- **Workflows:** Responsible for orchestrating multiple jobs.

- **Jobs:** Responsible for running a series of steps that perform commands.

- **Steps:** Run commands (such as installing dependencies or running tests) and shell scripts to do the work required for your project.

![](https://github.com/amarnadh19/books/blob/main/images/circle_learn_3.png?)


## Jenkins VS CircleCI

Jenkins is a self-contained and open source automation server that is customizable and requires setup and configuration at the organization level. Remember in the Jenkins CI chapters, we spent some time installing Jenkins in the Windows, Linux, and macOS operating systems. We also had the ability to configure Jenkins however we wanted. While this is great for software companies with dedicated teams in operations, DevOps, and so on, it is not as great for open source projects where often lone developers are setting up environments for their personal projects.

CircleCI was designed around the principle of open source development and for ease of use. CircleCI can be set up within minutes of creating a project in the GitHub and Bitbucket platforms. Although CircleCI is not as customizable as Jenkins CI in this respect, it has the distinct advantage of having a quick setup. CircleCI uses an in application configuration file that uses YAML syntax and can be used in the GitHub (https://github.com/) platform as well as in the Bitbucket (https://bitbucket.org/) platform, unlike Travis CI.


