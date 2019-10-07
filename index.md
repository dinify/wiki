# Dinify platform wiki
## Introduction
Welcome to the wiki, this repository serves as a central source of information within the team. All documentation of our research, knowledge. Refer to [guidelines/wiki](./guidelines/wiki.md) how to contribute.
## Table of contents
_TODO: use github pages to generate a styled version of all the markdown pages. The table of contents will become a convenient navigation header in the html output._

|  |  |
|--|--|
| _(this page)_ | [index](./index.md) |
| | |
| **Guidelines** | |
| For this wiki | [guidelines/wiki](./guidelines/wiki.md) |
| For team members | [guidelines/team](./guidelines/team.md) |
| Coding guidelines | [guidelines/code](./guidelines/code.md) |
| | |
| **Ingegrations** | |
| Charts | [integrations/charts](./integrations/charts.md) |
| Events | [integrations/events](./integrations/events.md) |
| | |
| **Processes** | 
| Tasks | [processes/tasks](./processes/tasks.md) |
| | |
| **Solutions** | |
| Navigation | [solutions/navigation](./solutions/navigation.md) |
| Technology stack | [tech-stack](./tech-stack.md) |

## Goal
Merge business logic, documentation, and other sources of information into a central, indexable, structured, and hierarhical location. Using versioning will help us "stage" new peices of knowledge and review it before merging it into the main branch.

## Platform specification
### Roles and actors
### Business goals
### Domains
`dinify.app` is the production domain.
`dinify.dev` is the staging domain. Any subdomain created on these domains will need to use a slug formatted version for any resource.
### Products
### Features
### Roadmap
_(list of milestones/stories/epics)_

## Codebase
All code is hosted here, on gitlab. Any code hosted outside of gitlab must be linked here in the wiki.
### Repository structure
#### Workspace repository
#### Artifacts
### Dependency management
### Package management
### Coding guidelines
...

## Taxonomy
### Definition
_(source: [dpci.com](https://www.dpci.com/insights/taxonomy-vs-metadata))_
>Taxonomy (...) is the science of classification according to a pre-determined system with the resulting catalog used to provide a conceptual framework for discussion, analysis, or information retrieval.
Learn more: https://increment.com/internationalization/programming-as-translation/

### Example
Here is an example of how a taxonomic database looks like:
[dl.acm.org](https://dl.acm.org/ccs/ccs_flat.cfm#10011007)


### Introduction
These terms describe and standardize parts of the business and the logic guarding it. Pluralization and formatting of terms depend on the context they are used in. For example, in a URL, or in a marketing campaign tracking tag, a term is formatted like a slug, but in an SQL database, it's snake case, and in camel case a Javascript context.  

### Additions
Any term should be added to our taxonomic database that provides metadata in a software context, and is highly relevant to the business.

