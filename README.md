Tfs2Trello
==========

A tool for syncing work item information from TFS to Trello (one way)

This is a C# console application written that syncs some of your work item information from Team Foundation Server to Trello. There is no data going from Trello to TFS.

WARNING: This tool will DELETE ALL cards in a board before starting to sync (happens on each restart) so if you have something valuable in your Trello board, please don't use it.

See config.toml for how to get started. These are the fields you need to specify:
- Iteration (TFS iteration)
- TrelloKey (see https://trello.com/1/appKey/generate)
- TrelloToken (see https://trello.com/docs/gettingstarted/index.html#getting-a-token-from-a-user)
- BoardId (end of URL on each Trello board)
- TfsUrl (TFS Team Project Collection URL)
- TfsProject (TFS Project Name)

A big thank you to Trello.Net, RestSharp, Json.Net and toml-net for making this SO much easier - https://github.com/detroitpro/Trello.net

For the time being, Trello list names are matched with TFS Work Item State names (Active, Resolved, Closed f.ex.). That means you will have to create Trello lists that correspond to the TFS states that are available on your project.

Fork Notes
----------
- The original code was adding the TFS Description as a Comment on the Trello Card, changed to save as Description
- As TFS uses HTML to format the description and Trello Markdown, I added a component (and some regular expression) to convert and clean-up unsupported codes.
- If a TFS state did not exist as a List the code will try to add to a list named "Unknown" if that also does not exist it will skip (show a console message) and continue to process items.

Marcelo Lv Cabral
