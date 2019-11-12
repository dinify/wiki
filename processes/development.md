> Csaba Zamolyi  
> _Author_
>
> Jun 17, 2018  
> _Created_

# Development Workflow in TABB

## General

The TABB development workflow follows agile methodology, since the scope of the project and the size of the team requires this.
Generally agile software development is an iterative process with continuous integration and continuous delivery.
Agile software development has very strict rules that must be followed in order to be successful with it.
Let's see these rules

![Agile Workflow](http://e5workflow.com/wp-content/uploads/2015/12/Agile-Development-1024x768.jpg)

## Task Management

One of the main points of agile is the management of tasks. Every piece of work must be covered by tasks that have not just a title but a description and specification of the given issue. Tasks must have additional value to the project.
And these tasks start a journey from the backlog to the closed status and through the CI/CD and QA, to the user. But this flow has strict rules!

### Creating Tasks (Desigh Phase)

At the start of every week all tasks for the entire week must be created and filled up with information. This process might take 1-2 hours depending on the given situation. We have to do it because we don't have a PM who should hold this responsibility. But we need the work of the PM to be done so we have to do it ourselves. It might be daunting that we are writing tasks at the start of the week, but this is the case, we must do this. If we don't, the result is clear.

Creating and managing the tasks properly solves many questions on Slack, like: 'So guys, what's the progress?', or 'What are the remaining problems?' or 'What have you worked on?' and such. These questions mean distraction, it breaks the workflow, also they are unnecessary if tasks are managed properly by the rules given here.

### The Value of Tasks

So if you do write tasks, the do it well. A non-descriptive oneliner or only-title-er task doesn't have any additional value for the project.
We cannot start a conversation about it, we cannot see why and how this task will be solved, etc.

So the task must answer a few questions:

- **What** do you want to do?
- **How** do you want to do it?
- **Why** do you want to do it?

These three questions above are **mandatory** for every task. Sure there are some optional questions also, like

- What will be changed with this tasks?
- What areas / other parts will this change affect?
- How the connected applications should be able to implement the change made to the system?

Taks are made **not only for yourself**. You must continuously think about other players in the system. Issues tell everything about how the project goes. Also prevents unnecessary discussion on Slack, even between developers. If everyone can clearly see exactly what is going on and is being developed, there should be no questions about this anymore on Slack.

Here is an example of a bad task:
![Bad Task](images/issue1.png)

And here is a good one:
![Good Task](images/issue2.png)

Issue Board
![Issue Board](images/issue3.png)

### Task Attributes

There are some techniques and extensions for this tasks system that must be used.

#### Labels

Labels mean the main part of organizing the tasks across the system. Every label attached to the task means something. If you cannot find a suitable label, create one. Although there are some mandatory ones, like `priority`, `severity` an `type`. In the issue boards tasks are organized by labels, so we must use these to tag the issues.

#### Weight

Issues can have weight. It is a number from 1 to 20 and represents how hard is to solve the task. So a few-liner task that is quite easy to implement will probably have a weight of 1 to 4. But a task that requires investigation, discussion, research, or is hard to implement, it will probably have a weight of 10 to 20. These are important to be filled because actually not the exact number of tasks finished counts but the sum weight of the finished tasks!

#### Time Tracking

Time tracking must be used because it is needed when we try to calculate how long the given milestone will take. We can estimate it better if all tasks have a filled 'estimate' field. Also the spent time should be tracked in the task, to see how we need to adjust the timeframe of a milestone or just fine tune our estimations.

#### Due Date

This is something that might be important in some situations, but in genereal, due date is not required if everyone follows the steps above. In some special cases there must be a due date, but we will see it when there is such a case. (Probably later.)

#### Milestone

There must be no issue without a milestone. But I will discuss this below.

## Milestones

A milestone is a bigger step in the system. A milestone **must be created before the issues** and must have a clear description of the required functionality. At the start of the week, if there is no remaining issues from the last week, we create the new milestone and write down what functionalities we want to implement in that week. After it is done, we can start creating the small tasks and assign the to the milestone. Also there should be a release milestone, and bug reports (tasks with `type: bug` label) should be assigned to that milestone. (Like `Release v0.5`)

The milestone is important part of tracking changes. It has charts to show how the issues are going and if we will reach the desired output in time or not. (It is called Burndown Chart.)

Milestone content
![Example](images/milestone1.png)

Burndown Chart
![Burndown Chart](images/milestone2.png)

## Git Workflow

The main and very strict point of agile git workflow that the `master` brach contains **only working and tested code**. No unfinished features and not properly working and tested parts can ever appear on master. If it does, agile is broken, since we cannot start a new feature while master is not fixed. Since this is a **team** project, we must not be selfish to push our crappy code to master to break everyone else's working copy of the product. Commit to master is **only** permitted through **merge requests**

### Feature Branches

For every feature you will be working on, create a feature branch with the prefix: `feature/`, so like `feature/login-ui`. Start working on your feature and if there is a change in master, **rebase** your feature branch on it. If you don't know how to do it: https://www.atlassian.com/git/tutorials/rewriting-history/git-rebase

Every feature branch should end in a **merge request** and should be merged to master.

### Merge Requests

When you are getting close to finish your feature, create a Merge Request. MR does what its name says: it is a request to merge your feature branch into master. This is the only way to push commits to master. Every merge request must be approved by at least one other member in the team. For example, if a relevant UI change is waiting to be merged, John must be added as an approver. If a relevant frontend logic is being merged, Mate must approve it. If a significant backend change is going on, Lukas must approve, and so on. These can change, but no merge request will be merged without approvers and will be immediately reverted by the system.

MRs are also assigned to milestones!

### Hotfix branches

Yes, you need to create a branch even if your fix is small. The first reason for that: you can never know if it really will be a small fix. The second reason is that you aren't able to push directly to master.

### Commit Messages

Commit messages should be long enoght to contain all the changes you have made. So if you did multiple things in a commit (you shouldn't be do too much though), the include them in the commit message, like:

```
Created login page
 - added login form
 - added login button and connected
 - added placeholder texts
```

This above is a useful commit message, because other dev can know exactly what happened without reading the whole changelist.

But if you just wrote `Created Login Page` we can't know what it covers. So please, be descriptive!

## Development Practices

### Clean Code

Clean code is the most important thing in what you write. The code you have written must be understandable for any (decent) developer. There are several rules of the clean code, but if you do frontend you have a slightly easier job since you don't have to think about very deep logic and hierarchy and such.

There is a book about this, written by Robert C. Martin (Uncle Bob), with a title: 'Clean Code - Handbook of Agile Software Craftmanship.' **Read it.** It is mandatory to understand what clean code means and how to do it. Here you can find it for free: https://www.investigatii.md/uploads/resurse/Clean_Code.pdf

A code quality measurement will be implemented in the CI and if it fails, the merge request will not be accepted until the quality reaches an acceptable level!

### Testing

There are several now pretty easy to use testing frameworks for every use case. For example, on frontend, there is http://webdriver.io/  
And in backend there are several language-specific testing frameworks.

Automated tests are **mandatory** for agile development. Without testing, the development won't be agile, releases will be late, bugs will appear, more and more, and the project is failed after a few months of operation.

No, no MR will be accepted without tests also. It is not so hard to write test for at least the critical parts of the system... Don't have to test the color of a button, but have to if the numbers are displayed correctly, if the list contains all items, etc. Check out thah WebDriver, it is quite easy to use.

### Code Review

Before the merge request gets accepted, the code in the changed files will be reviewed quickly and if changes are required, the merge request won't be accepted until they are fixed. Code must be reviewed by at least one other team member.
