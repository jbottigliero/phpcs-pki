Punchkick Interactive's Coding Standard for PHP_CodeSniffer
===========================================================

This is the set of sniffs that should be used with [PHP_CodeSniffer](http://pear.php.net/PHP_CodeSniffer) for Punchkick Interactive projects.


Installation
-----------------------------------------------------------

* Install [PHP_CodeSniffer](http://pear.php.net/PHP_CodeSniffer) with `pear install PHP_CodeSniffer` (PHP_CodeSniffer 1.3 or later is required).
* Checkout this repository as `PKI` into the `PHP/CodeSniffer/Standards` directory (e.g. /usr/share/php/PHP/CodeSniffer/Standards/PKI)
* Use the coding standard with `phpcs --standard=PKI`.


phpMD / PHP CodeSniffer Netbeans Plugin
-----------------------------------------------------------

Netbeans PHP Plugin which provides violations detected by - PHP Mess Detector
(phpmd.org by Manuel Pichler) and - warnings / infos from PHP CodeSniffer
(http://pear.php.net/package/PHP_CodeSniffer/)
Website: https://sourceforge.net/projects/phpmdnb/
Plugin Files: http://sourceforge.net/projects/phpmdnb/files/nbm/



Example of How the PKI Sniff Can be Configured
-----------------------------------------------------------

```
$bash:  ls -la
drwxr-xr-x  13 root  wheel   442B Oct 31 00:13 ./
drwxr-xr-x  15 root  wheel   510B Jul 26 20:45 ../
-rw-r--r--   1 root  wheel    33K Jul 26 20:45 AbstractPatternSniff.php
-rw-r--r--   1 root  wheel   7.7K Jul 26 20:45 AbstractScopeSniff.php
-rw-r--r--   1 root  wheel   7.4K Jul 26 20:45 AbstractVariableSniff.php
drwxr-xr-x   5 root  wheel   170B Jul 26 20:45 Generic/
-rw-r--r--   1 root  wheel   1.1K Jul 26 20:45 IncorrectPatternException.php
drwxr-xr-x   4 root  wheel   136B Jul 26 20:45 MySource/
drwxr-xr-x   5 root  wheel   170B Jul 26 20:45 PEAR/
drwxr-xr-x   3 root  wheel   102B Jul 26 20:45 PHPCS/
lrwxr-xr-x   1 root  wheel    56B Oct 31 00:13 PKI@ -> /Applications/MAMP/vh/docroots/git_Punchkick - phpcs-pki
drwxr-xr-x   5 root  wheel   170B Jul 26 20:45 Squiz/
drwxr-xr-x   4 root  wheel   136B Jul 26 20:45 Zend/
$bash:
```


PHPCS Config Settings for Local Development
-----------------------------------------------------------

```
$bash: phpcs --config-show
Array
(
)
$bash: sudo phpcs --config-set tab-width 2
$bash: sudo phpcs --config-set error-severity 1
$bash: sudo phpcs --config-set warning-severity 8
$bash: sudo phpcs --config-set report_width 120
$bash: sudo phpcs --config-set standard PKI
$bash: sudo phpcs --config-set encoding utf-8
$bash: sudo phpcs --config-set extensions php
$bash: phpcs --config-show
Array
(
    [tab-width] => 2
    [error-severity] => 1
    [warning-severity] => 8
    [report_width] => 120
    [standard] => PKI
    [encoding] => utf-8
    [extensions] => php
)
$bash:
```



HOW TO DETECT ROUGUE SNIFFS THAT DON'T CONFORM TO OUR STANDARDS
---------------------------------------------------------------
####Step 1: 
`$bash: phpcs --standard=PKI -s AclResourceHelper.php`

```
FILE: ...croots/[...]/AclResourceHelper.php
------------------------------------------------------------------------------------------------------------------------
FOUND 2 ERROR(S) AFFECTING 1 LINE(S)
------------------------------------------------------------------------------------------------------------------------
 33 | ERROR | Multi-line function declaration not indented correctly; expected 2 spaces but found 48
    |       | (PEAR.Functions.FunctionDeclaration.Indent)
 33 | ERROR | There must be a single space between the closing parenthesis and the opening brace of a multi-line
    |       | function declaration; found newline (PEAR.Functions.FunctionDeclaration.NewlineBeforeOpenBrace)
------------------------------------------------------------------------------------------------------------------------
```

####Step 2:
Add exclude lines into `ruleset.xml`. e.g. 

```
<exclude name="PEAR.Functions.FunctionDeclaration.NewlineBeforeOpenBrace"/>
```