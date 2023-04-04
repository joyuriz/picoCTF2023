# general-skill/Specialer
Write-up by: [ptrckstuns](https://github.com/ptrckstuns)

## Description
Reception of Special has been cool to say the least. That's why we made an exclusive version of Special, called Secure Comprehensive Interface for Affecting Linux Empirically Rad, or just 'Specialer'. With Specialer, we really tried to remove the distractions from using a shell. Yes, we took out spell checker because of everybody's complaining. But we think you will be excited about our new, reduced feature set for keeping you focused on what needs it the most. Please start an instance to test your very own copy of Specialer.

Official Hint:
> "What programs do you have access to?"

## Solution
1. From the previous challenge `general-skill/Special`: `"[command]"`, `"[command]" '[args]'` and  still works but limited.
    
    ![](/attachments/specialer1.png)

2. Use `compgen` to list all available commands, built-ins, and keyworkds that is available to run.
    > Help/Tip from StackOverFlow

    ![](/attachments/specialer2.png)

    > Note: Above are available commands to run 

    ![](/attachments/specialer3.png)

    ![](/attachments/specialer4.png)

3. Find another way to list files and directories. Using `printf '%s\n' *` from Google.
    
    ![](/attachments/specialer5.png)
    > Check every directory if has a file named 'flag.txt'

4. Read all the text files per directory. Using these commands from [stackexchange](https://unix.stackexchange.com/questions/86321/how-can-i-display-the-contents-of-a-text-file-on-the-command-line)
    
    ```sh
    echo "$(<filename)"
    or
    printf "%s" "$(<filename)"
    ```
    > Proof that echo is working to read files.

    ![](/attachments/specialer6.png)


5. Flag is found in **ala/** directory using the bypassed command `""echo $(<kazam.txt)""`

    ![](/attachments/specialer7.png)


**Flag:** `picoCTF{y0u_d0n7_4ppr3c1473_wh47_w3r3_d01ng_h3r3_d5ef8b71}`
