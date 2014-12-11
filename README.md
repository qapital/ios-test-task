#iOS Test Task
The test task involves writing a simplified version of the user's list of savings goals, the list that the user sees when opening the app. This list should be displayed as the provided psd shows. Each goal has one entry in the list displaying the goals image, an optional target amount and how much has been saved. Goals can also be shared with other users in the system. In this case the goal will have a list of connected users and these should be displayed as well. 

When tapping a goal there should be a transition to a fullscreen display of the goal image. How you decide to do this transition is up to you.

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
There is a psd available in the repo with how we would like you to display this list. The needed fonts are available as well.

##Submiting
Just send us your code along with a description on how to run the app and the tests. If there is anything that you have not had time to complete or intentionally left out please reason on how you would implement it or why it was left out.
