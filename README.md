# Bloxlink Documentation
## Contents
* [Getting Started](#getting-started)
* [Nickname Templates](#nickname-templates)
* [Group Roles](#group-roles)
* [Permissions](#permissions)
* [Power Ups](#power-ups)
* [Command Usage](#command-usage)
* [Bloxlink Premium](#bloxlink-premium)

### Getting Started
The easiest way to setup Bloxlink is with the `!setup` command.  Check your Direct Messages after using the setup command.
Note: if you want to skip a setting and leave it as what it was before (or to its default value), say `skip` or `next`.
The command will walk you through the following steps:
		* _Would you like to link a ROBLOX group to this Discord server?_
			* If you want to link your group, specify the group ID here.  Linking your group unlocks group-specific commands, and enables the automatic giving of roles. A member’s rank will also show in the `!getinfo` command.
				* Default: 0 (no group)
		* _Would you like to change the Verified role name to something else?_
			* The verified role is the role users get when they link their Roblox account to their Discord account. 
				* Default: Verified
		* _Premium informational post_
		* _Would you like to automatically transfer your ROBLOX group ranks to Discord roles?_
			* This will create Discord roles that match your Roblox group (if you’ve provided a group id previously).
				* Options: merge, replace
					* Merge: NO Discord roles will be deleted. Group roles will be added right under your roles already there.
					* Replace: ALL Discord roles will be DELETED and REPLACED with the new group roles.
				* Default: None
		* _Would you like to set a nickname for new members that join your server?_
			* This will set a nickname for each member that joins the server. Refer to the [Nickname Templates](#nickname-templates) section for more information.
### Nickname Templates
The nickname template is a set of instructions that determines what nickname a person gets if they use a command that gives nicknames. In addition, if certain server features are enabled, the nickname will be applied when the person joins the server.
You *CANNOT* omit the {} for the templates.
The templates are:
```
{roblox-name} --> changes to their ROBLOX Username
{discord-name} --> changes to their Discord username
{discord-nick} --> used to reflect no nickname template if this is the only template
{roblox-id} --> changes to their ROBLOX ID
{group-rank} --> changes to their current rank in the linked group
{group-rank-id} --> replace id with your group ID. The person will get the group rank corresponding with the group id. Example: {group-rank-1337}
{clan-tag} --> allows the user to specify a clan-tag with !clantag
```
You can use multiple. For example: `{roblox-name} | {group-rank}` will output: `robloxian123 | HR` if their group rank is “HR”. Note: for `{group-rank}`, the group is taken directly from the “Main Group” (!setup).
*If you would like a user be allowed to change part of their nickname at will*, use the *{clan-tag}* nickname template; otherwise, their nickname will be reverted while using the normal functionality of the bot
If you want to have *no nickname template*, USE `{disable-nicknaming}`, as this will not apply a nickname to the user.
### Group Roles
There are 2 ways to tell Bloxlink to give your members roles.
#### Main Group:
	This is probably the easiest way to deliver group roles. If your group is linked via !setup, *and* there is a Discord role in your server that matches the member’s Group Roleset, then the user will get the role. Please note: roles will *only* be automatically created if done by !setup. There is a `!dynamicroles` command which will make group roles that are missing from the Discord server. By default, this is turned on.
#### Binds:
	Note: binds are more advanced, but offer more freedom for specifying who gets what role.
	To make a bind, use `!bind`. The command will ask for your Roblox Group ID, the name of a Discord role in your server, and a list of Roblox Group Rolesets that will get the role. You can call the command to get into the prompts (the bot will ask for the values), or you can do it with one go:
`!bind 123 | My Awesome Role | 1, 3, 5-10`
Take note of the last value.  Those numbers are Roleset IDs. Bind values MUST 100% MATCH the member’s roleset for that group for them to get the role. Example: a value of `1` will match everyone in that group with a roleset of `1`, not higher or lower. To account for a larger range, negate the number. Example: `-10` means everyone with Roleset 10 *and higher*. You can also specify a range: `1-3` means Rolesets `1, 2, 3`. Please note that there is a max on the amount of binds you can do. If you want to bind all ranks, then just use `!setup`, as that’s the easiest way to link your group. Binds are for when you want *verify specific* ranks to get a certain role.
### Permissions
Most administrative commands require the `Manage Server` permission. To grant a user the permission, make a new Discord role, and check `Manage Server`. Give it to the person; they will now be able to use administrative Bloxlink commands, such as the `!settings` command. Some commands require other permissions than Manage Server, though. Those commands will specify which permission the person needs to run it.

Note: it is possible to override this behavior with Magic Roles. See the #Magic-Roles section for more information.
### Power Ups
By default, Bloxlink doesn’t do much. Sure, you can use `!setup` and link your group, but what if you want Bloxlink to do things automatically?
*Power Ups* allow Bloxlink to verify users automatically, and do other actions.
Power ups must be activated by command toggles.
Current Power Ups:
		* !autoverify
			* Bloxlink will give the Verified role and update the member’s nickname on join, if they apply to the person.
		* !dynamicroles
			* Bloxlink will attempt to create missing group roles from your server. Note: this will create roles from the “Main Group” only, not from binds.
		* !autoroles
			* Bloxlink will give _all_ roles and binds that apply to the person on join. This is different from `!autoverify` that only gives the verified role and nickname. This is equivalent to the user manually running `!getrole`.
		* !persistroles (premium)
			* Bloxlink will update roles and nickname when a user starts typing, no command needed from them! This is very useful if you want to ensure active members in your server are always up-to-date in terms of roles and nicknames.
		* !grouplock (premium)
			* Bloxlink will kick anyone not in the Main Group. This is used if you want only group members to join your server. Before kicking the person, Bloxlink will DM them with the instructions on verifying and joining the group.
### Command Usage
To view the commands, use `!help`. The bot will list the usage for each command. Certain commands are based off *prompts*— aka the bot will ask you what argument you want to use for the command. Most of these prompts can be skipped with the pipe ` | ` character to aid in command efficiency. 
Example: `!somecommand arg1 | this is another arg | last arg here`
### Bloxlink Premium
Bloxlink premium allows you to supercharge your Bloxlink experience and efficiently manage your Roblox server members.
To see what premium offers, use the `!help` command and skip to the Premium category. 
You can buy premium a few ways:
	*  [Selly](https://selly.gg/u/bloxlink)
	*  [Patreon](https://patreon.com/bloxlink)
If you purchase premium from Selly, you’ll get a code delivered to your email. Redeem the code with `!redeem <code>` in a server you own.
If you purchase from Patreon, link Discord account to your Patreon account from your Patreon settings page. After this, you will automatically receive Bloxlink premium after 5 minutes.
### Magic Roles
Magic roles are ways to bypass certain Bloxlink restrictions. To create a Magic Role, create a new Discord role with the exact name as below, then give it to a person.

The magic roles are as follows:
	*  Bloxlink Bypass
		* Bloxlink will NOT update roles and nicknames for people with these roles.
	* Bloxlink Updater
		* Users with this role can run *!updateuser* on other people, as well as run *!verifyall*
	* Bloxlink Admin
		* Users with this role can use *any* Bloxlink command.