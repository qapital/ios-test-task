#iOS Test Task
The test task involves writing a simplified version of the user's list of savings goals, the list that the user sees when opening the app. This list should be displayed as the provided psd shows. Each goal has one entry in the list displaying the goals image, an optional target amount and how much has been saved. Goals can also be shared with other users in the system. In this case the goal will have a list of connected users and these should be displayed as well. 

When tapping a goal there should be a transition to the provided goal screen with the goals activities displayed. How you make this transition is up to you.

##Implementation
We provide you with a simplified API to get the list of goals to display and information about them. The API does not require any login. How you implement this and what external libraries you use are entirely up to you. Whats important to us is that the app is smooth and that scrolling does not have any stuttering.


The following API is available:

####Endpoint
http://qapital-ios-testtask.herokuapp.com

####/savingsgoals
This resource will return an object with one key, savingsGoals. This key maps to a list of goal objects with the following fields:

| Field          | Type	     | Description |
| -------------- | --------- | ----------- |
| goalImageURL   | String    | URL where the image can be downloaded from |
| userId         | Int       | Id of the user that owns this goal |
| targetAmount   | Float     | Target amount of the goal. Might be null |
| currentBalance | Float     | Current balance on the goal. How much has been saved |
| status         | String    | If this goal is active or deleted. A string that is either "active" or "deleted" |
| name           | String    | Name of the goal |
| id             | Int       | Unique id of the goal |
| connectedUsers | List<Int> | A list of user ids that this goal is shared with. |

####/savingsgoals/:id/feed
This resource will return an object with on key, feed. It contains various events that have happened on the goal, with relations to objects that have triggered them.

| Field         | Type      | Description |
| ------------- | --------- | ----------- |
| id            | String    | Unique id of the feed item |
| type          | String    | Describes the type of feed item. "saving" is the only allowed value. |
| timestamp     | timestamp | When the item occured. Format: 2015-03-10T14:55:16.025Z |
| message       | String    | A text (with html style elements) describing the item, to be displayed to the user |
| amount        | Float     | The amount saved to the goal |
| userId        | Int       | Id of the user that created the event, may be different from the user of the goal |
| savingsRuleId | Object    | Id of the rule that created the event, if it exists. See description below |

####/savingsrules
This resource will return an object with one key: savingsRules. The key maps to list of rule objects with the following fields:

| Field       | Type      | Description |
| ----------- | --------- | ----------- |
| id          | Int       | Unique id of the rule item |
| type        | String    | Describes the type of the rule. Allowed values: roundup, guilty_pleasure |
| amount      | Float     | Describes how much the rule will save. If the type is roundup, what amount should be rounded up to, otherwise how much will be saved. |

####/users/:id
This resource will return a user object for a specific id. The user object has the following fields:

| Field          | Type   | Description |
| -------------- | ------ | ----------- |
| userId         | Int    | Unique user id |
| displayName    | String | Display name of user |
| avatarUrl      | String | URL where the users avatar can be downloaded from |

##Testing
You should add at least some simple tests. At what level and how much of the app you test is up to you but please reason around the decisions you made.

##Design
There are two psds available in the repo with how we would like you to display this list as well as the goal view. The needed fonts are available as well. Assets for the rule images are available as well.

##Submiting
Just send us your code along with a description on how to run the app and the tests. If there is anything that you have not had time to complete or intentionally left out please reason on how you would implement it or why it was left out.
