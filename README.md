# Cyphr.me Programming Style Guide

**General Programming Styles**

General rules for syntax applied to a wide variety of scripting and programming
languages.

## General Rules

- Be consistent.
- Long code is better than wide code.
- Do your best to continue using the style in which a project was originally
  written. Don't be the cause of unneeded mixed styles.
- Clear code is better than comments.  When clear code is not possible write a
  comment, but don't be too verbose. If a junior developer wouldn't understand a
  code block, write a comment.  Don't assume expert knowledge.
- Projects should be documented with a README.md.  
- Use tool where ever possible for formatting and linting, for example, `go
  fmt`.  Automate where possible.
- If you still think it best to change the style of an existing project, try to
  make the style changes to the whole project. Under the extraordinary
  circumstance that is not reasonably possible keep your style changes to
  limited to specific files and leave comments explaining your reasoning.
- When using a framework, an alternative style is permitted as long as there is
  a clear distinction where the framework ends and your work begins. If this is
  not the case, your should continue to use the framework's style.

### Documentation
Every project should have a README, preferably a `README.md` at the root of the
project. It's okay to use the README to link to an online wiki. A README's may
be warranted in subdirectories as well.

Documentation closer to code is good. It's bad to remove documentation from the
code sections where it is relevant.


## Formatting

Use tools that automatically format your code when possible.

### Tabs, Spaces, and Indentation

One tab per indent level. Tabs and not spaces should be used for formatting and
indentation. Spaces are generally bad.  Spaces should only be used where tabs
are useless or technically required.

Format your code in such a way spaces don't matter. If you are formatting your
code so that spaces matter, you are probably doing something wrong.

**The standard tab size is 4 spaces.**

Try to keep main blocks of code flush and not indented. It's okay to not indent
after declaring a namespace, package, inside HTML head tags, or something
similar. Tab size of 8 spaces is historically accurate but not very useful in
modern usage.  Tab size of 2 spaces is nice to write code in.

### White Space

- White space is usually good and should be used to make code more readable.
- Use two line spaces between function/methods. 
- One line in between blocks of code as desired to organize code like English
  paragraphs.
- Two line spaces should denote large code breaks.
- No white space at the end of lines is ideal.
- Use two spaces at the end of punctuation between sentences.

### Column Size

80 characters when possible.

#### Optional formatting

Braces and semicolons are required where optional unless delimited by a new
line.  

### Functions/Methods, code blocks

Correct:
```
if(bv){
    return true
}
```

Correct:
```
if (bv) {return true}
```

Correct:
```
if(bv1 && bv2){
    return true
}else{
    return false
}
```

Correct:
```
if(thatIsTrue
  && trueIsTrue
  || thisAndThat ){
    return true
} else {
    return false
}
```

Wrong:
```
if( hatIsTrue && trueIsTrue
  && thisIsTrue){
    return true;
}
```

It is discouraged to have the opening brace of `if` statements, `loops`, and
other blocks can be on it's own line. 

Discouraged:
```
if(true)
{
    return true;
}
else
{
    return false;
}
```



## Variable Naming and Casing

- Ideally, narrowly scoped variables should have small names, ideally, single
  letters. 
- Like Java, use camel case for variable naming.
- Long file names should be lower snake case.
- Use lower snake case in URL's and anything file path like.
- File names used in "asset" like directories (like images and templates) should
  use lower snake case.
- Avoid underscores in code except when names are user facing, like file names.
  Underscores are also permitted when writing in all uppercase or the language
  is case insensitive (like PL SQL).
- Avoid capitalization unless technically necessary.
- Avoid pluralization unless the datastructure is plural.  (Object names should
  be singular, an array of objects should be plural).
- **Never use dashes unless required.** Use underscores with lower snake case
  instead.
- Don't reuse names, even when cased, spaced, or underscored differently. All
  things should be uniquely named regardless of case.  
- Using abbreviations is okay. Both `image` and `img` are okay, but be
  consistent project wide.
- Acronyms should be all upper or lower case, but not both.  

Examples:

**Wrong**

```
var One = 1;
var SSN = 1;
var GamePoints = 1;
var iPAD = 0;
https://example.com/billy-bob
func ServeHttp
```

**Correct**

```
var i = 1;
var ssn = 1;
var gamePoints = 1;
var thinkPad = 1;
https://example.com/billy_bob
func ServeHTTP
func httpServe
func HTTPServe
```

### Casing

#### Casing for files and long name casing

Use **lower snake case** for files. Classes, and things like classes, should
always be upper camel case (Pascal case) and begin with a capital letter. If
classes are saved to a file, the file should have the same name as the class.

Things like functions, methods, and variable names should be lower camel case.

Constants and/or globals may be be ALL CAPS and underscores should be used to
break up words.

Local package directories should be all lower snake case (e.g. coze_cli).
Github/other hosted repositories are upper CamelCase (e.g. CozeCLI).  Acronyms
should be in one case, all upper or lower.  For example, for Ed25519, "Ed" is
not an acronym while for CozeCLI "CLI" is an acronym.  

If names are long consider subpackages in a Go-like fashion using subdirectories
to organize your code.

Avoid [Hungarian notation](https://en.wikipedia.org/wiki/Hungarian_notation) and
references to types in typed languages.  For Javascript, use JSDoc for types.  



### Encoding

#### Line Endings

If at all possible, lines should end with the standard Unix **line feed** and
not line feed plus carriage return.

#### File Encoding

Encoding should always be UTF-8 unless something else is required.


#### Comments

- As a general rule, comments are good. Write code that clear and if needed well
  documented. Sometimes it's needed to have large comment sections with small
  bit of code.
- Use line comments, such as `//`, and not block comments, such as `<!-- -->`,
  where possible. Most tools have key combinations to easily toggle line
  comments, like `ctrl + /`. This includes long comment sections.
- Code comments should be in complete sentences and end with punctuation.
- Machine generated code should begin with a comment, and probably include,
  "MACHINE GENERATED. DO NOT EDIT. SEE [...]" with a reference to the editable
  source files.  
- Avoid commenting out code for later use. It's better to put code snippets that
  you'd like to save in their own file.
- Every function should have a comment. It's acceptable to include a single
  comment section for a group of helper functions.

## Project and Package Organization

- Use git.
- Have a clear entry point for programs, ideally in the root.
- Keep your root project directory clean. Exceptions:
  - Project is "wide" and there's no need for any depth.

- Don't have a lot of different files for different tools if possible. It's
  better to put things in subdirectories.

- Generally, if you have more than one of something on the top level, it should
  probably go in it's own directory.

Most projects should have the following at the top level.

```
  - .git/
  - LICENSE
  - README.MD
```

An example top level project directory.

```
  - .git/
  - img/
  - test/
  - LICENSE
  - README.md
```

## Images

Images kept in the same folder with different resolutions should end with the image size.

Example:

```
 kitty_128.png
 kitty_256.png
```
 
# Testing

**Golden values** are static test values used to compare against test results.
This is distinct from a "golden path", also known as "happy path".

# SQL Guide

## Database logic

When possible always program database logic into the database instead of application side.

## Table and Column Naming and Casing

Don't use a prefix for table native columns. For example, in a `users` table a
`password` column should not be prefixed with table information. Some sort of
prefix may be ideal when referring to foreign keys.

Tables should be plural and native columns should be singular (see
<http://stackoverflow.com/a/338606/1923095> for a nice explanation). The
exception is for **foreign keys, which should be plural to signify that they are
a foreign key.**

Table names and columns are considered to be all in the same case. Do no use
camel casing. Use lower snake case (underscores) to separate words.

Try to avoid putting too many tables in a single schema or database. If a table
"prefix" appears necessary to avoid confusion with like named tables, it it most
likely ideal to split out the tables into many databases/schemas.

Data types should not be included in names unless for documented technical
reasons.

Avoid abbreviations. If a well known acronym is not available and no other
acronym is appropriate, an abbreviation probably isn't either. Names should be
descriptive but not too long.

Obviously, reserved words cannot be included in table or column names. It is
fine to have names that are like reserved words as table or columns names and is
not bad practice.

**Example:** For a given table, "users"

Correct:

```
id
student_id
username
password
created
updated
```

Wrong:

```
userPkId
users_userName
users_password
stuId
datetime2_created
updatedtds
```

Table names like "user_address" are okay for **junctions tables**.

## Standard Column Names

- **id** - Primary key.  Serial integer or random string.  
- time or created - Datetime of when the record was created.  Ideally Unix time.  
- updated - Datetime of the last update to the field.


# Terminology
## Login
"Log in" is preferred over "log on" or "sign in".  The first successful message
on ARPANET was "login".  "Log off" is preferred over "log out" or "sign out".
Your login is your credentials for log in.  


# Javascript
General:
- Omit ending `;`.  As of newer versions, it is not needed. 
- Exported Javascript functions variables should be JS doc'ed.  Most functions
  and types should be JS doc'ed.
- Non-HTML javascript variables should be defined by JSDoc and not denote types.
- Use lower camelCase for non-exported Javascript variables and upper CamelCase
  for exported variables.

## HTML elements selected into JS variables
HTML ID's should be lower camelCase.  

For these HTML elements, append the following to ID's and names.  For example,
`homeBtn` or `nameInput`.  After selecting the HTML element into a Javascript
variable, the Javascript variable name should match the HTML ID.  

```
- Elem      HTML Element
- Btn       HTML Button
- Input     HTML Input and Text Area
- Chk       HTML Checkbox
- Select    HTML Select
- Modal     Modal (Like Bootstrap Modal)
- Tmpl      HTML template (Pre-cloned, post-clone can be named whatever)
```

In lieu on "Elem", specific HTML tag, like "Div" or "Li", may be used.  

## JS Doc
JS Doc has many bugs.  We document them as we go in `typedef.js`

Use lower case names for Javascript build in types.  Don't use preceding ` * `
on lines.  It is excessively silly to use line escaping for block comments.  We
prefer using the function name as the first word in the function documentation
as is convention in Go.  

### Example JS Doc

```js
export { Bob }

/**
Bob creates a bob.  
@returns {void}
*/
function Bob(){
	...
}


/**
isEmpty is a helper function to determine if thing is empty. 
@param   {any}     thing    Thing you wish was empty.  
@returns {boolean}          Boolean.  
*/
function isEmpty(thing) {
	...
}
```

