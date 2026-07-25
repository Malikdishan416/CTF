> 7 points - Easy difficulty
> 

[The level](https://fad4a3d96f05d3c1dbb75fe486895d4f.ctf.hacker101.com)

# 8/6/2026

#### First of all. I should familiarize the app.

**Sign up, create an account,**

1. What URLs are there? (Home, posts, profile, etc.)
- Adds up `/index.php?` to the URL after the first click
1. What happens when I create a public post vs. private post?
2. Can I see other users' posts?
3. What does the post URL look like? (`/post/1`, `/post?id=1`, etc.)

`#1 Attempt`

Try to test IDOR

Steps taken:

1. After signing in, open a post
2. Notice the `id` parameter in the address bar - opportunity to test IDOR
3. Replace the `id` value with an arbitrary number
4. Flag exposed

!image.png

`#2 attempt`

Steps taken:

Try to find an endpoint that shows my account id so I can access someone else's 

1. Click my profile
2. Notice the id is shown in address bar
3. Change it to `b`

Accessed to admin’s account!

!image.png

Unfortunately there's no new flag - the flag there was already claimed on first attempt

`#3 attempt`

Test SQL

Steps taken :

1. Open a page
2. Type single quote `(’)` at the end of URL

Unfortunately the application sanitized it and replaced it with “`%27`”

`#4 attempt`

Try to post an XSS

Steps taken: 

1. Click “write a new post”
2. Paste an XSS : `<script>alert(1)</script>`
3. Click create post 

Unfortunately it didn't work. But got an Idea!

Try with another XSS

Steps taken

1. Do the same with `<script>alert('XSS')</script>`

then `<img src=x onerror=alert(1)>` , then `<img src=x onerror=alert('XSS')>`

#### Unfortunately none of them worked but at least I got a conclusion that the application sanitizes XSS payloads so I won't test XSS further.

`#5 attempt`

Try to do the same but IDOR to another one’s `/page/edit` and then place the XSS there. Since mine didn't work,

1. Click edit post
2. IDOR to `id=1` - which means the edit page of the page which `id` is 1
3. Flag exposed

!image.png

`#6 attempt`

Try to intercept the `delete-post` request and do it on someone else's 

steps taken:

1. Go to home
2. Turn intercept on
3. Click a post
4. Replace the `page=view.php&id=3` in the starting line with  `page=home.php&message=Post%20deleted!`(its what appears on URL when a post is deleted)
5. Click forward, then turn intercept off

Unfortunately application doesn't let me delete posts. I did the same with repeater method it showed `200OK` but no flags nor post was deleted. 

#### Got another clue :

In the view page source of the post I placed `<script>alert(1)</script>` The XSS there was converted to a random string,

 I saw `&lt;script&gt;/alert(1)&lt;/script&gt;` (I had to type manually it didn't let me paste the exact thing) - This is **HTML encoding,** It's the the app converts `<` to `&lt;` and `>` to `&gt;`

I looked at some of the labs, There is a lab where I can un-sanitize the payload but I think only if the application sanitize it by adding string on the beginning, not mixed up like this. 

`#7 attempt`

Despite feeling ashamed I went to hints.

<aside>
💡

Flag3 -- Not Found
189 * 5

</aside>

So I figured the answer is 945 I 

- Just typed `/945` and nothing happened
- Noted the `index.php?page=view.php&id=` is the parameter to page IDs so I added 945

Flag exposed

!image.png

`#8 attempt`

The hint saying *"The person with username 'user' has a very easy password..."* 

The common passwords that come to my mind are 

- `password`
- `123456`
- `user`
- `admin`

Tried first one. flag exposed

!image.png

`#9 attempt`

Modified the `create-page` request by IDOR the `ID` parameter to admin’s 

(i think it works in by intercepting and modifying too)

Steps taken: 

1. Click create post
2. Locate the request in https history
3. Send to repeater
4. replace the value of `id` with 2 - it's admin’s post id number 
5. Click send and notice response shows `HTTP/2 302 Found` 
6. Search “Flag”’
7. Flag exposed

!image.png

# Completed CTF points that are enough to make me eligible for private programs
