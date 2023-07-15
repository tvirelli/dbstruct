# dbstruct
The class provides the ability to compare 2 database structure dumps and compile a set of SQL statements to update one database to make its structure identical to another.

This Class was originally written by Kirill Gerasimenko <ger.kirill@gmail.com>. However, it hasn't been updated since 2012. When I updated some of my projects using dbStruct.php to PHP 8 the class stopped working.

I couldn't immediately find the issue, so I posted reddit.com/r/PHPhelp/ (https://www.reddit.com/r/PHPhelp/comments/150g0ho/need_help_with_an_older_script_that_compares_2/). There a user named MrCosgrove2 found the problem.

As explained by Him:

Change
```
function dbStructcUpdater() {
$this->init();
}
```
to
```
function __construct() {
$this->init();
}
```
The reason that this needed changing is that back in the day the constructor method could be named the same as the class name so, because the class was named 'dbStructcUpdater' then the constructor class could also be named `dbStructcUpdater`. This changed and now the constructor method must always be __construct.
