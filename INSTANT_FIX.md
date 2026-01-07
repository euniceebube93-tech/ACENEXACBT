# INSTANT FIX - "Failed to Fetch" Error

## The Error
```
Failed to fetch
Backend may be unreachable
```

## The Cause
Your **backend is not running**.

## The Fix (60 Seconds)

### Step 1: Open Terminal
```bash
npm start
```

### Step 2: Wait for This Message
```
Server running on port 5000
```

### Step 3: Go to Browser
- Open: http://localhost:5173
- Try adding subject again
- ✓ Should work now!

---

## That's It!

**Your backend MUST be running for ANY API calls to work.**

If you see **"Server running on port 5000"**, your backend is ready.

### Keep Backend Running
Leave that terminal open while you use the app.

### To Stop Backend
Press `Ctrl+C` in the terminal

---

## If It Still Fails

### Check 1: Is Backend REALLY Running?
Terminal should show:
```
Server running on port 5000
```

If you see an error instead, read it carefully. Common errors:
- "Port 5000 already in use" → Stop other process or use different port
- "Cannot find module" → Run `npm install` first

### Check 2: Is Frontend on Right URL?
Open: http://localhost:5173 (not 5000, not your IP address)

### Check 3: Check Browser Console
1. Press F12 in browser
2. Go to Console tab
3. Try adding subject
4. Look for error message
5. It will tell you what's wrong

---

## Browser Console Error Examples

### You See:
```
[API] GET http://localhost:5000/api/subjects
[API] FAILED TO FETCH http://localhost:5000 - Backend not running
```

**Fix:** Run `npm start`

### You See:
```
[API] GET http://localhost:5000/api/subjects
[API] ✓ GET http://localhost:5000/api/subjects
```

**This is good!** Backend is working.

---

## Two Terminals Required

### Terminal 1 (Backend)
```bash
npm start
```
Leave this running. You'll see:
```
Server running on port 5000
```

### Terminal 2 (Frontend)
```bash
npm run dev
```
This is where you see:
```
Local: http://localhost:5173
```

**Both must be running for full functionality.**

---

## Quick Checklist
- [ ] Terminal 1: `npm start` is running
- [ ] You see: "Server running on port 5000"
- [ ] Terminal 2: `npm run dev` is running
- [ ] Browser: http://localhost:5173 loads
- [ ] Try adding subject → Works!

If all checkboxes pass, you're done!

---

## Still Stuck?

1. Run this test:
```bash
curl http://localhost:5000/health
```

Should return: `OK`

2. Check backend terminal for errors
3. Read the error message carefully
4. It will tell you what's wrong

---

**Backend must be running. Full stop. That's the issue.**

Run `npm start` and try again.
