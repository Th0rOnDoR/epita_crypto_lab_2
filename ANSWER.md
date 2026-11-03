> ![NOTE] cat `secret.age.` How many times is the payload encrypted? What is duplicated per recipient? What exactly is in each recipient block? (You built the same thing by hand in Lab 1.)

3 times, one per person.


> ![NOTE] The file is deleted in HEAD. If you would have pushed, Who can still read the password?

The ones using a previous version

> ![NOTE] After filter-repo, is the password safe? What did you have to do first?

Might not be, we purged the local only, and we can't purge a remote.

> ![NOTE] What does git commit --no-verify do to your hook? Where else must the same check run?

