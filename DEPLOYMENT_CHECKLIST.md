# Love Triad - Deployment Checklist

## Files That Need to Be Uploaded to GitHub

### Core HTML Files
- ✅ Index.html (main page with all features)
- ✅ dashboard.html (user dashboard)
- ✅ auth.html (login/signup)
- ✅ topic-view.html
- ✅ All forum HTML files (ForumOYg.html, ForumOYn.html, etc.)
- ✅ HumanMolecule.htm

### CSS Files (CRITICAL - These style everything)
- ✅ styles.css (main styles)
- ✅ community-premium.css (community hub styles)
- ✅ auth-styles.css (authentication styles)

### JavaScript Files (CRITICAL - These make features work)
- ✅ script.js (main functionality + user auth state)
- ✅ community-functions.js (live sessions, meetups, video calls)
- ✅ community-live-updates.js (animated live updates)
- ✅ dashboard.js (dashboard functionality)
- ✅ auth.js (login/signup logic)

### Images
- ✅ LTlogo5trans.png
- ✅ All house images (OYg.jpg, OYn.jpg, YYg.jpg, YYn.jpg)
- ✅ Background images (creme4bg.gif, rainbar.gif)

## What Was Fixed

### Issue: Community Hub Features Not Working
**Problem:** The `user` variable in script.js was file-scoped (using `const`), so community-functions.js couldn't access it.

**Solution:** Changed script.js to make user globally accessible:
```javascript
window.user = JSON.parse(localStorage.getItem('lovetriad_user'));
const user = window.user;
```

## File Dependencies (What Links to What)

### Index.html loads:
1. styles.css (line 17)
2. community-premium.css (line 18)
3. community-live-updates.js (line 21)
4. script.js (line 1624)
5. community-functions.js (line 1625)

### dashboard.html loads:
1. styles.css
2. auth-styles.css
3. script.js
4. dashboard.js

### auth.html loads:
1. styles.css
2. auth-styles.css
3. auth.js

## Features in Index.html

### When NOT logged in:
- Preview widgets showing online members
- Hot discussions preview
- Live activity stream
- Community chat (locked with sign-in prompt)

### When logged in:
- Live video sessions with join functionality
- Upcoming meetups with RSVP
- Post composer
- Community feed
- Video call widget
- Live chat
- Quick actions

## How to Verify After Upload

1. Upload ALL files to GitHub
2. Visit your GitHub Pages URL
3. Test WITHOUT logging in:
   - Should see preview widgets
   - Should see "Sign In" button
   - Community features should show locked state
4. Test WITH logging in:
   - Click "Sign In" → Create account
   - Should redirect to dashboard
   - Go back to home → Community section should show full features
   - Try clicking "Go Live", "RSVP Now", "Post Comment"

## Common Issues

❌ **If community features don't work:**
- Check browser console (F12) for JavaScript errors
- Verify all .js files uploaded
- Clear browser cache (Ctrl+Shift+R)

❌ **If styling looks broken:**
- Verify all .css files uploaded
- Check that file names match exactly (case-sensitive)
- Clear browser cache

❌ **If login doesn't persist:**
- Check that auth.js is uploaded
- Verify localStorage is enabled in browser
- Check that dashboard.html exists

## Cache Busting

The CSS files use version parameters (?v=10). If you update CSS:
1. Change the version number in Index.html
2. Example: `styles.css?v=11`
3. This forces browsers to reload the new version
