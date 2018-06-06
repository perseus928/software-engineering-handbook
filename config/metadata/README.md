# Metadata Configuration Files

The optional metadata configuration files are used to compose the `index.md` files for each directory
in the navigation tree. The composition of the `index.md` files is done using a **Jinja2** template 
file.

All the metadata configuration files are placed directly under `/config/metadata` directory without 
additional grouping directories.

There are two types of index.md files:
- Non-leaf index files - hosted buy non-leaf directories
- Leaf index files - hosted by tree leaf directories

## Anatomy of Index Files

Index files are composed of the following parts:
- Title - mandatory. taken from the navigation configuration (e.g., root.yml).
- Introduction - optional. taken from metadata.
- Contents - mandatory. exists only in Non-leaf index files. taken from the navigation configuration.
- Guides - optional. taken from metadata.
- Topics - optional. taken from metadata.

### Title

The name of the hosting directory. A mandatory part. It is taken automatically from the navigation 
tree configuration file and not from metadata.

### Introduction

Free text providing an introduction to the subject of the hosting directory. An optional part. 
It is provided by a metadata file associated with the hosting directory.

YAML item type: dictionary
Key: intro
Value: text with optional Markdown syntax

Example:

```yml
intro: |
  Vagrant is an open source wrapper around a Virtual Machine provider, such as Oracle's 
  VirtualBox. It makes it easy to create and run a Virtual Machine (VM) from the command line.
```

### Content

List of the next navigation level. Equal to the names of the children directories
of the hosting directory (siblings of the index file). It is taken automatically from the navigation  
tree configuration file and not from metadata. A mandatory part that exists only in non-leaf index 
files.

### Guides

List of references to guides relevant to the subject of the hosting directory. An optional part. 
It is provided by a metadata file associated with the hosting directory.

YAML item type: dictionary
Key: guides
Value: list of links relative to the `/Guides` directory

Example:

```yml
guides:
  - Vagrant/Vagrant Overview
  - Vagrant/Vagrant Installation
  - Vagrant/Getting Started with Vagrant
  - Vagrant/Known Issues
```

Notes: 
1. The guides under the `/Guides` directory are grouped under one-level of grouping directories. 
   In the above example, the grouping directory is `Vagrant`.
2. The links should be without leading or training `'/'`
3. No Markdown syntax is allowed

### Topics

List of references to topics relevant to the subject of the hosting directory. An optional part. 
It is provided by a metadata file associated with the hosting directory.

YAML item type: dictionary
Key: topics
Value: list of links relative to the `/Topics` directory

Example:

```yml
topics:
  - SSH Protocol
```

Restrictions: 
1. All the topics are placed immediately under `/Topics` without additional grouping directories.
2. The links should be without leading or training `'/'`
3. No Markdown syntax is allowed

## Metadata File Naming Principles

Metadata files are associated 1-1 with directories in the navigation tree.
By default, their name is a "slagified" version of the 'Humanized' (i.e., title case with spaces)
name of the associated directory as defined by the navigation tree configuration file (e.g., root.yml)

For instance, a directory called `Vagrant and VirtualBox` will be associated by default with an 
optional metadata file called `vagrant-and-virtualbox.yml`

The optional argument `@id=<unique-id-value>` of any node in the navigation tree configuration file 
can be used to specify a custom id of the associated navigation node. When used, the respective 
metadata filename will be `<unique-id-value>.yml`  

## Metadata File Example

The following example is taken from `/config/metadata/vagrant-and-virtualbox.yml`.

```yml
intro: |
  Vagrant is an open source wrapper around a Virtual Machine provider, such as Oracle's 
  VirtualBox. It makes it easy to create and run a Virtual Machine (VM) from the command line.

guides:
  - Vagrant/Vagrant Overview
  - Vagrant/Vagrant Installation
  - Vagrant/Getting Started with Vagrant
  - Vagrant/Known Issues
```

## Jinja Template for Index Files

The following Jinja2 template is used to compose the `index.md` files.  
It is located at `/config/templates/index-template.j2`

```jinja2
# {{title}}

{% if intro is defined and intro -%}
{{intro}}
{% endif -%}

{% if contents is defined and contents -%}
## Contents

{% for c in contents -%}
- {{c}}
{% endfor -%}
{% endif -%}

{% if guides is defined and guides -%}
## Guides

{% for g in guides -%}
- {{g}}
{% endfor -%}
{% endif -%}

{% if topics is defined and topics -%}
## Topics

{% for t in topics -%}
- {{t}}
{% endfor -%}
{% endif -%}
```
