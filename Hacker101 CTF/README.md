### H1-101 — HackerOne Learning CTF

Documenting my CTF completion journey!

# How to Find Flags in Hacker101 CTF

**Pro Tip**:
If stuck, use the **Hints** button on the challenge page.

1. **Explore Everything**
    - Click every button and link.
    - Visit every page.
    - Create accounts/items if possible.
2. **Tamper With Everything**
    - Change numbers in URLs (IDOR) — very common.
    - Add single quote ' at the end of parameters (SQLi).
    - Try XSS payloads in every input field (<script>alert(1)</script>).
    - Change HTTP methods (GET → POST).
3. **Check Source Code**
    - Right-click → View Page Source.
    - Look for hidden comments, file names, or flags.
    1. **Use Burp Suite**
    - Intercept all requests.
    - Look at every parameter being sent.
4. **Common Flag Locations**
    - In URLs (change ID)
    - In page source or comments
    - After creating/editing something
    - In responses from the server
