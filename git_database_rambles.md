### database when switching branches

When switching branches where you have been doing database work
it is a good idea to `rails db:schema:load` to make sure you get rid of any changes you had on the other branch.
It is a similar “I should do this when pulling / changing branches / etc” like we do `bundle install` and `yarn install`
Because the database doesn’t _know_ you changed branches and that other branch shouldn’t have `map_notes` in it.
If we don’t do this we run the risk of accidentally adding tables to the schema we don’t mean to.

------------------------------------------

commit database change at a repo where it's created
But do not necessarily commit the change to master. Do the merge when merge the entire branch when the branch is ready to be merged to master
