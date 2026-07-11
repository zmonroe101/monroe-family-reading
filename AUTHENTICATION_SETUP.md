# 🔐 Authentication & Security Setup Guide

## Overview
The phonics platform now includes a simple but effective authentication system designed for families. All credentials are stored locally in the browser (localStorage) for privacy and simplicity.

---

## 🔑 Security Features

### 1. **Family Passcode (Required)**
- **4-digit PIN** protecting access to the entire platform
- Set on **first visit**
- Remembered on the same device (session persistence)
- Required after logout or browser data clearing

### 2. **Kid PINs (Optional)**
- **Individual 4-digit PINs** for each child profile
- Prevents siblings from accessing each other's progress
- Set per-profile in Settings
- Can be added/changed/removed anytime

### 3. **Parent Dashboard PIN (Optional)**
- Separate PIN for accessing parent dashboard and settings
- *(Future enhancement - not in current version)*

### 4. **Session Persistence**
- Once logged in, device remembers you
- No need to re-enter passcode unless:
  - You click Logout
  - Browser data/localStorage is cleared
  - Different device/browser used

---

## 📱 First-Time Setup

### Step 1: Set Family Passcode
1. Open `index.html` in browser
2. You'll see the **login screen** with a numpad
3. Enter a **4-digit PIN** (e.g., `1234`)
4. Click **Enter**
5. The app will confirm: *"Family passcode set! Remember this: 1234"*
6. **Write down your passcode** somewhere safe!

### Step 2: (Optional) Set Kid PINs
1. From the profile selection screen, click **⚙️ Settings**
2. Scroll to **🔐 Security Settings**
3. Click **🔑 Manage PINs**
4. For each child:
   - Click **Set PIN** button
   - Enter a 4-digit PIN they can remember (e.g., `2468`)
   - Confirm the PIN
5. Now that child will need their PIN to access their profile

---

## 🚪 Daily Use

### Logging In
1. Open the app
2. Enter your **family passcode** using the numpad
3. Click **Enter**
4. Select a child profile:
   - **No PIN**: Goes straight to lessons
   - **Has PIN**: Shows numpad to enter kid's PIN

### Logging Out
- Click the **🚪 Logout** button (visible on every screen)
- Requires re-entering family passcode to get back in

---

## 🔄 Changing Credentials

### Change Family Passcode
1. Go to **⚙️ Settings**
2. Scroll to **⚠️ Danger Zone**
3. Click **🔄 Change Family Passcode**
4. Enter **current passcode**
5. Enter **new passcode** (4 digits)
6. Confirm new passcode
7. Done! ✅

### Change Kid PIN
1. Go to **⚙️ Settings**
2. Click **🔑 Manage PINs**
3. Find the child's card
4. Click **Change PIN**
5. Enter new 4-digit PIN
6. Confirm PIN
7. Done! ✅

### Remove Kid PIN
1. Go to **⚙️ Settings**
2. Click **🔑 Manage PINs**
3. Find the child's card
4. Click **Remove PIN**
5. Confirm removal
6. That profile is now accessible without a PIN ✅

---

## 🔒 Security Best Practices

### ✅ DO:
- **Choose memorable PINs** kids can remember (e.g., `1111`, `2222`, their age repeated)
- **Write down the family passcode** in a safe place (not on the device)
- **Logout when done** if sharing the device with others
- **Use different PINs** for each child to prevent guessing

### ❌ DON'T:
- **Share your passcode** with people outside your family
- **Use birthdates** or easily guessable PINs if privacy is important
- **Forget to logout** on shared/public devices
- **Clear browser data** without knowing your passcodes (you'll need to re-enter)

---

## 🆘 Troubleshooting

### "I forgot my family passcode!"
**Solution:**
1. Open browser developer console (F12)
2. Go to **Application** → **Local Storage**
3. Find `phonicsAuthState`
4. Click **Delete**
5. Refresh the page
6. You can now set a **new passcode**
7. ⚠️ **WARNING:** This does NOT delete progress data, but you'll lose any kid PINs set

### "I forgot my kid's PIN!"
**Solution:**
1. Go to **⚙️ Settings**
2. Click **🔑 Manage PINs**
3. Find the child
4. Click **Remove PIN** (requires family passcode)
5. Optionally set a new PIN they can remember

### "The app logs me out constantly"
**Cause:** Browser is clearing localStorage automatically.

**Solutions:**
- Check browser privacy settings (don't auto-clear on exit)
- Disable "private/incognito mode" (it clears data on close)
- Check if browser extensions are clearing storage
- Try a different browser (Chrome/Edge recommended)

### "Logout button not showing"
**Cause:** JavaScript error or screen not loading correctly.

**Solutions:**
1. Hard refresh: **Ctrl+Shift+R** (PC) or **Cmd+Shift+R** (Mac)
2. Clear browser cache
3. Check browser console for errors (F12)

---

## 🌐 Sharing With Others

### Hosting on GitHub Pages / Netlify / Vercel
If you deploy this to a public URL, **anyone with the link** can access the login screen.

**Security measures in place:**
- ✅ Family passcode prevents unauthorized access
- ✅ Each device must enter the passcode (not shared across devices)
- ✅ No server-side storage - all data stays in browser

**Privacy consideration:**
- This is **not enterprise-grade security** - it's designed for family use
- Data is stored in browser localStorage (cleartext, not encrypted)
- If someone has physical access to the device + browser dev tools, they can see/modify data
- **For family use, this is fine.** For sensitive data, use a proper authentication service.

---

## 📊 Technical Details

### Where Data is Stored
All authentication data is stored in **browser localStorage**:

```javascript
// Family passcode and login state
localStorage.setItem('phonicsAuthState', JSON.stringify({
    isLoggedIn: true,
    familyPasscode: "1234",
    parentPin: null
}));

// Profile names, kid PINs, and progress
localStorage.setItem('phonicsAppState', JSON.stringify({
    profiles: [
        {id: 1, name: 'Emma', pin: '2468', progress: {...}},
        {id: 2, name: 'Liam', pin: null, progress: {...}},
        ...
    ]
}));
```

### Session Flow
```
1. Page loads → Check localStorage for 'phonicsAuthState'
2. If isLoggedIn === true → Go to profile selection
3. If isLoggedIn === false → Show login screen
4. User enters passcode → Verify against stored value
5. If correct → Set isLoggedIn = true, show profiles
6. User clicks profile with PIN → Show kid PIN screen
7. User enters kid PIN → Verify, then enter lessons
8. User clicks Logout → Set isLoggedIn = false, back to login
```

---

## 🎯 Recommended Configurations

### **For Young Kids (Ages 4-6)**
- **Family Passcode:** Simple, like `1111` or `1234`
- **Kid PINs:** Not needed (they can't read yet to navigate alone)
- **Logout:** Leave logged in on dedicated tablet

### **For Older Kids (Ages 7-10)**
- **Family Passcode:** Medium security, like `2580` or `1379`
- **Kid PINs:** Set for each child (simple: `1234`, `2345`, `3456`, `4567`)
- **Logout:** Use if device is shared with siblings

### **For Families with Multiple Devices**
- **Same Passcode:** Use same family passcode on all devices for consistency
- **Different PINs:** Let each kid set their own PIN (they'll remember it better)
- **Sync Warning:** Progress does NOT sync between devices (each device is independent)

---

## 🚀 Quick Reference

| Action | Steps |
|--------|-------|
| **First login** | Enter 4-digit PIN → Set it as family passcode |
| **Daily login** | Enter family passcode → Select profile → Enter kid PIN (if set) |
| **Logout** | Click 🚪 Logout button (top right) |
| **Change family passcode** | Settings → Danger Zone → Change Family Passcode |
| **Set kid PIN** | Settings → Manage PINs → Set PIN for child |
| **Remove kid PIN** | Settings → Manage PINs → Remove PIN for child |
| **Reset everything** | F12 → Application → Local Storage → Delete all |

---

## ✅ Security Checklist

Before deploying for your family:
- [ ] Test login flow on desktop browser
- [ ] Test login flow on mobile (iOS Safari, Chrome)
- [ ] Verify logout works on all screens
- [ ] Set memorable family passcode
- [ ] Optionally set kid PINs
- [ ] Write down all passcodes in safe place
- [ ] Test "forgot passcode" recovery procedure
- [ ] Confirm session persists after closing/reopening browser
- [ ] Verify data doesn't leak between browser profiles

---

## 📞 Support

If you encounter issues:
1. Check the **Troubleshooting** section above
2. Test in a different browser (Chrome recommended)
3. Open browser console (F12) to see error messages
4. Clear all localStorage and start fresh if needed

---

**Remember:** This authentication is designed for family use, not high-security applications. It prevents casual access but is not cryptographically secure. For families, it's perfect! 🎉
