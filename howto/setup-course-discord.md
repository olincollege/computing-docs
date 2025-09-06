# How to set up a computing course Discord server

In this guide, we will walk through the process of setting up a course Discord
server in the style used at most computing courses at Olin.

There are many other ways to set up servers for this purpose, but this
specifically provides:

- A set of standardized roles and channels
- A reasonable set of permissions for the roles and channels above
- Automatic role assignment through the YAGPDB Discord bot

## Create the server

From the Discord app, click to add a server, then select "Create My Own".

When asked to "Tell Us More About Your Server", skip the question.

The server name is the full name of the course, followed by the semester and
year. For example, DSA Fall 2023 would be "Data Structures and Algorithms Fall
2023".

Select a picture for the server icon if one is available.

## Add the YAGPDB Discord bot

Go to https://yagpdb.xyz and access the Control Panel. You may be prompted to
sign into your Discord account.

Select the new server you created. There should be a plus symbol (+) to add the
bot to this server.

Use the following permissions:

- Manage Roles
- View Audit Log
- Send Messages
- Send Messages in Threads
- Manage Messages
- Embed Links
- Read Message History
- Add Reactions

## Create Roles

On the new Discord server, create the following roles and arrange them in the
order shown below:

- Instructor
- CA
- Member
- MechE
- ECE
- E:Bio
- E:C
- E:Design
- E:Robo
- E:Self
- E:Sust
- Olin
- Babson
- Wellesley

Make sure to "Click to Save Changes" after adding these roles.

## Set Up Role Commands

In the YAGPDB control panel, go to "Role commands" and select "Change settings
here". (It's okay that the section is shown in red.)

Create the following **groups**:

- Member
  - Mode: Standard
  - Requires roles: None selected
  - Ignore roles: None selected
- Major
  - Mode: Standard
  - Requires roles: Member
  - Ignore roles: None selected
- School
  - Mode: Standard
  - Requires roles: Member
  - Ignore roles: None selected

In the Member group tab, create the following role command:

- Member
  - Group: Member
  - Role: Member
  - Requires roles: None selected
  - Ignore roles: None selected

In the Major group tab, create the following role command:

- MechE
  - Group: Major
  - Role: MechE
  - Requires roles: None selected
  - Ignore roles: None selected

Some of the fields may be pre-populated with this information, or may fill in as
you type the name of the role command.

Then do the same for the other majors (ECE, E:Bio, E:C, E:Design, E:Robo,
E:Sust, and E:Self) using the same settings.

Create the relevant role commands for the School group and the roles within them
(Olin, Babson, Wellesley), using the same procedure as for the Major group.

## Creating Channels

Create the following categories and channels.

Start Here

- `#rules`

General

- `#announcements`
- `#ca-hours-info` (leave out if you have no CAs)
- `#get-roles`
- `#class-meetings-chat`
- `#course-feedback`
- `#request-one-on-one-help`

Q&A (private category with YAGPDB.xyz and Member having access)

- `#discord`
- `#canvas`
- `#computational-setup`
- `#zoom`
- Any other tools you might want to provide support for. As examples:
  - `#command-line`
  - `#git`
  - `#vscode`
  - `#python`

Teams (private category with YAGPDB.xyz, Instructor, and CA having access)

- `#instructors` (private channel with YAGPDB.xyz and Instructor having access)
- `#cas-only` (private channel with YAGPDB.xyz and CA having access)
- `#teaching-team`

Off-Topic (private category with YAGPDB.xyz and Member having access)

- `#quotes`
- `#memes`
- `#random`

Not Yet (private category with YAGPDB.xyz and Member having access)

- Any channels that you want to create now but not activate until later can go
  here.

Archived (private category with YAGPDB.xyz and Member having access, empty to
start)

Then, delete all other categories and channels.

## Enable Developer Mode

Go to User Settings -> Advanced (this is for your user, not a particular
server). Advanced is under the App Settings category within your Settings
sidebar.

Ensure that Developer Mode is checked.

## Set up Rules Channel

In the `#rules` channel, post the following message, **replacing the
term/year/course information as appropriate**:

```
Welcome to the Discord server for the (Fall/Spring) (Year) edition of (Course)!

⚠️ **Once you have read and understand these rules, please react with a 👍 to get access to the remainder of the channels visible to you.** ⚠️

Please note the following rules and guidelines:

1. Be kind to one another. We do not tolerate discriminatory or disparaging treatment based on someone's sex, race, religion, ethnicity, sexuality, gender identity, school, year, major, previous programming experience, etc.
2. Be appropriate. Offensive nicknames or profile pictures are not allowed. NSFW content or discussions are not allowed.
3. Be mindful of what you post. Messages will usually stay up for the duration of the course, and are typically visible to all students, CAs, and instructors.
4. Don't spoil the fun. We're all mainly here to learn, and posting answers or major hints to assignment problems will hinder others' learning.
5. Post in the appropriate channel. An explanation of each channel is below. Messages not in the right channel may be deleted without a response.
6. Stay on topic. Please keep messages relevant to the course, unless you are in an off-topic channel.

Violations of these rules may result in a temporary or permanent ban from the server.
```

Right-click this message and select "Copy Message ID".

Then, in the `#rules` channel, post the following message, pasting the Message
ID instead of `(message_id)`:

```
-rolemenu create Member -m (message_id)
```

You will be prompted to react with the appropriate emoji to get the role. Select
`:thumbsup:` (👍).

This should add a 👍 reaction to the rules message, and you should see a
notification that you're done setting up. You can then delete the messages
containing your rolemenu command and the bot's message.

Check that this works by reacting with a 👍 to the message. You should then get
the Member role.

## Set Up get-roles Channel

In the `#get-roles` channel, run the following command:

```
-rolemenu create Major
```

Another message will appear asking you to react with an emoji for each major,
one at a time. We recommend using the following emojis for each major:

- MechE: `:compression:`
- ECE: `:control_knobs:`
- E:Bio: `:microbe:`
- E:C: `:computer:`
- E:Design: `:ledger:`
- E:Robo: `:robot:`
- E:Sust: `:earth_americas:`
- E:Self: `:mag:`

You can check that this works by reacting and seeing if you get the major of
your choice.

Once this works, you can delete the rolemenu creation message and the completion
message.

Set up a role menu for the School group using a similar process. We recommend
using the following emojis:

- Olin: `:bird:`
- Babson: `:beaver:`
- Wellesley: `:blue_square:`

## Set Role Permissions

Be sure that the following permissions are set for certain roles.

Instructor:

- Administrator

CA:

- Create Invite
- Manage Channels
- Manage Nicknames
- Timeout Members
- Manage Messages
- Pin Messages
- Priority Speaker
- Mute Members
- Deafen Members
- Move Members

Member:

- View Channels
- Change Nickname
- Send Messages
- Send Messages in Threads
- Create Public Threads
- Create Private Threads
- Embed Links
- Attach Files
- Add Reactions
- Use External Emoji
- Use External Stickers
- Mention @everyone, @here, and All Roles
- Read Message History
- Send Voice Messages
- Create Polls
- Connect
- Speak
- Video
- Use Soundboard
- Use External Sound
- Use Voice Activity
- Set Voice Channel Status
- Use Application Commands
- Use Activities
- Use External Apps

## Get Invite Link

Create an invite link by going to the server menu and selecting "Invite people".
By default, the link expires in 7 days, but you can customize this. We recommend
setting the link to never expire and to have unlimited uses.

Copy this link, and send it out to the course instructors/CAs/students.
