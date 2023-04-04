# general-skill/Special
Write-up by: [ptrckstuns](https://github.com/ptrckstuns)

## Description
Don't power users get tired of making spelling mistakes in the shell? Not anymore! Enter Special, the Spell Checked Interface for Affecting Linux. Now, every word is properly spelled and capitalized... automatically and behind-the-scenes! Be the first to test Special in beta, and feel free to tell us all about how Special streamlines every development process that you face. When your co-workers see your amazing shell interface, just tell them: That's Special (TM)

## Solution
1. Commands work inside two quotes `" "` such as `"[command]"`
    
    ![](/attachments/special1.png)

2. List files but previous is not working. Need to bypass by adding another two quotes such as `" "ls" "` or `" "[command]" "`. 
    
    ![](/attachments/special2.png)

3. **blargh** is a directory. List the files inside that folder and read the flag such as `""ls"" 'blargh'`, `""cat"" 'blargh/flag.txt'` or `""[command]"" '[args]'`
    
    ![](/attachments/special3.png)

**Flag:** `picoCTF{5p311ch3ck_15_7h3_w0r57_0c61d335}`