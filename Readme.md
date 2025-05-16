# About GitHub-hosted runners

GitHub offers hosted virtual machinis to run workflows. The virtual machine contains an environment of tools, packages, and settings available for GitHub Actions to use.

## In this article

- [Overview of GitHub-hosted runners](#overview-of-github-hosted-runners)  
- [Using a GitHub-hosted runner](#using-a-github-hosted-runner)  
- [Viewing available runners for a repository](#viewing-available-runners-for-a-repository)  
- [Supported runners and hardware resources](#supported-runners-and-hardware-resources)  
- [Runner Images](#runner-images)  
- [Cloud hosts used by GitHub-hosted runners](#cloud-hosts-used-by-github-hosted-runners)  
- [Workflow continuity](#workflow-continuity)  
- [Administrative privileges](#administrative-privileges)  
- [IP addresses](#ip-addresses)  
- [Communication requirements for GitHub-hosted runners](#communication-requirements-for-github-hosted-runners)  
- [The etc/hosts file](#the-etchosts-file)  
- [File systems](#file-systems)  
- [Further reading](#further-reading)

---

## Overview of GitHub-hosted runers

Runners are the machines that execute jobs in a GitHub Actions workflow. For example, a runner can clone your repository locally, install testing software, and then run commands that evaluate your code.

GitHub provides runners that you can use to run your jobs, or you can host your own runners. Each GitHub-hosted runner is a new virtual machine (VM) hosted by GitHub with the runner application and other tools preinstalled, and is available with Ubuntu Linux, Windows, or macOS operating systems. When you use a GitHub-hosted runner, machine maintenance and upgrades are taken care of for you.

You can choose one of the standard GitHub-hosted runner options or, if you are on the GitHub Team or GitHub Enterprise Cloud plan, you can provision a runner with more cores, or a runner that's powered by a GPU processor. These machines are referred to as "larger runners." For more information, see _About larger runners_.

Using GitHub-hosted runners requires network access with at least 70 kilobits per second upload and download speeds.

---

## Using a GitHub-hosted runner

To use a GitHub-hosted runner, create a job and use `runs-on` to specify the type of runner that will process the job, such as `ubuntu-latest`, `windows-latest`, or `macos-latest`. For the full list of runner types, see _About GitHub-hosted runners_. If you have `repo: write` access to a repository, you can view a list of the runners available to use in workflows in the repository. For more information, see _Viewing available runners for a repository_.

When the job begins, GitHub automatically provisions a new VM for that job. All steps in the job execute on the VM, allowing the steps in that job to share information using the runner's filesystem. You can run workflows directly on the VM or in a Docker container. When the job has finished, the VM is automatically decommissioned.

The following diagram demonstrates how two jobs in a workflow are executed on two different GitHub-hosted runners.
