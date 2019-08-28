# Events
_Integration_
## Intro
This page summarizes the integrations that implement how events are handled within the team's infrastructure, so  notifications get delivered to the relevant communication channels or directly to a person.  
Design goals:
- minimize manual work
- optimize communication with relevant notifications
- alert the team in case of high priority action required

## Slack notifications integration
Since slack delivers realtime notifications to all of the devices it's installed on, we can use it for integration with other developer tools and send notifications.

#### GitLab
Links for integration settings
||
|-|
|[dinify/staging/app](https://gitlab.com/dinify/staging/app/-/settings/integrations) |
|[dinify/dinify-node-api](https://gitlab.com/dinify/dinify-node-api/-/settings/integrations) |
|[dinify/workspace](https://gitlab.com/dinify/workspace/-/settings/integrations) |
|[dinify/appengine](https://gitlab.com/dinify/appengine/-/settings/integrations) |
|[dinify/api](https://gitlab.com/dinify/api/-/settings/integrations) |


All repository write events (push, merge, etc.), as well as notifications in the GitLab webapp should be pushed to slack. This is configured on a per-repo basis (see link above), since the "Group Webhooks" feature in GitLab is only available for paid plans. If there will be a lot of repositories, it might be worth it in the future.

## Email notifications integration

In case the slack webhook fails, or integration is not possible with a tool, the implementation should fall back to sending an email. Internal, team-wise email addresses directly correspond to the channels the team uses on Slack.

## **Event**
Events are fired by any of our tools and also when steps are being taken within a process. Examples include: task created in Trello, code pushed to git, merge request created in GitLab.
_TODO: standardize and classify event types on the Dinify platform_