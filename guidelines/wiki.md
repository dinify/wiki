# Wiki
_guidelines_

## Good example
Here is a very good example of a wiki done by the GitLab team.
https://about.gitlab.com/direction/

## Structure
### Introduction
The wiki itself is comprised of multiple (not exclusively) markdown files organized into and arbitraty hierarchy of folders. Each markdown file is considered to be a **page**. Pages are composed of **sections**, and each section and their content must conform to the guidelines agreed upon in this page.
### Page types
Each page type has a corresponding template that gives a framework as to how to structure that type of information. 
#### Guidelines
This kind of page should be similar to and RFC standard, it is instructive such that it uses the terms "must", "should", "may", and so on.
#### Processes
Documentation of an end-to-end process, step by step. It can be a solution to a specicic problem or bug that has reoccured or was complicated to solve.
#### Solutions
Usually a result of a d/a type task, that documents the result of doing research on a topic, suggestion, idea, or new trend. These pages usually describe a solution to a higher level problem that is not a step by step process, like a reserach paper comparatively.
#### Charts
Explain something visually. The team already has a massive collection of charts in Google Drive.
#### Notes
These can include notes from meetings, or from an article that a member of the team read online. This information should be filtered, processed further and structured into our knowledgebase. Discovered a new platform? A new tool? A new framework? Note pages should contain the already filtered, TLDR information that is relevant to the business.

## Formatting and content
Although sometimes obvious, every member of the team should contibute to the content of the wiki in order to organize the knowledge that the team gathers. By stating the obvious, the team can create a hierarchical, indexable repository of all that the team knows. This way, every new member that comes will be able to access this information fast in order to perform a task.
### Language
All documentation should be written in English, with some special terms that are part of our taxonomy database and can be looked up easily. Please use a spellchecker in the IDE or whatever environment the page is being written in.
### Links
Links that lead to a different page within the wiki must relative paths. This is so that if the wiki repository is cloned to a local filesystem, the URLs point to the files on disk as opposed to the ones on the gitlab.com domain. Similarly, the URL of the wiki page depends on the environment if the wiki is deployed on a different domain with GitLab Pages.
| Current page location | URL | Link text |
|-|-|-|
| In root | `./folder-1/file-1.md` | [folder-1/file-1](#) |
| In subfolder | `../folder-1/file-1.md` | [folder-1/file-1](#) |
| In `folder-1` | `./file-2.md` | [folder-1/file-2](#) |

Links should always be included if the peice of information or content being described refers to an external resource.

### Sections
The sections within a page each have a type. Since this wiki repository will be ever evolving, there isn't a predefined set of types. 
### Grammar and wording
Use passive voice where possible. 
Avoid the use of "us", "we" and other pronouns that refer to a person or the team. Task management tools are there to mitigate responsabilities. Refer to (processes/tasks)[../processes/tasks.md] for which tools are used for task management.
#### Terms
A collection of terms that list how pages in the wiki might be worded.

The business  
The team  
Team member, member of the team, person    
Restaurant partner (**RP**)  
Dinify platform  
User app  
Waiterboard  
Dashboard  
Restaurant menu  


## Modifications and versioning
To modify either this page or any other page in the wiki, versioning must be used. Fortunately this is build into git and gitlab. At some point