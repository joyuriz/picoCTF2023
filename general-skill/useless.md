# general-skill/useless
Write-up by: [ptrckstuns](https://github.com/ptrckstuns)

## Description
There's an interesting script in the user's home directory The work computer is running SSH. We've been given a script which performs some basic calculations, explore the script and find a flag.

Hostname: `saturn.picoctf.net` 
Port: `54040` 
Username: `picoplayer`
Password: `password`
`ssh picoplayer@saturn.picoctf.net -p 54040`

## Solution
1. SSH to the server.
2. List the files
    ![](/attachments/useless1.png)
3. Read useless file
    ![](/attachments/useless2.png)
4. Read manual
    ![](/attachments/useless3.png)


**Flag:** `picoCTF{us3l3ss_ch4ll3ng3_3xpl0it3d_4373}`