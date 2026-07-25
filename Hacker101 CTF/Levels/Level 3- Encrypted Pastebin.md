> 4 points - Hard difficulty, skills - Web, Crypto
> 

---

# 11/6/2026

`#1 attempt`

IDOR

steps taken

1. Create a post
2. Change the post `id` to something else
3. Flag found

<img width="762" height="116" alt="image" src="https://github.com/user-attachments/assets/376be5f7-9837-48fc-abb4-37e463d3a877" />

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
