# Android-Java-Coding-Guidelines

Derived from

1) https://github.com/ustwo/android-coding-standards
2) https://source.android.com/setup/contribute/code-style
3) And some good to follow Rules 
4) What to include on GitIgnore / SVNIgnore


# Line Length

Stick within the 120 char line limit. Use line breaks to split up code according to the style guidelines


# Id names

Layout resource ids should use the following naming convention where possible:
<layout name>_<object type>_<object name>
    E.g.    
    home_listview_hotels
    hotel_item_imageview_star_rating


# Variable Declarations(General practice)

>Java best practices state "one declaration per line".
>Member Variable within the scope of class must be declared as:
    <m><objectname><objecttype>
    EX: mDisableAllSwitch
>Keep the scope of local variables to a minimum


#Don't catch generic exception

Not Recomended:

    try {
          someComplicatedIOFunction();        // may throw IOException
          someComplicatedParsingFunction();   // may throw ParsingException
          someComplicatedSecurityFunction();  // may throw SecurityException
          // phew, made it all the way
      } catch (Exception e) {                 // I'll just catch all exceptions
          handleError();                      // with one generic handler!
      }
      
It obscures the failure handling properties of your code, meaning if someone adds a new type of Exception in the code you're calling, the compiler won't help you realize you need to handle the error differently.

If Required:
Alternatives to catching generic Exception:

    Catch each exception separately as part of a multi-catch block, for example:

    try {
        ...
    } catch (ClassNotFoundException | NoSuchMethodException e) {
        ...
    }


# Don't use finalizers

>Finalizers are a way to have a chunk of code executed when an object is garbage collected. 
While they can be handy for doing cleanup (particularly of external resources), 
there are no guarantees as to when a finalizer will be called (or even that it will be called at all). 

# Order of import statements

>The ordering of import statements is:
1)Android imports
2)Imports from third parties (com, junit, net, org)
3)java and javax


# Spaces rules for indentation

>Use four (4) space indents for blocks and never tabs.
>Use eight (8) space indents for line wraps, including function calls and assignments. 


# Log sparingly

> [AOSP Link](https://source.android.com/setup/contribute/code-style#log-sparingly)


# Constants

Its always better to keep constants in a separate file declaring static variables for each of them to increase code read-ability.


# What to include on GitIgnore / SVNIgnore or what files to commit 

>Ignoring folders:
    .svn
    .idea
    .gradle
    Build (From root and from inside app directory/ Very important to ignore as this is generated in every build and will conflicts the diffs later)

>Ignore Files:
    .DS_Store (If MAC OSX)
    "local.properties" file
    "APP_NAME.iml"
    


