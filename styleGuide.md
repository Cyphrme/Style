#**Zamicol's Programming Style Guide**
----------

##**General Programming Styles**
-----------

This section covers syntax that can be applied to a wide variety of scripting and programming languages.

**General Rules:**

- #1 rule: Be consistent.
- Do your best to continue using the style in which a project was originally written. 
- For strongly opinionated styled languages, like Go, prioritize their style.  
- If you still think it best to change the style of an existing project, try to make the style changes to the whole project.  Under the extraordinary circumstance that is not reasonably possible keep your style changes to limited to specific files and leaves comments explaining your reasoning.  
- Don't be the cause of unneeded mixed styles.  
- When using a framework, using an alternative style is permitted as long as there is a clear distinction where the framework ends and your work begins.  



###Formatting
####White Space
White space is usually a good thing and should be used to make code more readable.  

Typically, two lines between function/methods, one line in between blocks of code as desired.  



####Optional formatting
Braces and semicolons are required where optional.  

####Tabs and Spaces
One tab per indent level.  Tabs and *not spaces* should always be used for formatting and indentation.   

Spaces should only be used where tabs are totally useless.  
Tab is the character specifically intended for indentation.  Space is for separating words and sentences.  Spaces should only be used for indentation when it is not possible to use tabs.  

The standard tab size is 4 spaces.  Try to format your code in such a way this doesn’t matter.  

####Functions/Methods, code blocks

Correct:

    if(true){
	    return true;
    }

Acceptable:

    if( true ){
	    return true;
	}

The opening brace of **If** statements and **loops** should *not* be on it's own line.  Long statements can be word wrapped by using two indent levels.  

Correct:

    if(true){
	    return true;
    }else{
	    return false;
    }

Correct:

    if(thatIsTrue && trueIsTrue
			&& thisIsTrue
			|| thisAndThat){
        return true;
    }else{
	    return false;
    }

Correct:

    if(true){ return true; }

Wrong:

    if(true)
    {
	    return true;
    }
    else
    {
	    return false;
    }

Also Wrong:

    if(thatIsTrue 
	    && thisIsTrue
	    || thisAndThat)
    {
        return true;
    }else{
	    return false;
    }


###Naming and Casing
Avoid underscores and dashes.  Underscores are only permitted when writing in all uppercase or the language is case insensitive (like PL SQL). Never use dashes unless absolutely necessary.  

Never reuse a name with different casing. All things should be uniquely named discounting casing.  

Wrong:

    var One = 1;
    var oNe = 1;
    var OnE = 1;

Correct:

    var i = 1;
    var gamePoints = 1;
    var newPersons = 1;

####Casing
**Casing** should always be **camel casing**.  Classes, and things like classes, should always be upper camel case (Pascal case) and begin with an upper capital letter.  If classes are saved to a file, the file should have the same name as the class.

Things like functions, methods, and variable names should be normal camel case and begin with a lowercase letter.  

Acronyms should be treated as one word with only the first character capitalized.  

Constants and Globals should be ALL CAPS and underscores should be used to break up words.  

Packages should be all lowercase with no underscores or dashes.  

Avoid Hungarian Notation, putting datatypes in names, where possible.  

###Encoding
####Line Endings
If at all possible, lines should end with the standard Unix **line feed** and not line feed and carriage return.

####File Encoding
Encoding should always be UTF-8 unless something else is required.  


###Documentation and Comments
####Comments
Where possible, try to use line comments and not block comments.  


##**SQL Guide**
###Database logic
When possible always program database logic into the database instead of the application.  



###Table and Column Naming and Casing
Don't use a prefix for table native columns.  For example, in a `users` table a `password` column should not be prefixed with table information.  Some sort of prefix may be ideal when referring to foreign keys.

Tables should be plural and native columns should be singular.  The exception is for foreign keys, which should be plural to signify that they are a foreign key.  

Table names and columns are considered to be all in the same case.  Do no use camel casing and use underscores to separate words.  

Try to avoid putting too many tables in a single schema or database.  If a table “prefix” is looking like it is necessary to avoid confusion with like named tables, it it most likely ideal to split out the tables into many databases/schemas.  

The column datatype should not be included in the column name unless for technical reasons.    

Avoid abbreviations.  If a well known acronym is not available and no other acronym is appropriate, an abbreviation probably isn't either.  Names should be descriptive but not too long.  

Of course reserved words cannot be included in table or column names.  It it fine to have names that are like reserved words as table or columns names.  This is not bad practice.  

For a given table, “users”
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


###Standard Column Names
 - **id** - System generated, auto incrementing integer primary key
 - **updated** - Datetime of the last update to the field.   
 - **created** - Datetime of when the record was created.  
 

