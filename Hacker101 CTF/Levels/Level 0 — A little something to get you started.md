**Challenge:** Blank page saying 'Welcome to level 0. Enjoy your stay.'

**Steps taken:**

1. Right clicked the page → View Page Source
2. Found background.png image referenced in the HTML
3. Navigated directly to `/background.png` in the URL bar
4. Found the flag string hidden in the image
5. Copied the full flag including ^FLAG^ and $FLAG$ markers
6. Submitted on HackerOne — accepted

**Lesson:** Flags are often hidden in plain sight — images, source code, metadata. Always check every asset referenced in the HTML.
