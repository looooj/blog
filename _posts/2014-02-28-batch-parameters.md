---
layout: post
title: Using batch parameters
---
You can use batch parameters anywhere within a batch file to extract information about your environment settings.

Cmd.exe provides the batch parameter expansion variables %0 through %9. When you use batch parameters in a batch file, %0 is replaced by the batch file name, and %1 through %9 are replaced by the corresponding arguments that you type at the command line. To access arguments beyond %9, you need to use the shift command. For more information about the shift command, see Shift The %* batch parameter is a wildcard reference to all the arguments, not including %0, that are passed to the batch file.

For example, to copy the contents from Folder1 to Folder2, where %1 is replaced by the value Folder1 and %2 is replaced by the value Folder2, type the following in a batch file called Mybatch.bat:

     xcopy %1\*.* %2

To run the file, type:

     mybatch.bat C:\folder1 D:\folder2

This has the same effect as typing the following in the batch file:

     xcopy C:\folder1 \*.* D:\folder2
 
You can also use modifiers with batch parameters. Modifiers use current drive and directory information to expand the batch parameter as a partial or complete file or directory name. To use a modifier, type the percent (%) character followed by a tilde (~) character, and then type the appropriate modifier (that is, %~modifier).


The following table lists the modifiers you can use in expansion.

Modifier Description

    %~1  Expands %1 and removes any surrounding quotation marks ("").
    %~f1 Expands %1 to a fully qualified path name.
    %~d1 Expands %1 to a drive letter.
    %~p1 Expands %1 to a path.
    %~n1 Expands %1 to a file name.
    %~x1 Expands %1 to a file extension.
    %~s1 Expanded path contains short names only.
    %~a1 Expands %1 to file attributes.
    %~t1 Expands %1 to date and time of file.
    %~z1 Expands %1 to size of file.
    %~$PATH:1 Searches the directories listed in the PATH environment variable and expands %1 to the fully qualified name of the first one found. If the environment variable name is not defined or the file is not found, this modifier expands to the empty string.

The following table lists possible combinations of modifiers and qualifiers that you can use to get compound results.
Modifier	Description

    %~dp1 Expands %1 to a drive letter and path.
    %~nx1 Expands %1 to a file name and extension.
    %~dp$PATH:1 Searches the directories listed in the PATH environment variable for %1 and expands to the drive letter and path of the first one found.
    %~ftza1 Expands %1 to a dir-like output line.
    
##Note
In the previous examples, you can replace %1 and PATH with other batch parameter values.
The %* modifier is a unique modifier that represents all arguments passed in a batch file. You cannot use this modifier in combination with the %~ modifier. The %~ syntax must be terminated by a valid argument value.
You cannot manipulate batch parameters in the same manner that you can manipulate environment variables. You cannot search and replace values or examine substrings. However, you can assign the parameter to an environment variable, and then manipulate the environment variable.
