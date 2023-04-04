# picoCTF - Web/Java Code Analysis 
![](https://img.shields.io/badge/category-web-informational) ![](https://img.shields.io/badge/language-java-green)

BookShelf Pico, my premium online book-reading service. I believe that my website is super secure. I challenge you to prove me wrong by reading the 'Flag' book! Here are the credentials to get you started:

Username: "user"
Password: "user"

[Source Code](https://artifacts.picoctf.net/c/483/bookshelf-pico.zip)

---
# Solution
tldr Inspect the code for weakness, endpoints and form inputs. Update the user role to get the flag (Weak JWT)


## Important clues found
[ptrckstuns](https://github.com/ptrckstuns) also found some clues that helped solve the challenge

1. The provided user credentials has a `role` of "Free". It is required to have Admin Access to view the flag 
![Pasted image 20230319021928](https://user-images.githubusercontent.com/72879902/226131161-8dff7caa-c8f2-4622-a08e-93f8ed631e1b.png)

2. A `data.sql` containing the roles is also found under the `/src/main/resources` folder
![Pasted image 20230319023212](https://user-images.githubusercontent.com/72879902/226131186-91e1423f-86ca-4656-a4cc-19a3e77945f8.png)

3. The idea is to change the role to Admin using a post request. There was a `/users/pass` endpoint captured in burp when I try to change my password. So I tried to look for other endpoints
![Pasted image 20230319022458](https://user-images.githubusercontent.com/72879902/226131175-0d40a94d-93e0-4783-b800-2a798174e78c.png)

> `/users/role` seems the one to be used to update roles using a `PATCH`

4. Inspecting the `UpdateUserRoleRequest` properties shows that the request requires  an `id` and a `role`
![Pasted image 20230319022536](https://user-images.githubusercontent.com/72879902/226131192-2f91b991-e3ba-434f-b807-304153041d44.png)

5. Initialization of default users hints that there is already a `user` and `admin`  by default
![Pasted image 20230319023744](https://user-images.githubusercontent.com/72879902/226131199-afed5111-dea6-4524-91ee-ed0552eb5c7c.png)

6.  A secret generator for jwt which uses a hardcoded string `1234`
![Pasted image 20230319021503](https://user-images.githubusercontent.com/72879902/226131233-1ee55044-356d-4265-ac77-bdec55ac71f8.png)

## Updating the Role
1. Trying to update the role using a basic request using the token provided by the application
![Pasted image 20230319023634](https://user-images.githubusercontent.com/72879902/226131287-a9bddb38-b005-4084-b3a2-147b800c2246.png)

2. Observing the given JWT http://jwt.io/
![Pasted image 20230319024244](https://user-images.githubusercontent.com/72879902/226131283-6a83fd03-2550-471c-b06d-10fa2a59b9ed.png)

3. Changing the JWT (pretend as an Admin) using the information found during analysis 
![Pasted image 20230319024639](https://user-images.githubusercontent.com/72879902/226131299-09aa70dd-f45d-405c-a0b7-f298cae5ced7.png)
   Since the initialized `user` has the Id of `1` I figured the `admin` user has an Id of `2`

4. Submit the request
![image](https://user-images.githubusercontent.com/72879902/226133231-0561f1d3-aee0-444e-afaf-555d38327f20.png)

5. Login and Access the Flag 
![Pasted image 20230319025223](https://user-images.githubusercontent.com/72879902/226131307-c692fb34-a2ff-4d1d-b392-cfff51e9243e.png)

---

flag: `picoCTF{w34k_jwt_n0t_g00d_7745dc02}`


