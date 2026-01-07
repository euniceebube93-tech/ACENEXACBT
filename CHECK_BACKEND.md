# Backend Status Checker - Run This First!

## Step 1: Open Terminal and Check Port 5000

### Mac/Linux:
```bash
lsof -i :5000
```

### Windows:
```bash
netstat -ano | findstr :5000
```

**If it shows nothing:** Port 5000 is FREE ✓
**If it shows a process:** Something is already running

---

## Step 2: Start Backend (If Not Running)

```bash
npm start
```

You should see exactly this:
```
Server running on port 5000
```

**If you see an error:**
- Read the error message carefully
- Common: "Port already in use" → Kill process or use different port
- Common: "Cannot find module" → Run `npm install` first

---

## Step 3: Test Backend is Responding

**While backend is running, open a NEW terminal and run:**

### Mac/Linux/Windows:
```bash
curl http://localhost:5000/health
```

**Expected response:**
```
OK
```

**If you get error:**
- "Connection refused" → Backend not running
- Timeout → Backend crashed
- Other error → Read error message

---

## Step 4: Test Subject API

```bash
curl http://localhost:5000/api/subjects
```

**Expected response:**
```json
[{"id":"...", "name":"English", ...}, ...]
```

**If you get error:**
- 404 → Backend running but endpoint not found
- "Connection refused" → Backend not running
- Other → Check backend logs

---

## Step 5: Check Browser Console

1. Open http://localhost:5173 in browser
2. Press F12 to open DevTools
3. Go to Console tab
4. Try adding a subject
5. Look for error message
6. Post the exact error here

---

## Common "Failed to Fetch" Causes

| Error | Cause | Fix |
|-------|-------|-----|
| "Failed to fetch" | Backend not running | Run `npm start` |
| "CORS error" | CORS config wrong | Check server.js lines 19-38 |
| "Network timeout" | Backend too slow | Check logs in terminal |
| "503 Service Unavailable" | Database unreachable | Check Supabase connection |

---

## Checklist Before Adding Subject

- [ ] Terminal 1 running: `npm start` (Backend)
- [ ] Terminal 2 running: `npm run dev` (Frontend)
- [ ] Browser: http://localhost:5173 (Frontend)
- [ ] Backend responds: `curl http://localhost:5000/health` = OK
- [ ] API responds: `curl http://localhost:5000/api/subjects` = JSON array
- [ ] Browser console: No red errors

If all checkboxes pass, adding subject should work!

---

## Still Failing? Follow This:

1. Open Terminal 1
2. Stop backend (Ctrl+C)
3. Run: `npm start`
4. Wait for: "Server running on port 5000"
5. Go to http://localhost:5173
6. Try adding subject again

If still "failed to fetch":
1. Press F12 in browser
2. Go to Console tab
3. Try adding subject
4. Copy the error message
5. Share it with us

---

## Emergency Reset (If Nothing Works)

```bash
# Terminal 1 - Stop backend (Ctrl+C)

# Kill anything on port 5000
lsof -ti:5000 | xargs kill -9  # Mac/Linux
netstat -ano | findstr :5000   # Windows (then taskkill /PID <PID> /F)

# Start fresh
npm install
npm start

# Terminal 2
npm run dev
```

---

**Your backend MUST be running for ANY API calls to work!**

If you see "Server running on port 5000" in Terminal 1, your backend is ready.
