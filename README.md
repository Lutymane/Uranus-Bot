# Discord Hack Week Bot 2019

![Main Banner](/banner.png)

# Uranus Discord Bot

Uranus - a simple moderation bot with a unique member search feature - queries

You may watch for the bot completion here:
https://github.com/LiteOnE/Uranus-Bot/projects/1

Author: LT#[]

---

## Search query syntax

A query is an expression with boolean operations

The syntax will appear somewhat familiar if you have some experience with programming

It contains of properties, values, flags, operators and brackets

### Properties

- `nickname`, `n` - Looks at user's nickname on server. If they don't have one, the search will be applied to username
- `username`, `u` - User's username
- `role`, `r` - Role applied to user on server
- `bot`, `b` - Whether or not member is a bot. If you want to match bots, then use `bot=1`, any other value will be considered FALSE - matching non bot members. This property **does not require any flags**

### Operators

- `|` - Or
- `&` - And

```
💡 Keep in mind that boolean rules work here and '&' will be executed the first and then '|'
But if you don't want that, you may use brackets
```

### Brackets

- `(` - Opening bracket
- `)` - Closing bracket

```
💡 You can use brackets to define execution order
For example a|b&c - b&c will be executed the first and only then a|
But you may want to execute a|b the first, so you need to use brackets like this: (a|b)&c
```

### Flags

- `!` - Inversed (`Not` operation)
- `*` - Partial matching (Contains, includes)
- `?` - Case sensitive (Because by default the bot uses case insensitive search)

```
💡 The flags should be entered after property name and before '=' sign,
which is used to split property name with flags from value to search
```

---

### An example command using query

### `$$ban role!=admin&role!=mod&n*=sas`

**Breakdown**

`$$` - Bot's prefix

`ban` - Command to be executed on matched members if any

`role!=admin&role!=mod` - Has neither of the roles **Admin** or **Mod**. By default all values are case insensitive, so that will also match **ADMIN**, **aDmIn** and etc. You may supply property with `?` flag to match the case

`n*=sas` - Has the word **sas** contained in the user's nickname. If they don't have one, then it will be applied to username. Also we used a shortcut `n` for `nickname` here

**Result**

The bot will ban every member that has **sas** in their name, while not having **Admin** or **Mod** role in any capitalization

### You can use @mention or snowflake ID as an argument as well

### `$$rn @fib`

`rn` - shortcut for `resetnickname`
### `$$warn 396787552775831552 don't nubasify server's members`

### Commands List

```
💡 [user(s)] means a command's argument is a query, @mention or snowflake
```
```
💡 [user(s) role] or similar means a commmand have multiple arguments, each one should
be separated by space(s)

Also you might want to close a query with grave accent symbol ` like this `role=sas`
```

- `q` - Print matched users \[user(s)]
- `ban`,`b` - Ban \[user(s)]
- `unban` - Unban. **Only @mention or snowflake is accepted for this command, for obvious reasons**
- `kick`, `k` - Kick \[user(s)]
- `unkick`, `uk` - Unkick \[user(s)]. Nah, just kidding, there is no such command :smile:
- `addrole`, `ar` - Add a role \[user(s) role]. Accepted @role or role ID as the third argument
- `removerole`, `rr` - Remove a specified role \[user(s) role]
- `help`, `h` - Print help. No arguments
- `warn`, `w` - Warn matched users in direct message \[user(s) message]. Third argument is a text - message
- `resetnickname`, `rn` - Reset nickname \[user(s)]

