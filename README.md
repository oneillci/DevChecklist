#Dev Checklist

##Things to check before code is 'complete'

###Client-side
1. Has javascript been unit tested?
1. All html <forms> should have @Html.AntiForgeryToken()
1. CSS should be in css file, not inline
1. Submits that are expected to take time should display the spinning gif
1. All fields should have maxlength applied
1. JavaScript should not subscribe to any events at a global level - should always be scoped to a function definition
1. Test double-clicking of submit buttons
1. Test page behaviour with slow sql server responses

###Server-side
1. Have unit tests been written?
1. Code defensively -- assume all javascript logic/validation has been bypassed
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
1. Have you added and checked in any database schema change?


