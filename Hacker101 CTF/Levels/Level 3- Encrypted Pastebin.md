> 4 points - Hard difficulty, skills - Web, Crypto
> 

https://b781bd4d02d0f0cc901e8b2ae35a1818.ctf.hacker101.com/

---

# 11/6/2026

`#1 attempt`

IDOR

steps taken

1. Create a post
2. Change the post `id` to something else
3. Flag found

!image.png

`#2nd attempt`

SQL

Steps taken:

1. Open or create a post
2. Add (`'`) at the end of address bar
3. Click enter 

No flags. Sanitized to `%27`

<aside>
💡

Observation: The parameter of page id`id`s is `/?post=`

</aside>
