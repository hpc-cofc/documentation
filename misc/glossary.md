---
description: >-
  The definitions below are related to this document and are provided for quick
  reference.
---

# Glossary

For other terms commonly used in research software engineering environments, please see the [USRSE glossary](https://github.com/rseng/rse-glossary/blob/master/_data/terms.yml)

## Terms

| Term | Definition |
| :--- | :--- |
| Bash | A UNIX shell used for entering command-line executions. Included with most Linux distributions and macOS. Includes SSH capability. |
| Cluster | Servers, networked to execute batch jobs that require high core count, not possible on a single physical server |
| Hypervisor | Also known as a _virtual machine monitor_, a hypervisor is software/hardware that creates, runs, and manages virtual machines. |
| Instance | A virtual machine set up through OpenStack. See "Virtual Machine". |
| OpenStack | A cloud operating system that controls large pools of compute, storage, and networking resources throughout a data center. |
| Project | The base unit of "ownership" in OpenStack. All resources in OpenStack should be owned by a specific project. In OpenStack Identity, a project must be owned by a specific domain. |
| Scheduler | Software responsible for the job, queue, and user management and accounting, e.g. Slurm |
| Virtual Machine | An operating system instance that runs on top of a hypervisor. Multiple virtual machines \(VMs\) can run at the same time on the same physical host. |

# Research software engineering terms

This was taken from the [USRSE glossary](https://github.com/rseng/rse-glossary/blob/master/_data/terms.yml)

| Name | Definition |
|:------------|:----------------------------------------------------|
| research software engineer | Those who regularly use expertise in programming to advance research. https://us-rse.org/what-is-an-rse/
| digital humanities | computational work and software for traditionally liberal arts oriented domains   https://en.wikipedia.org/wiki/Digital_humanities
| reproducibility | the extent to which a workflow or series of steps can be performed again as originally intended  https://en.wikipedia.org/wiki/Reproducibility
| sustainability | the ability for software, policy, or community to be maintained at a certain rate or level over a long period of time  https://en.wikipedia.org/wiki/Sustainability
| cyberinfrastructure | research environments that support advanced data services and computing beyond the scope of a single institution. https://en.wikipedia.org/wiki/Cyberinfrastructure
| ask-cyberinfrastructure | A platform for high performance computing administrators and users to share knowledge and ask questions about cyberinfrastructure, available at ask.ci. https://ask.cyberinfrastructure.org/
| exascale | a level of supercomputing intended to hit a quintillion calculations per second, and mirror processes in biology, climate, and physics. https://www.exascaleproject.org/what-is-exascale/
| containers | encapsulated environments and namespaces that provide an abstraction for reproducible analyses and workflows. https://en.wikipedia.org/wiki/OS-level_virtualization
| supercomputing (SC) | the Supercomputing conference that takes place annually, one of the largest for HPC enthusiasts in the world. http://supercomputing.org/
|  PEARC | The Practice and Advanced Experience in Research Computing Conference series (pronounced 'perk'). https://www.pearc.org/
| version control | a system that lets you keep every version of a file, in the case that you need to restore it later. Common version control online services like GitHub or GitLab provide you with a remote repository to interact with using git.  https://git-scm.com/book/en/v1/Getting-Started
| code reviews | the practice of looking over other's code for possible bugs and improvements, and to ensure that work done is in scope with goals for the project. Code reviews are typically done by way of version control platforms when one person wants to merge their changes with the main project branch. This is called a 'pull request' on GitHub. https://google.github.io/eng-practices/review/reviewer/
| continuous integration (ci) | the process of continually and regularly testing, building, and deploying your code to ensure that bugs don't pop up. You can typically use a CI service integrated with your version control to automate this process. Examples of common CI services include CircleCI, GitHub CI, GitLab CI, Travis CI, and Semaphore. https://en.wikipedia.org/wiki/Continuous_integration
| requirements | the minimal set of software and library dependencies (and their versions) for a software project. https://hackernoon.com/proper-software-requirements-101-32cf87e02a2f
| repository | refers to a folder for a software project, commonly with a .git folder for version control https://help.github.com/en/github/creating-cloning-and-archiving-repositories/about-repositories
| pair programming | working on a problem with another engineer, with typically one person sitting at the keyboard and the other watching and helping verbally. https://en.wikipedia.org/wiki/Pair_programming
| cloud | refers to a network of remote servers, databases, and other resources for compute that can be available on demand. https://en.wikipedia.org/wiki/Cloud_computing
| API |  an application programming interface, or a set of functions exposed by a provider for some service. https://www.freecodecamp.org/news/what-is-an-api-in-english-please-b880a3214a82/
| devops | a combination of development and operations that aims to improve communication between traditionall disparate teams. In practice, it means using fast feedback loops to deliver features, fixes, and updates more frequently. https://newrelic.com/devops/what-is-devops
| code coverage | the percentage of a code base that is tested https://en.wikipedia.org/wiki/Code_coverage
| unit testing | the practice of testing individual components or functions of a software base http://softwaretestingfundamentals.com/unit-testing/
| integration testing | combination of functions (software units) to test as groups http://softwaretestingfundamentals.com/integration-testing
| regression testing | testing to ensure that changes in code don't break previously working functionality http://softwaretestingfundamentals.com/regression-testing
| static analysis | examining source code for errors before it is run https://www.perforce.com/blog/sca/what-static-analysis-static-code-analysis
| linting | analysis of source code for formatting and other language conventions. Linters can be run to validate, or can be used to automatically fix the file. https://en.wikipedia.org/wiki/Lint
| pull request | putting your money where your mouth is and taking a shot at fixing an issue in a code base, and then opening a request for it's review to merge into the main (usually master) branch https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests
| IDE | means 'Integrated development environment,' and combines writing code, building and debugging into a single interface https://www.codecademy.com/articles/what-is-an-ide
| TDD | means 'test-driven development', which is the idea of writing tests first then writing code that satisfies the tests https://en.wikipedia.org/wiki/Test-driven_development
| acceptance testing | acceptance testing is a test conducted to determine if the requirements of a specification or contract are met. https://en.wikipedia.org/wiki/Acceptance_testing


## Acronyms

| Acronym | Definition  |
|:---------|:---------------------------------
CLI | Command-Line Interface
DTN | Delay-Tolerant Network
GPU | Graphics Processing Unit
GUI | Graphical User Interface
IDE | integrated development environment
HPC | High-Performance Computing/Cluster
LDAP | Limited Lightweight Directory Access Protocol
MPI | Message Passing Interface
NFS | Network File System
S3 | Simple Storage Service
SFTP | Secure/SSH File Transfer Protocol
SLURM | Simple Linux Utility for Resource Management \(SLURM\) is a batch scheduling tool used to submit your calculations to run on appropriate compute resources.
SSH | Secure Shell
VM | Virtual Machine
