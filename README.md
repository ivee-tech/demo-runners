# Runners

Demo repository for using self-hosted runners in a workflow.

:exclamation: Please note the pre-requisites below. To control cost, there are no self-hosted runners currently available ad-hoc and it is therefore required to set up a runner for the demo beforehand in e.g. AWS or Azure.

## Prerequisites
- Owner of an organization (needed to demo runner groups)
  - Runners can still be added on organization level on a free/pro/teams plan, and the `Default` group can be shared with select repositories
  - New runner groups can only be created on an Enterprise plan
- If an organization is not available, self-hosted runners can also be used on private repositories behind your user account. Runner groups cannot be demoed in this case.
- Access to a cloud platform (needed to create a runner machine)
- :bulb: In case of no access to a runner environment, then the demo can be spent showing the setup of runner groups, the docs, and taking Q&A.

## Usage 

### Creating a runner machine

1. A runner machine can be set up in any cloud (AWS, GCP, Azure, ...) or on-prem environment that has connectivity to GitHub, and has a supported OS. Note that connectivity requirements differ between GHES and GHEC, e.g. if the customer is on GHES and uses a proxy then additional steps might be required.
    - [GitHub Docs: Supported architectures and operating systems for self-hosted runners](https://docs.github.com/en/actions/hosting-your-own-runners/about-self-hosted-runners#supported-architectures-and-operating-systems-for-self-hosted-runners)
    - [GitHub Docs: Communication between self-hosted runners and GitHub](https://docs.github.com/en/actions/hosting-your-own-runners/about-self-hosted-runners#communication-between-self-hosted-runners-and-github)
    - :exclamation: Note that the docs for self-hosted runners can differ between GHES and GitHub.com, ensure you are viewing the correct version.
1. The steps needed to spin up a compute resource, e.g. a EC2 instance on AWS, is not covered in this description. Please check the documentation for the applicable platform for details.
1. Ensure that you are able to SSH into the instance after the setup is complete.

### Registering the runner in the organization

1. SSH into your runner machine
1. In your organization, go to **Settings** --> **Actions** --> **Runners** 
1. Add a new runner by following the instructions
    - :bulb: Make sure you select the correct OS and architecture
1. By the end of the setup, you should see the runner in **Idle** state
1. Show how additional labels can be added to the runner

### Add a runner group (if on GHEC or GHES)

1. In your organization, go to **Settings** --> **Actions** --> **Runner groups**
1. Add a new runner group
1. Transfer the runer to the new group
1. Show how runner groups can be scoped to select repositories

### Using the runner in a workflow

1. In any workflow (e.g. a simple starter workflow), specify your runner in the `runs-on` key using the labels
1. Trigger the workflow and ensure it runs without error

### Cleanup

1. N/A (all demos related to self-hosted runners must be done in separate organizations)
1. If a self-hosted runner has been created on a public cloud, terminate or stop the instance to avoid incurring unnecesary cost

