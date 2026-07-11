# Quick Start Guide

## 🚀 Get Started in 3 Steps

### Step 1: Choose Your Path

#### Path A: Local Use (Simplest)
```bash
# Download the file
# Double-click index.html
# Done! 🎉
```

#### Path B: Deploy Online (Share with Others)
See options below ↓

### Step 2: Customize (Optional)
1. Open `index.html` in text editor
2. Change child names (line 800)
3. Change colors (line 20)
4. Save and reload

### Step 3: Start Learning!
1. Select a child profile
2. Start with Lesson 1
3. Complete activities
4. Play games for review
5. Print worksheets for practice

---

## 🌐 Deployment Options

### Option 1: GitHub Pages (Best for Long-Term)

**Prerequisites:** GitHub account (free)

```bash
# 1. Create repository on GitHub.com
# Repository name: phonics-reading-platform
# Make it PUBLIC

# 2. In your local directory
cd phonics-reading-platform
git remote add origin https://github.com/YOUR_USERNAME/phonics-reading-platform.git
git push -u origin main

# 3. Enable GitHub Pages
# Go to: Settings → Pages
# Source: Deploy from branch main
# Save

# 4. Your URL (ready in 2-3 minutes)
# https://YOUR_USERNAME.github.io/phonics-reading-platform/
```

### Option 2: Netlify (Fastest Deploy)

**Prerequisites:** None (sign up during deploy)

```bash
# Method 1: Drag & Drop (30 seconds)
1. Go to https://app.netlify.com/drop
2. Drag index.html file
3. Get instant URL: https://random-name.netlify.app

# Method 2: CLI (if you want custom domain)
npm install -g netlify-cli
netlify deploy --prod
# Follow prompts
```

### Option 3: Vercel (Developer-Friendly)

**Prerequisites:** None (sign up during deploy)

```bash
# Install Vercel CLI
npm install -g vercel

# Deploy
vercel --prod
# Follow prompts

# Your URL: https://phonics-reading.vercel.app
```

### Option 4: Local Server (Testing)

**Option 4a: Python (Built-in on Mac/Linux)**
```bash
cd phonics-reading-platform
python3 -m http.server 8000
# Open: http://localhost:8000
```

**Option 4b: Node.js**
```bash
npm install -g http-server
cd phonics-reading-platform
http-server -p 8000
# Open: http://localhost:8000
```

**Option 4c: PHP**
```bash
cd phonics-reading-platform
php -S localhost:8000
# Open: http://localhost:8000
```

---

## ✅ Verification Checklist

After deployment, test these features:

- [ ] Home screen loads with 4 profiles
- [ ] Clicking profile shows lesson selector
- [ ] Lessons 1-26 visible (rest locked)
- [ ] Clicking Lesson 1 opens lesson view
- [ ] Letter slider shows letters A
- [ ] "Play Sound" button speaks letter
- [ ] Games load when clicked
- [ ] Videos embed properly
- [ ] Books page shows 6 resources
- [ ] Worksheets generate correctly
- [ ] "Complete Lesson" marks lesson done
- [ ] Progress saves after refresh
- [ ] Parent Dashboard shows stats
- [ ] Mobile view works (test on phone)
- [ ] Settings allows name changes

---

## 🎯 First-Time Setup Tips

### For Parents
1. **Customize Names:** Go to Settings and update child names
2. **Test Audio:** Click "Play Sound" in Lesson 1 to verify
3. **Bookmark:** Add site to home screen (mobile) or bookmarks
4. **Print Sample:** Test worksheet printing with Lesson 1
5. **Watch Video:** Try one video to ensure YouTube embeds work

### For Teachers
1. **Deploy to Class URL:** Use GitHub Pages or school hosting
2. **Test on School Network:** Verify YouTube isn't blocked
3. **Print Worksheets:** Generate samples for filing system
4. **Create QR Code:** Use qr-code-generator.com for easy access
5. **Share Instructions:** Give parents/students the URL

---

## 🔧 Common Issues & Fixes

### "Audio doesn't work"
**Fix:** Use Chrome or Edge browser (best Web Speech API support)

### "Progress disappeared after closing browser"
**Fix:** Don't use Private/Incognito mode (blocks LocalStorage)

### "Videos show error"
**Fix:** Check internet connection; YouTube may be blocked on school networks

### "GitHub Pages shows 404"
**Fix:** 
- Verify file is named `index.html`
- Wait 2-3 minutes after enabling Pages
- Check repository is PUBLIC
- Hard refresh (Ctrl+Shift+R)

### "Netlify deploy failed"
**Fix:** Make sure you're dragging `index.html` (not the whole folder)

---

## 📱 Mobile Setup

### Add to iPhone/iPad Home Screen
1. Open site in Safari
2. Tap Share button
3. Tap "Add to Home Screen"
4. Name it "Reading Lessons"
5. App icon now on home screen!

### Add to Android Home Screen
1. Open site in Chrome
2. Tap ⋮ menu
3. Tap "Add to Home screen"
4. Name it "Reading Lessons"
5. App icon now on home screen!

---

## 🎨 Quick Customization Examples

### Change to Blue Theme
Edit line 20-25:
```css
--primary-color: #2196F3;    /* Blue instead of green */
--secondary-color: #FF5722;  /* Red-orange */
--accent-color: #4CAF50;     /* Green */
```

### Unlock All Lessons (Remove Progressive Lock)
Edit line 950:
```javascript
const isLocked = false; // Changed from complex check
```

### Add 5th Child Profile
Edit line 800:
```javascript
{id: 5, name: 'Child 5', avatar: '👶', progress: {}}
```

---

## 🆘 Getting Help

1. **Read Full Docs:** [PHONICS_PLATFORM_README.md](PHONICS_PLATFORM_README.md)
2. **Check Deployment Guide:** [DEPLOYMENT_GUIDE.md](DEPLOYMENT_GUIDE.md)
3. **Open GitHub Issue:** Report bugs or ask questions
4. **Browser Console:** Press F12 to see error messages

---

## 🚀 Next Steps After Setup

### Week 1: Getting Familiar
- [ ] Complete Lesson 1 with your child
- [ ] Try 2-3 different games
- [ ] Watch one video together
- [ ] Print and complete one worksheet
- [ ] Check Parent Dashboard

### Week 2: Building Routine
- [ ] Set daily 15-minute reading time
- [ ] Complete 1-2 lessons per day
- [ ] Introduce one new game
- [ ] Read one decodable book together
- [ ] Review progress in dashboard

### Month 1: Tracking Progress
- [ ] Complete first 26 lessons (alphabet)
- [ ] Celebrate "Letter Master" certificate!
- [ ] Note challenging letters for review
- [ ] Keep printed worksheet portfolio
- [ ] Adjust pace based on child's comfort

---

**Ready to start? Open `index.html` and begin your reading journey! 📖✨**
