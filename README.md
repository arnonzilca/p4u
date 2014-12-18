p4u
===

A lighter approach to command line perforce (p4)

# installation
clone this repository and put the directory in your PATH.
> Note that the scripts use one another, so you'll need all of them to be reachable from your PATH.


## [p4-show](p4-show)

Shows the current status of the relevant client, the current pending & shelved changelists as well as the default changelist.

![image](https://cloud.githubusercontent.com/assets/4737096/3824370/576ba9d6-1d46-11e4-9728-81a2bb5ddfe7.png)

It can also show historical information of the current p4 client, and highlight reviewboard links and fixes.

![image](https://cloud.githubusercontent.com/assets/4737096/3751349/881ddf24-17fe-11e4-8d29-a20fb5c10fe1.png)

> Note that this script works a lot faster if [gnu-parallel][1] is installed.
> Moreover, Since this script is usually used daily - several times a day (at least by me),
> it is recommended to alias it to a shorter phrase (`p4p`, `pp` or even just `p`).
> Aliasing is also recommended for personalizing the script's configuration.
> (Helps permanently removing the colors, printing briefly always or printing verbosely always).


## [p4-switch-context](p4-switch-context)

Allows switching the current changelist you're working on by shelving everything arround and unshelving the requested changelist.

#### Say this is your current p4 state:

![image](https://cloud.githubusercontent.com/assets/4737096/3790299/32f6d0bc-1af8-11e4-9f48-9a9a41a20666.png)

#### And Now, you want to work on changelist #1237177

![image](https://cloud.githubusercontent.com/assets/4737096/4993321/9c6977e6-69b5-11e4-9dc4-9ddbe05d95ef.png)

#### After running [p4-switch-context](p4-switch-context) you're there:

![image](https://cloud.githubusercontent.com/assets/4737096/3790301/32f7e98e-1af8-11e4-8852-19d89f7d7afb.png)

Run [p4-switch-context](p4-switch-context) without passing a changelist number when you want to start fresh and store all your current work. Everything will be shelved, and all pending work will be reverted.

> You can also sync & resolve automatically after the switch is done (run with -h to see all the options).


## [p4-annotate](p4-annotate)


Improving 'p4 annotate' to annotate a specific line of a certain file.

It's helpful the most when combined with an editor.

For example, if you use vim you can add this command to your vimrc:

	command! Blame execute '!p4-annotate' . expand('%:p') . ' ' . line('.')


## [p4-delete-changelist](p4-delete-changelist)

Deletes a certain changelist overcoming a lot of p4 obstacles.

> Automatically Deletes shelve, Reverts files, removes fixes (also fixes hostname in case changelist was created on a different host than it's deleted).


## [p4-delete-client](p4-delete-client)

Deletes current p4 client completely - deletes the client on the p4 server and the local files.

> Automatically deletes all changeslists, reverts all files & makes Matrix references! :)


## [p4-untracked](p4-untracked)

Find untracked (unadded) files in a p4 directory.


## [p4-reshelve](p4-reshelve)

Just as it sounds - reshelves a shelved changelist by the current pending files (old shelve is deleted).


## [p4-unshelve](p4-unshelve)

Unshelves a changelist to itself by default (instead of p4 default unshelve to the 'Default changelist').


## [p4-revert-all-opened](p4-revert-all-opened)

Just as it sounds - Did a lot stuff you regret? revert everything (doesn't harm shelves).


## [p4-show-changelist](p4-show-changelist)

Pretty prints a changelist. It is used in [p4-show](p4-show) & [p4-annotate](p4-annotate).
> It's more of a scaffold script, but you can use it to automate pretty changelist printing yourself.


## [p4-help-functions](p4-help-functions)

This is an unrunnable file containting helper functions for other p4 scripts to source.


[1]: http://www.gnu.org/software/parallel/
