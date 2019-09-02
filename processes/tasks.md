## Intro
No need to reinvent project management. Although SCRUM is the industry standard for software developer teams, it's just a set of habits and routines, not the holy bible of project management, and especially in our case where *self-management* is required, we have to come up with additional layer of processes to cover our specific needs, such as evaluation of each task at the end of the week by:
- if done: by level of relation to the goal of the sprint 
- if not done: by severity of delay caused (as John proposed)
so we can reflect on plan and its execution, and continuously build up the skill of prioritization and focus

## Definition
A task can be defined as a piece of work that can be assigned to one or more people within the team.

## Tools
**Trello.**  
Link: trello.com/dinify  
Later we may switch over to Jira because of it's better integration capabilities, when the team's scale is better suited for more complex project management.

## Workflow
**Step 1. Identify the task at hand.**  
This is usually done when reading something, having a random thought or being reminded of something through conversation.
General examples of a task include:
- request: _"Print a contract attachments"_
- management: _"MLM marketing strategy"_
- idea: _"Have a webassembly QR scanner"_
- suggestion: _"Translate menu to all supported languages by default"_
- research: _"PWA capabilities with http2"_
- design: _"Navigation graph for all frontends"_
- implementation: _"Create localization midddleware"_

**Step 2. Open Trello.**  
Either in the app on your phone or on trello.com/dinify

**Step 3. Search existing tasks.**  
In the top search bar, search for any of the keywords that are related to the task about to be created. Make sure that the new task being created is not a duplicate of an already existing task. If it already exists, the priority may be modified, or a comment be made where the need to fulfill that task occured.

**Step 4. Categorize.**  
As you can see, there are three boards in Trello: Backend, Frontend and Business. If the task is not related to either of these, discuss with the team to create a new board that is the most general category for the task. Choose the board that the task is related to.

**Step 5. Create task.**  
At the bottom of the _"Backlog"_ column, type the title of the task in text field. Start with a prefix if it can be further categorized, beginning with the higher-most level category and using slaches to create hierarchy, followed by a colon and what needs to get done. 

**Step 6. Assign to someone.**  
Consider the role that each member of the team has, and select and assignee based on that. If you are fulfilling that role then you may assign yourself. If it is not clear, the team will go over the assigment at the weekly sprint meeting if it is a high priority.

**Step 7. Label.**  
Priority label is required. Labeling the task for what type of task it is will help others find it by filtering. If you are assigning yourself and getting started on it soon then it's optional.

**Step 8. Add task content _(optional)_.**  
If the title is not specific enough for the assignee to understand, then add a description, checklist, attachment, or anything that will help the assignee get started right away without having to ask questions or comment under the task. 

### Exmaples
Tasks created in Backend board's backlog column:  
```
DevOps: copy production db to test

DevOps / CI: set up staging for user app

API / v2: table status endpoint
```

## Weekly sprints
Each weekend, the team goes over what tasks to work on for the next week. We set the deadlines based on the priorities and move them to the _"Selected for sprint"_ column. 
Refer to google doc by Lukas.