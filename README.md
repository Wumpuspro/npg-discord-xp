

# Discord-Xp

# Download & Update
You can download it from npm:
```cli
npm i npg-discord-xp
```
You can update to a newer version to receive updates using npm.
```cli
npm update npg-discord-xp
```


```js
/* xpFor Example */
const Levels = require("discord-xp");
// Returns the xp required to reach level 30.
var xpRequired = Levels.xpFor(30);

console.log(xpRequired); // Output: 90000
```

# Setting Up
First things first, we include the module into the project.
```js
const Levels = require("discord-xp");
```
After that, you need to provide a valid mongo database url, and set it. You can do so by:
```js
Levels.setURL("mongodb://..."); // You only need to do this ONCE per process.
```

# Examples
*Examples can be found in /test*

# Methods
**createUser**

Creates an entry in database for that user if it doesnt exist.
```js
Levels.createUser(<UserID - String>, <GuildID - String>);
```
- Output:
```
Promise<Object>
```
**deleteUser**

If the entry exists, it deletes it from database.
```js
Levels.deleteUser(<UserID - String>, <GuildID - String>);
```
- Output:
```
Promise<Object>
```
**deleteGuild**

If the entry exists, it deletes it from database.
```js
Levels.deleteGuild(<GuildID - String>);
```
- Output:
```
Promise<Object>
```
**appendXp**

It adds a specified amount of xp to the current amount of xp for that user, in that guild. It re-calculates the level. It creates a new user with that amount of xp, if there is no entry for that user. 
```js
Levels.appendXp(<UserID - String>, <GuildID - String>, <Amount - Integer>);
```
- Output:
```
Promise<Boolean>
```
**appendLevel**

It adds a specified amount of levels to current amount, re-calculates and sets the xp reqired to reach the new amount of levels. 
```js
Levels.appendLevel(<UserID - String>, <GuildID - String>, <Amount - Integer>);
```
- Output:
```
Promise<Boolean/Object>
```
**setXp**

It sets the xp to a specified amount and re-calculates the level.
```js
Levels.setXp(<UserID - String>, <GuildID - String>, <Amount - Integer>);
```
- Output:
```
Promise<Boolean/Object>
```
**setLevel**

Calculates the xp required to reach a specified level and updates it.
```js
Levels.setLevel(<UserID - String>, <GuildID - String>, <Amount - Integer>);
```
- Output:
```
Promise<Boolean/Object>
```
**fetch** (**Updated recently!**)

Retrives selected entry from the database, if it exists.
```js
Levels.fetch(<UserID - String>, <GuildID - String>, <FetchPosition - Boolean>);
```
- Output:
```
Promise<Object>
```
**subtractXp**

It removes a specified amount of xp to the current amount of xp for that user, in that guild. It re-calculates the level.
```js
Levels.subtractXp(<UserID - String>, <GuildID - String>, <Amount - Integer>);
```
- Output:
```
Promise<Boolean/Object>
```
**subtractLevel**

It removes a specified amount of levels to current amount, re-calculates and sets the xp reqired to reach the new amount of levels. 
```js
Levels.subtractLevel(<UserID - String>, <GuildID - String>, <Amount - Number>);
```
- Output:
```
Promise<Boolean/Object>
```
**fetchLeaderboard**

It gets a specified amount of entries from the database, ordered from higgest to lowest within the specified limit of entries.
```js
Levels.fetchLeaderboard(<GuildID - String>, <Limit - Integer>);
```
- Output:
```
Promise<Array [Objects]>
```
**computeLeaderboard** (**Updated recently!**)

It returns a new array of object that include level, xp, guild id, user id, leaderboard position, username and discriminator.
```js
Levels.computeLeaderboard(<Client - Discord.js Client>, <Leaderboard - fetchLeaderboard output>, <fetchUsers - boolean, disabled by default>);
```
- Output:
```
Promise<Array [Objects]>
```
**xpFor**

It returns a number that indicates amount of xp required to reach a level based on the input.
```js
Levels.xpFor(<TargetLevel - Integer>);
```
- Output:
```
Integer
```
