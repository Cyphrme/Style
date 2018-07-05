# Zamicol's Programming Style Guide

**General Programming Styles**

Rules for syntax that can be applied to a wide variety of scripting and programming languages.

## General Rules

- Be consistent.
- Write useful comments in abundance. When in doubt, write a comment.
- Do your best to continue using the style in which a project was originally written.
- Use standard formatting tooling where available. For example, Go has `go fmt` which formats code in a standard way across the language.
- Use tools where ever possible to format your code for you. Automate where possible.
- If you still think it best to change the style of an existing project, try to make the style changes to the whole project. Under the extraordinary circumstance that is not reasonably possible keep your style changes to limited to specific files and leave comments explaining your reasoning.
- Don't be the cause of unneeded mixed styles.
- When using a framework, an alternative style is permitted as long as there is a clear distinction where the framework ends and your work begins. If this is not the case, your should continue to use the framework's style.
- Long code is better than wide.

## Formatting

Use tools that automatically format your code when possible.

### Tabs, Spaces, and Indentation

One tab per indent level. **Tabs and not spaces** should **always** be used for formatting and indentation. Spaces are evil when used for formatting.

Spaces should only be used where tabs are totally useless or technically required.

Format your code in such a way spaces don't matter. If you are formatting your code so that spaces matter, you are probably doing something wrong.

- **The standard tab size is 4 spaces.** If spacing size is important to you, this is what you use. This is the industry standard.
- Tab size = 2 spaces is nice to write code in.
- Tab size = 8 is historically accurate, but not very useful in modern usage.

Try to keep main blocks of code flush and not indented. It's okay to not indent after declaring a namespace, package, inside HTML head tags, or something similar.

### White Space

- White space is usually good and should be used to make code more readable.
- Use one line space between function/methods and one line in between blocks of code as desired to organize code like English paragraphs.
- It is okay to use two line breaks between large blocks of code, for instance between functions.
- No white space at the end of lines is ideal.
- Use two spaces at the end of punctuation between sentences.

### Column Size

80 characters when possible.

#### Optional formatting

Braces and semicolons are required where optional.

### Functions/Methods, code blocks

Correct:

```
if(true){
    return true;
}
```

Correct:

```
if( true ){
    return true;
}
```

Acceptable:

```
if ( true ) { return true; }
```

Although discouraged, the opening brace of `if` statements, `loops`, and other blocks can be on it's own line. This must stay consistent throughout a project. Long statements can be word wrapped by using two indent levels.

Correct:

```
if(true){
    return true;
}else{
    return false;
}
```

Correct:

```
if( thatIsTrue
        && trueIsTrue
        && thisIsTrue
        || thisAndThat ){
    return true;
} else {
    return false;
}
```

Acceptable:

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

Acceptable:

```
if(thatIsTrue
    && thisIsTrue
    || thisAndThat)
{
    return true;
}else{
    return false;
}
```

Wrong:

```
if( thatIsTrue && trueIsTrue
  && thisIsTrue
  || thisAndThat ){
    return true;
}
```

## Naming and Casing

- Like Java, use camel case and for variable naming.
- Long file names should be lower snake case.
- Use lower snake case in URL's and anything file path like.
- File names used in "asset" folders like images and template files should use lower snake case.
- Avoid underscores in code except when names are end user facing, like file names. Underscores are also permitted when writing in all uppercase or the language is case insensitive (like PL SQL).
- Avoid capitalization unless technically necessary.
- Avoid pluralization unless technically necessary.
- **Never use dashes unless absolutely necessary.** Use underscores with lower snake case instead.
- Never reuse names, even when cased, spaced, or underscored differently. All things should be uniquely named regardless of case.
- Using abbreviations is okay, but single names are best. Both `image` and `img` would be okay, but be consistent project wide.

Examples:

**Wrong**

```
var One = 1;
var SSN = 1;
var GamePoints = 1;
var iPAD = 0;
https://example.com/billy-bob
```

**Correct**

```
var i = 1;
var ssn = 1;
var gamePoints = 1;
var thinkPad = 1;
https://example.com/billy_bob
```

### Casing

#### Casing for files and long name casing

**Casing** for should always be **lower snake case**. Classes, and things like classes, should always be upper camel case (Pascal case) and begin with a capital letter. If classes are saved to a file, the file should have the same name as the class.

Things like functions, methods, and variable names should be lower camel case.

Acronyms should be all upper or lower case, such as "ServeHTTP", "httpServe", "HTTPServe"; not "ServeHttp".

Constants and globals should be ALL CAPS and underscores should be used to break up words.

Packages should be all lowercase with no underscores or dashes. If names are long consider subpackages in a Go-like fashion using subdirectories to organize your code.

Avoid Hungarian notation and putting references to datatypes in names where possible. This clutters up code. <https://en.wikipedia.org/wiki/Hungarian_notation>

### Encoding

#### Line Endings

If at all possible, lines should end with the standard Unix **line feed** and not line feed plus carriage return.

#### File Encoding

Encoding should always be UTF-8 unless something else is required.

### Documentation

Every project should have a README, preferably a `README.md` at the root of the project. It's okay to use the README to link to an online wiki. It's often a good idea to include a README in every subdirectory used to manage project code.

Documentation closer to the code is a good idea. It's a bad idea to remove documentation from the code sections where it is relevant.

#### Comments

- As a general rule, more comments are better. Write code that is well documented. It's better to have large comment sections with small bit of code rather than large sections of code with minimal comments.
- Use line comments, such as `//`, and not block comments, such as `<!-- -->`, where possible. Most tools have key combinations to easily toggle line comments, like `ctrl + /`. Line comments are easier to manage. This includes long comment sections.
- Leave one space after line comment characters before content, For example, "// " or "# "
- Code comments should be in complete sentences and end with punctuation.
- Every file containing human written code should contain a comment, preferably at the beginning.
- Machine generated code should begin with a comment, and probably include, "DO NOT EDIT".
- Avoid commenting out code for later use. It's better to put code snippets that you'd like to save in their own file.
- Every function should have a comment. It's acceptable to include a single comment section for a group of helper functions.

## Project and Package Organization

- Use git.
- Have a clear entry point for programs, ideally in the root.
- Keep your root project directory clean. Exceptions:

  - Project is "wide" and there's no need for any depth.

- Don't have a lot of different files for different tools if possible. It's better to put things in subdirectories.

- Generally, if you have more than one of something on the top level, it should probably go in it's own directory.

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

### External Examples

Go web app project by Brad Fitzpatrick:

- <https://github.com/perkeep/perkeep>

## Images

Images kept in the same folder with different resolutions should end with the image size.

Example:

```
 kitty_128.png
 kitty_256.png
```

# Testing

**Golden values** are static test values used to compare against test results. This is distinct from a "golden path", also known as "happy path".

# SQL Guide

## Database logic

When possible always program database logic into the database instead of application side.

## Table and Column Naming and Casing

Don't use a prefix for table native columns. For example, in a `users` table a `password` column should not be prefixed with table information. Some sort of prefix may be ideal when referring to foreign keys.

Tables should be plural and native columns should be singular (see <http://stackoverflow.com/a/338606/1923095> for a nice explanation). The exception is for **foreign keys, which should be plural to signify that they are a foreign key.**

Table names and columns are considered to be all in the same case. Do no use camel casing. Use snake case (underscores) to separate words.

Try to avoid putting too many tables in a single schema or database. If a table "prefix" appears necessary to avoid confusion with like named tables, it it most likely ideal to split out the tables into many databases/schemas.

The datatypes should not be included in names unless for documented technical reasons.

Avoid abbreviations. If a well known acronym is not available and no other acronym is appropriate, an abbreviation probably isn't either. Names should be descriptive but not too long.

Obviously, reserved words cannot be included in table or column names. It is fine to have names that are like reserved words as table or columns names and is not bad practice.

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

## Standard Column Names

- **id** - System generated, auto incrementing integer primary key.
- **updated** - Datetime of the last update to the field.
- **created** - Datetime of when the record was created.



# Terminology
## Login
"Log in" is preferred over "log on" or "sign in".  The first successful message on ARPANET was "login".  "Log off" is preferred over "log out" or "sign out".  Your login is your credentials for log in.  
