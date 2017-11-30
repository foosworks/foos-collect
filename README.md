# foos-collect
API intended to receive foos table activity from sensors and store appropriately

This application is intended to be deployed automatically from this repository using the embedded Docker configuration files.


Casual Match
------------

Create a game

```
<- POST /api/v1/table/?token=TOKEN
   {
    'score_wins': '5',
    'game_wins': '2',
   }
-> 200
   {
    'match': { 'id': 'ID' }
    'game': { 'id': 'ID' }
    'red': { 'id': 'ID' }
    'blue': { 'id': 'ID' }
   }
```

Score a goal

```
<- POST /foos/api/v1/goal/?token=TOKEN
   {
    'game': { 'id': 'ID' }
    'concede': 'ID'
   }
-> 200
   {
    'goal_id': 'ID',
    'blue_score': 'NUM',
    'red_score': 'NUM',
    'match_done': 'no',
    'next_game': 'ID'
   }
```

Reverse a goal

```
<- DELETE /foos/api/v1/goal/{goal_id}?token=TOKEN
-> 200
   {
    'blue_score': 'NUM',
    'red_score': 'NUM',
    'match_done': 'no',
    'next_game': 'ID'
   }
```


Tournament Match
----------------

Create a game

```
<- POST /foos/api/v1/table/?token=TOKEN
   {
    'blue_goalie': 'ID',
    'red_goalie': 'ID',
    'blue_striker': 'ID',
    'red_striker': 'ID',
    'score_wins': '5',
    'game_wins': '2',
   }
-> 200
   {
    'match': { 'id': 'ID' }
    'game': { 'id': 'ID' }
    'red': { 'id': 'ID' }
    'blue': { 'id': 'ID' }
   }
```


Score a goal

```
<- POST /foos/api/v1/goal/?token=TOKEN
   {
    'game': { 'id': 'ID' }
    'concede': 'ID'
   }
-> 200
   {
    'goal_id': 'ID',
    'blue_score': 'NUM',
    'red_score': 'NUM',
    'match_done': 'no',
    'next_game': 'ID'
   }
```


Reverse a goal

```
<- DELETE /foos/api/v1/goal/{goal_id}?token=TOKEN
-> 200
   {
    'blue_score': 'NUM',
    'red_score': 'NUM',
    'match_done': 'no',
    'next_game': 'ID'
   }
```


Cancel a game

```
DELETE /api/v1/games/{game_id}/
```
