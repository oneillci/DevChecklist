#Dev Checklist

##Things to check before code is 'complete'

###Client-side
1. Has javascript been unit tested?
1. All html forms (think POST) should have @Html.AntiForgeryToken()
1. All form headers should be driven from t_WebContent
1. CSS should be in css file, not inline
1. Submits that are expected to take time should display the spinning gif
1. All fields should have maxlength applied
1. JavaScript should not subscribe to any events at a global level - should always be scoped to a function definition
1. Test double-clicking of submit buttons
1. Test page behaviour with slow sql server responses

###Server-side
1. Have unit tests been written?
1. Code defensively -- assume all javascript logic/validation has been bypassed
1. Code defensively -- use Single/First OrDefault() and if null log it, then redirect instead of waiting for exception
1. All GET's that take parameters should cater for that parameter not being included
1. All POST actions should be decorated with [ValidateAntiForgeryToken]
1. POST actions should use PRG pattern (like Report an Issue). See http://en.wikipedia.org/wiki/Post/Redirect/Get
1. Methods should be small - refactor repeating code into methods
1. All possible logic should be contained in Domain Logic class rather than controller
1. Use enums instead of magic strings where possible
1. If can't use enums use const or readonly string variables
1. Actions that require you to be logged in should be decorated with [Authorize]
1. Action that return  JSON that require you to be logged in should be decorated with [AjaxAuthorize]
1. Check your local ELMAH log to see if your code is generating any errors that are being swallowed
1. DB columns should have sensible column lengths & indexes specified

###Database
1. All changes of database schemas are to be applied to database projects and and checked the in TFS
1. All changes of database schemas are to be applied to relevant staging tables in external and internal databases
1. All changes of database schemas are to be applied to OBC_MBC as well.
1. Change of schemas normally indicates new records are to be added to t_ads_dictionary table and rebuild of view table in SQL server for datasync processing
2. A new baseline of every database schema is required for every release

