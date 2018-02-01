# Zamicol's Programming Style Guide
----------

**General Programming Styles**

Rules for syntax that can be applied to a wide variety of scripting and programming languages.

## General Rules

- Be consistent.
- Do your best to continue using the style in which a project was originally written.
- For languages like Go, use the standard tooling for formatting which would be go fmt in this case.
- Use tools where ever possible to format your code for you.  Automation FTW.
- If you still think it best to change the style of an existing project, try to make the style changes to the whole project.  Under the extraordinary circumstance that is not reasonably possible keep your style changes to limited to specific files and leave comments explaining your reasoning.  
- Don't be the cause of unneeded mixed styles.  
- When using a framework, an alternative style is permitted as long as there is a clear distinction where the framework ends and your work begins.  If this is not the case, your should continue to use the framework's style.  
- Long is better than wide.  

## Tabs and Spaces
One tab per indent level.  Tabs and **not spaces** should always be used for formatting and indentation.   Spaces are evil!

Spaces should only be used where tabs are totally useless.  
Tab is the character specifically intended for indentation.  Space is for separating words and sentences.  Spaces should only be used for indentation when it is not possible to use tabs.  

The standard tab size is 4 spaces.  Try to format your code in such a way this doesn’t matter.  If you are formatting your code where spaces matter, you are probably doing something wrong.

Use tools that automatically format your code for you when possible.

You should try to keep main blocks of code in a file flush, not indented, with the first column without any indentation.  It's okay to not indent after declaring a namespace or something similar.  


### Formatting
#### White Space
White space is usually good and should be used to make code more readable.  

Typically, one line between function/methods, one line in between blocks of code as desired.  It is also okay to use two line breaks between large blocks of code.  

### Column Size
80 characters when possible.  

#### Optional formatting
Braces and semicolons are required where optional.  

#### Functions/Methods, code blocks

Correct:

    if(true){
    	return true;
    }

Acceptable:

    if( true ){
        return true;
    }

Acceptable:

    if ( true ) { return true; }

Although discouraged, the opening brace of `if` statements, `loops`, and other blocks can be on it's own line. This must stay consistent throughout a project. Long statements can be word wrapped by using two indent levels.  

Correct:

    if(true){
    	return true;
    }else{
    	return false;
    }

Correct:

    if( thatIsTrue
			&& trueIsTrue
			&& thisIsTrue
			|| thisAndThat ){
        return true;
    } else {
	    return false;
    }

Correct:

    if(true){ return true; }

Acceptable:

    if(true)
    {
    	return true;
    }
    else
    {
    	return false;
    }

Acceptable:

    if(thatIsTrue
    	&& thisIsTrue
    	|| thisAndThat)
    {
        return true;
    }else{
    	return false;
    }

Wrong:

    if( thatIsTrue && trueIsTrue
      && thisIsTrue
      || thisAndThat ){
        return true;
    }

### Naming and Casing
- Like java, use camel case and upper camel case for variable naming.  
- Avoid underscores in code except when names are end user facing, like file names.  Underscores are also permitted when writing in all uppercase or the language is case insensitive (like PL SQL).  
- File names used in "asset" folders like images should be lower snake case.  
- Use lower snake case in URL's and anything filepath like.  
- **Never use dashes unless absolutely necessary.** Use underscores with lower snake case instead.  
- Never reuse names, even when cased differently. All things should be uniquely regardless of case.  

Examples:

**Wrong**

    var One = 1;
    var oNe = 1;
    var OnE = 1;
    https://example.com/billy-bob

**Correct**

    var i = 1;
    var gamePoints = 1;
    var newPersons = 1;
    https://example.com/billy_bob

### Casing
#### Casing for files and long name casing

**Casing** for should always be **lower snake case**.  Classes, and things like classes, should always be upper camel case (Pascal case) and begin with a capital letter.  If classes are saved to a file, the file should have the same name as the class.

Things like functions, methods, and variable names should be normal camel case and begin with a lowercase letter.

Acronyms should be treated as one word with only the first character capitalized.  

Constants and globals should be ALL CAPS and underscores should be used to break up words.  

Packages should be all lowercase with no underscores or dashes.  If names are long consider subpackages in a Go-like fashion.  

Avoid Hungarian notation and putting references to datatypes in names where possible.  This clutters up code.  https://en.wikipedia.org/wiki/Hungarian_notation

### Encoding
#### Line Endings
If at all possible, lines should end with the standard Unix **line feed** and not line feed plus carriage return.

#### File Encoding
Encoding should always be UTF-8 unless something else is required.  


### Documentation and Comments
#### Comments
Where permissible, try to use line comments and not block comments.  

Code comments should be in complete sentences and end with punctuation.  


## SQL Guide
### Database logic
When possible always program database logic into the database instead of application side.  


### Table and Column Naming and Casing
Don't use a prefix for table native columns.  For example, in a `users` table a `password` column should not be prefixed with table information.  Some sort of prefix may be ideal when referring to foreign keys.

Tables should be plural and native columns should be singular (see http://stackoverflow.com/a/338606/1923095 for a nice explanation).  The exception is for foreign keys, which should be plural to signify that they are a foreign key.  

Table names and columns are considered to be all in the same case.  Do no use camel casing and use underscores to separate words.  

Try to avoid putting too many tables in a single schema or database.  If a table “prefix” appears necessary to avoid confusion with like named tables, it it most likely ideal to split out the tables into many databases/schemas.  

The datatypes should not be included in names unless for documented technical reasons.

Avoid abbreviations.  If a well known acronym is not available and no other acronym is appropriate, an abbreviation probably isn't either.  Names should be descriptive but not too long.

Obviously, reserved words cannot be included in table or column names.  It it fine to have names that are like reserved words as table or columns names and is not bad practice.  

**Eample:** For a given table, “users”

Correct:

    id
    students_id
    username
    password
    created
    updated

Wrong:

    userPkId
    users_userName
    users_password
    stuId
    datetime2_created
    updatedtds


### Standard Column Names
 - **id** - System generated, auto incrementing integer primary key
 - **updated** - Datetime of the last update to the field.   
 - **created** - Datetime of when the record was created.  
