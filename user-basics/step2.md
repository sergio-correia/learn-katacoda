# Setting the account password

User accounts are particularly useful because they require authentication.
Individuals must input a matching username and password to access a user account.

The `passwd` command is used to configure passwords. Calling it with no
arguments will default to changing the password for the account you are logged in
as. With root permission, `passwd` can be called with a name of another user
account to set their password.

Like with `useradd`, you must have root access to use this command. Set the password for the guest account you created in the previous step using the following command:

`passwd guest`{{execute T1}}

Type the password __rhel__ and press enter to set the password for this account.
Type the same password again to confirm it.

Here you use a four-character password for simplicity, but it is best practice to
select a more secure password. In fact, non-root users would be unable to use
the password __rhel__ for their account because it is too short and does not
contain a number or uppercase letter. Root users can bypass these guidelines if
they wish.

>_NOTE:_ When typing passwords on Linux no characters will show up. This can be confusing for some new users, but the password is still being typed.  

Validate the password by using the list (`-l`) option for the `chage` command:

`chage -l guest`{{execute T1}}

<pre class=file>
Last password change                                    : Jun 08, 2021
Password expires                                        : Sep 06, 2021
Password inactive                                       : Dec 05, 2021
Account expires                                         : never
Minimum number of days between password change          : 0
Maximum number of days between password change          : 90
Number of days of warning before password expires       : 7
</pre>

This outputs useful information about when the password was last changed, when
the password expires, and how long the user will have to change their password
before it becomes inactive.

>_NOTE:_ You can view this same information with the `passwd` command using various options, but `chage -l` provides it in a much more human-readable and concise format.

You can use the `passwd` command for many more actions, such as setting an
expiration date or locking users from logging in with their password. Check out
the Enable Sysadmin article [Managing Linux users with the passwd command](https://www.redhat.com/sysadmin/managing-users-passwd) for more information on these
actions.

The next step will demonstrate how to add users to groups on a system.
