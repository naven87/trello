Trello
======

This library exposes the basic functions in the Trello API as a member functions which can be used in larger applications.
The library is was originally created by [@GraemeF].  Requires Restler to function.

Examples
--------
### Creating trello connection
	var Trello = require 'trello';
	var trello = Trello( <key>,<token>);
### Reading all cards from a given board and printing card name
	trello.getCardsOnBoard(<boardId>, function (error, result){
		if (error instanceOf Error) {
			sys.p(error);
		} else {
			for (var i=0; i < result.length; i++) {
				sys.p(result[i].name)
			}
		}
	})
	
API
---
### Intialize
#### Trello(key, token)
Creates the initial Trello connection. You will need a read/write token to enable all functionality
### Adding Items
#### addBoard(name, description, organizationId, callback)
Adds new board to your Trello Account
#### addListToBoard(boardId, name, callback)
Adds a new list to a given board
#### addCard(name, description, listId, callback)
Add a new card to a given list
#### addCommentToCard(cardId, comment, callback)
Add a comment to specified card
### Update Items
#### updateCard(cardId, params, callback)
Update a specified card with parameters passed  
Valid Parameters  

* name - Name of the card 
* desc - Description of the card
* closed - Open or close card (True/False)
* idList - Id of the list to move the card to
* due - assign a due date to a card (either date or null)

#### updateDescOnCard(cardId, description, callback)
Updates the description on a card
#### moveCard(cardId, listId, callback)
Moves a card to a new list, the listId is for the new list
#### addMemberToCard(cardId, memberId, callback)
Add a member to a card
### Get Items
#### getBoardMembers(boardId, callback)
Retrieve the members of a given board
#### getListsOnBoard(boardId, callback)
Retrieve lists on a given board
#### getCardsOnBoard(boardId, callback)
Retrieve all cards on a given board
#### getCard(cardId, callback)
Get an individual card
### Delete Items
#### deleteCard(cardId, callback)
Delete a single card

