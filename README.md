GGScoreoid
============

Scoreoid is a 'non-restrictive, reliable and easy to use server platform for game developers' 
and GGScoreoid makes it easy to use in the Corona SDK.

Basic Usage
-------------------------

##### Require the code
```lua
local GGScoreoid = require( "GGScoreoid" )
```

##### Create your scoreoid object
```lua
local scoreoid = GGScoreoid:new( apiKeY, gameID )
```

##### Create a player
```lua
local onComplete = function( success, message )
	print( success, message ) 
end
scoreoid:createPlayer( "testUser1", nil, onComplete )
```

##### Create a player with more values set
```lua
local onComplete = function( success, message )
	print( success, message ) 
end

local options = {}
options.password = "monkey"
options.score = 50
options.email = "test@gmail.com"
options.platform = system.getInfo( "platformName" )

scoreoid:createPlayer( "testUser2", options, onComplete )
```

##### Edit a player
```lua
local onComplete = function( success, message )
	print( success, message ) 
end

local options = {}
options.email = "bob@gmail.com"
scoreoid:editPlayer( "testUser1", options, onComplete )
```

##### Delete a player
```lua
local onComplete = function( success, message )
	print( success, message ) 
end
scoreoid:deletePlayer( "testUser1", onComplete )
```

##### Count all players
```lua
local onComplete = function( count )
	print( count ) 
end
scoreoid:countPlayers( nil, nil, nil, onComplete )
```

##### Count players created between two dates
```lua
local onComplete = function( count )
	print( count ) 
end
scoreoid:countPlayers( "2012-01-01", "2012-03-25", nil, onComplete )
```

##### Count players created between two dates on a certain platform
```lua
local onComplete = function( count )
	print( count ) 
end
scoreoid:countPlayers( "2012-01-01", "2012-03-25", "iOS", onComplete )
```

##### Get the value of a field on a player
```lua
local onComplete = function( content, field )
	print( content, field ) 
end
scoreoid:getPlayerField( "testUser1", "email", onComplete )
```

##### Update the value of a field on a player
```lua
local onComplete = function( success, message )
	print( success, message ) 
end
scoreoid:updatePlayerField( "testUser1", "email", "bob@bob.com", onComplete )
```

##### Get the scores of a player with optional start and end dates and optional difficulty
```lua
local onComplete = function( scores )
	for i = 1, #scores, 1 do
		print( scores[ i ].score )
	end
end
scoreoid:getPlayerScores( "testUser5", "2012-01-01", "2012-12-25", 3, onComplete )
```

##### Get scores
```lua
local onComplete = function( scores )
	for i = 1, #scores, 1 do
		print( scores[ i ].username, scores[ i ].score )
	end
end
scoreoid:getScores( orderBy, order, limit, startDate, endDate, platform, difficulty, onComplete )
```

##### Get total score count
```lua
local onComplete = function( scores )
	print( "Total:", scores )
end
scoreoid:countScores( startDate, endDate, platform, difficulty, onComplete )
```

##### Get best score count
```lua	
local onComplete = function( scores )
	print( "Best:", scores )
end
scoreoid:getBestScores( startDate, endDate, platform, difficulty, onComplete )
```

##### Get the average score
```lua	
local onComplete = function( score )
	print( "Average:", score )
end
scoreoid:getAverageScore( startDate, endDate, platform, difficulty, onComplete )
```

##### Get total score count
```lua	
local onComplete = function( scores )
	print( "Best:", scores )
end
scoreoid:countBestScores( startDate, endDate, platform, difficulty, onComplete )
```

##### Get game information
```lua	
local onComplete = function( game )
	for k, v in pairs( game ) do
		print( k, v )
	end
end
scoreoid:getGame( onComplete )
```

##### Get game field
```lua
local onComplete = function( content, field )
	print( content, field )
end
scoreoid:getGameField( "name", onComplete )
```

##### Get game field average, everything is optional bar the actual field name
```lua
local onComplete = function( average, field )
	print( average, field )
end
scoreoid:getGameAverage( "lives", startDate, endDate, platform, onComplete )
```

##### Get game top game field, everything is optional bar the actual field name
```lua
local onComplete = function( top, field )
	print( top, field )
end
scoreoid:getGameTop( "lives", startDate, endDate, platform, onComplete )
```

##### Get game lowest game field, everything is optional bar the actual field name
```lua
local onComplete = function( lowest, field )
	print( lowest, field )
end
scoreoid:getGameLowest( "lives", startDate, endDate, platform, onComplete )
```

##### Get game total of a game field, everything is optional bar the actual field name
```lua
local onComplete = function( total, field )
	print( total, field )
end
scoreoid:getGameTotal( "lives", startDate, endDate, platform, onComplete )
```

##### Get a list of all your games notifications
```lua
local onComplete = function( notifications )
	for i = 1, #notifications, 1 do
		for k, v in pairs( notifications[ i ] ) do
			print( k, v )
		end
	end
end
scoreoid:getGameNotifications( onComplete )
```

##### Destroy the scoreoid object
```lua
scoreoid:destroy()
scoreoid = nil
```

Update History
-------------------------

##### 0.1
Initial release