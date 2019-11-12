> Csaba Zamolyi  
> _Author_
>
> Aug 14, 2018  
> _Created_

### _1. Tasks, tasks, tasks_

This is why we use Git & GitLab with it. If we don't have tasks we could just simply use command line git can't we? So we have several nice features coming with GL and on of them is task / issue management.
There should be no work on code not covered by at least one task. So if you want to do something take the time and create an issue on GitLab. Provide only information that is _required_ for that task and others to understand what's happening. _No bullshit!_ GitLab is a place for coding stuff not business stuff. We are not outsiders and children who don't understand IT words, right? Be _short_ and concise.
​

### _2. Outline and plan what you want to do._

Enough of continuous try-catch, that doesn't lead us anywhere. You have an idea of doing a new page like restaurant list? Yeah, go and plan it, see what smaller subtasks there are: cards for a restaurant, sidebar, scrolling, etc. You can create smaller to-do items for these in your task. If they're bigger then go for separate issues for them.
Design it, upload the scratch or whatever to GitLab (images are preferred so we can instantly see it)
@john Give feedback on new designs / tasks as soon as possible. It's your responsibility to know and say what you need or not, but it's also the developers' responsibility that only do what is needed to be done.
​

### _3. Stop "dreaming" and stacking tasks_

Imagine what is happening now. You're thinking about a task, you jump right into it but you discover another stuff so you start working on that and you discover something again and... This is a never-ending spiral. Stop it! Focus only on your current task and when it is finished you can move forward. Never forget planning. (see point 2) Otherwise if you have an idea, _don't jump into it_ but create a task and do it after you're done with the current feature. If you really need to interrupt your current task because you must do something else to make it work, that means usually one thing: you planned in wrong (or haven't planned). Then create a new task for the problem and start working on it. No untracked work, please!
​

### _4. Required Git workflow_

We use Git and not SVN. Why? Beacuse Git has great power over SVN with its branching model. There are a few principles.

#### 4.1. Commit!

Yes, we use git because we want to see how a task gets done and what steps, problems, etc. it took to finish. Commit after EVERY significant step. In a project like this usually 8-12 commits would be ideal per day. If you finished let's say the card for the restaurant in the restaurant list page it definitely means a commit.

#### 4.2 Master is clean

The master branch must contain code that's working (usable). There must be no broken or unfinished code / feature in master. There must be feature branches for every SIGNIFICANT feature (taking more than 1-2 commits with the commit rules above). The naming convention for them is simply `feature/my-feat` (where my-feat is obviously the very short description/name of the feature)

#### 4.3 Code review

You think this is enterprisey? No it's not. Even the smallest teams do this to reduce their fault rate and such.
When you're done with the feature you submit a merge request and I'll look over the code, check if it's deployable, we test it and then it goes to master. I want to prevent crappy code go out to master. Even very good developers can write bad code when there are no others reviewing it, so this becomes necessary. I'm senior enough to understand and see what code is clean and what is not. If there are small issues I'll fix it, if there are bigger ones I'll open an issue with the errors I see.

#### 4.4. No "global" changes on feature branch

If something is not that one-click easy it doesn't mean it's bad. Don't do a change on your feature branch that changes the whole system globally. If a "global" change is required, create a task for it, a feat branch (if reqd) from master, do the global change, put it back to master (if the change is not small, please MR) and rebase your feature on master. Does this sound hard? I have bad news: Git is not for only clicking the commit button. Git is for doing VCS right. Learn this and eventually you'll feel this in your hands instantly and it becomes easy.
This is exceptionally important because you (Lukas, Mate) will work on the same project but hopefully different parts of it. If one of you changes something globally on his feat branch and the other one doesn't know about it, it will fuck up the other devs work entirely when he submits the MR. So, don't do that please.

#### 4.5 Meaningful commit messages

Commit messages like 'fix' or 'cleanup' or 'commit' are bad. Please describe in a few words what you did: 'Cards for restaurants in list view' or 'fixed #24'
When you want to write this: 'fixed #24 and created new page and fixed data structure' - You can know that you should've created 3 commits...
​
Git Workflow explained: https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow
​

### _5. Testing_

Test your code. For logic / data layers TDD would be ideal. For JS I really recomment mocha, chai, sinon. UI test probably can be done manually for now, but data & logic must be unit (& integration later) tested automatically.
​

### _6. Communication_

Ask when required but don't ask the obvious. We are developers and we know how interruptions break our workflow. But when you really need to ask something, do it!
We are a team and we need to know who is the most experienced in what.
Mate is best in ui design concepts and layout build, branding, texts, etc.
Lukas is best in the logic behind frontend, f.e techniques, react, etc.
I know these about you and later on I'll try to know more. Please help me complete the list about you. You also need to know what questions you can ask from me:

- general coding practices, structures, standards
- code architectural patterns, code organization
- language-specific shortcuts, best practices, pitfalls
- Workflow, CI-CD, DevOps
- backend stuf

PLEASE ASK each other before do try-catching, really. If none of us knows the answer or doesn't respond in a reasonable time then okay, start experimenting but try to avoid this situation.
​

### 7. DON'T wait!

When you are starting a task or planning a bigger "milestone", **identify the dependencies** between tasks. If you have to wait for something to finish your current task, DON'T WAIT, go to another task that is **independent** of the current. (Of course on a different branch!) I think this is clear.
​

### 8. Coding rules

Clean Code. Make your code understandable for others. Don't add comments, make your code explain itself. If only you can understand the code is bad. If you need to add comments, your code probably could be much better. Keep this in mind and find tips in Robert C. Martin's Clean Code book. (Most of the developers keep this book as their Bible (um.. one of them))
