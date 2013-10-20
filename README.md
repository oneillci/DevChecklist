#Dev Checklist

##Things to check before code is 'complete'

###Client-side
1. Has javascript been unit tested?
1. Test page in various browsers (support back to IE8) for UI bugs
1. All html forms (think POST) should have `@Html.AntiForgeryToken()`
1. All form headers should be driven from `t_WebContent`
1. CSS should be in css file, not inline
1. To add red asterisks to required fields use the following (this utilises our :before pseudo selector):
```
<div class="label-left required">							
    @Html.LabelFor(m => m.FieldName)
</div>
```
1. Submits that are expected to take time should display the spinning gif
1. All fields should have `maxlength` applied (expecially those with Regex)
1. JavaScript should not subscribe to any events at a global level - should always be scoped to a function definition
1. Test double-clicking of submit buttons
1. Test page behaviour with slow sql server responses
1. Check page against [webdevchecklist.com](http://webdevchecklist.com) (install chrome extension)
1. Achieve good score in Google PageSpeed (install chrome extension)
1. Achieve good score in Yahoo! YSlow (install chrome extension)

###Server-side
1. Have unit tests been written?
1. Code defensively -- assume all javascript logic/validation has been bypassed
1. Code defensively -- use `FirstOrDefault` or `SingleOrDefault()` and if null log it, then redirect instead of waiting for exception
1. All GET's that take parameters should cater for that parameter not being included
1. All POST actions should be decorated with `[ValidateAntiForgeryToken]`
1. POST actions should use PRG pattern (like Report an Issue). See [http://en.wikipedia.org/wiki/Post/Redirect/Get](http://en.wikipedia.org/wiki/Post/Redirect/Get)
1. Methods should be small - refactor repeating code into methods
1. All possible logic should be contained in Domain Logic class rather than controller
1. Use `enum` instead of magic strings where possible
1. If can't use enums use const or readonly string variables
1. Actions that require you to be logged in should be decorated with ```[Authorize]```
1. Action that return  JSON that require you to be logged in should be decorated with ```[AjaxAuthorize]```
1. Check your local ELMAH log to see if your code is generating any errors that are being swallowed
1. DB columns should have sensible column lengths & indexes specified
1. Mitigate querystring tampering. If loading data based on a querystring parameter, ensure that the logged on user has is the owner of the the requested data 

##WCAG
1. Run the Squiz labs html code sniffer on each page and fix errors. [http://squizlabs.github.io/HTML_CodeSniffer/](http://squizlabs.github.io/HTML_CodeSniffer/) - copy bookmarklet to bookmark bar in Chrome

###Database
1. All changes of database schemas are to be applied to database projects and and checked the in TFS
1. All changes of database schemas are to be applied to relevant staging tables in external and internal databases
1. All changes of database schemas are to be applied to OBC_MBC as well.
1. Change of schemas normally indicates new records are to be added to `t_ads_dictionary` table and rebuild of view table in SQL server for datasync processing
2. A new baseline of every database schema is required for every release

