## Lab 05

- Name: Pranav Ponugoti
- Email: ponugoti.16@wright.edu

## namechange Usage Guide

- The current script allows you to rename the filename as required.
- You need to pass the pattern/word to be replaced and word that has to replace the requested pattern and the filename whose name who wanted to change
- Here -f option corresponds to word/pattern to be found, -r option refers to word that has to be replaced.
- At last we pass the filename as argument for which we wanted to change the name.
### The following are the pre-requisites and steps to run the script
#### Pre-requisites: See that script is in executable mode
- If it is not in executable mode, copy the file to `/bin` folder and give execute permissions as follows : `sudo chmod u+x namechange`
- Now user will be able to run the script in any directory.
- If you want to run script only in single directory then execute step 1 command in respective directory.
#### How to run the script
1. For working of script `-h` can be used.
  * Command: `namechange -h`
  * Output: 
```
Usage: namechange -f find -r replace "string to modify"
-f The text to find in the filename
-r The replacement text for the new filename
```

2. Command syntax: `namechange -f <find-pattern> -r <replace-word> <filename>`
- Example: `namechange -f '\s' -r '-' 'hello world'` This changes `hello world` to `hello-world`
- Output: `Renamed hello world to hello-world`
- Example: `namechange -f 'act+' -r 'action' rapidactt`
- Output: `Renamed rapidactt to rapidaction`
- Example to replace a word: `namechange -f 'world' -r 'wsu' 'hello-world'`
- Output: `Renamed hello-world to hello-wsu`
- Example: If filename which is not present is given, then the following is the output
- Output:
    ```
    User must provide valid filename
    Usage: namechange -f find -r replace "string to modify"
    -f The text to find in the filename
    -r The replacement text for the new filename
    ```
3. If user gives any other option, it throws error as follows.
- Always provide the `namechange` followed by options `-f` and `-r` , their corresponding values and `filename` as argument and nothing else.
- Example: `namechange -f 'act+' -r 'action' -x 'ss' rapidactt` Here we gave extra option `-x`, then it shows usage of command and quits the execution.
- If anyother option is found, user can find following output:
    ```
    Usage: namechange -f find -r replace "string to modify"
    -f The text to find in the filename
    -r The replacement text for the new filename
    ```
### In simple terms to change a filename, you can use the command with provided option and replace pattern/word with ease


