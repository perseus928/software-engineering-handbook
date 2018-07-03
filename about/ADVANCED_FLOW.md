# Advanced Workflow for Contributing to the Handbook

The following workflow describes the advanced steps required to contribute content for a new 
subject: 

1. [Select Subject](#select-subject)
2. [Set Development Environment](#set-development-environment)
3. [Fork Handbook Repository](#fork-handbook-repository)
4. [Create Content](#create-content)
5. [Connect Content with the Handbook](#connect-content-with-the-handbook)
6. [Build Handbook](#build-handbook)
7. [Submit Pull Request](#submit-pull-request)

When contributing enhancements to an existing subject only part of these steps are 
relevant.

## Select Subject

Think about a subject that is of interest to Software Engineers and from your own experience is not
covered well by existing tutorials or is not easily accessible.

Explore the [detailed Table of Contents (TOC)](toc.md) to get ideas of such subjects and identify 
where your contribution may fit. If you think that the current TOC requires changes, we recommend 
that you open an issue that presents your change or fix, before submitting a pull request.

## Set Development Environment

While developing your new content using this advanced workflow, it will be part of your local clone 
of the forked [handbook repository on GitHub][1].

Therefore, you have to set an environment that will allow you to conveniently edit content and 
use [Git][2] to track the changes you are doing and push changes back to the fork on GitHub.

Such environment could be your Windows PC with Git for Windows installed. However, Linux and MacOS
are more natural environment for this task. If you do not have a Linux or MacOS computer, we 
recommend using a Linux Virtual Machine (VM) hosted on a Windows PC. This may sound complex if you 
do not have experience with that. However, using [Vagrant][3], for instance, can simplify this task 
significantly. 

Such setup allows you to work on your Windows PC and on the VM and share files between these two 
machines transparently. For instance, you could use your favorite text editor on Windows and commit
the changes using Git on the Linux VM.

A recommended text editor for Windows is [Sublime Text][4]. It support many plug-ins, including 
Markdown syntax highlighting and Markdown preview, which are both useful with developing content.
Sublime Text has a sophisticated [package control manager][5], simplifying the search and 
installation of new packages.

## Fork Handbook Repository

Visit [Contributing to an Open Source Project][6] for instructions on how to fork and clone the 
[handbook repository on GitHub][1].

## Create Content

### Prerequisites

Learn about the differences between [Guides](Guides) and [Topics](Topics) in the context of the 
Software Engineering Handbook.

Understand the [structure and conventions](README.md) used for the handbook.

### Guides and Topics Authoring

Create Guides and/or Topics for the selected subject. Include appropriate references to external 
sources with minimal duplications of exiting materials. Create internal links associating the 
set of Guides and Topics for the subject. 

### Content Style Guides

* Use [Markdown][7].
* See relevant examples in [Guides](Guides), [Topics](Topics), and 
  [config](config) directories.
* Use preview tools for Markdown

### Git Commit Messages Style Guides

* Use the present tense ("Add feature" not "Added feature")
* Use the imperative mood ("Move cursor to..." not "Moves cursor to...")
* Limit the first line to 72 characters or less

## Connect Content with the Handbook

Compose at least one [Metadata configuration file](config/metadata) to connect the Handbook
navigation tree with the new content. The [github.yml](config/metadata/github.yml) is a simple 
example of such configuration file, including a short introduction and references to GUides and 
Topics.

## Build Handbook

This is an optional step.

At any time during the development of new content, you can build a new version of the handbook with
the new content placed under Guides, Topics, and config folders of your local clone of the forked 
handbook repository.

If you like, you can skip this step of building the complete handbook and reviewing it, and jump 
straight to submitting a pull request with the authored content. 

However, building and reviewing the complete handbook may help you identify issues prior to 
submitting a pull request.

If you decide to build the handbook, you will have to install the right tools. This is done easily
with pip, which is a tool for installing Python packages.

ToDo: Provide instructions.

## Submit Pull Request

We use [GitHub Flow][8], which means all changes happen through [pull requests][6].

If you are a first time contributor, we recommend that you open an issue that presents your 
change or fix, before submitting a pull request.

---

[1]: https://github.com/uribench/software-engineering-handbook
[2]: http://software-engineering-handbook.com/Guides/Git/Git%20Overview
[3]: http://software-engineering-handbook.com/Guides/Vagrant/Vagrant%20Overview
[4]: https://www.sublimetext.com/
[5]: https://packagecontrol.io/
[6]: http://software-engineering-handbook.com/Guides/Git/Contributing%20to%20an%20Open%20Source%20Project
[7]: https://daringfireball.net/projects/markdown
[8]: https://guides.github.com/introduction/flow/index.html
