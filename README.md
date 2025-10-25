Busy RN Readme + users guide

## ✨ Features

- **🎨 Beautiful Glassmorphism UI** - Modern, sleek interface with glass-like transparency effects
- **📞 Intelligent Call Screening** - Automatically screen calls based on multiple criteria
- **⚡ Android 14+ Compatible** - Built with Android's latest CallScreeningService API
- **🔧 Flexible Rule System** - Create custom rules with multiple conditions
- **⏰ Time-Based Filtering** - Block calls during specific times or days
- **👥 Contact Integration** - Different rules for contacts, favorites, and unknown numbers
- **🔒 Privacy First** - All processing happens on-device

## 📋 Rule Criteria

Each rule can be configured with:

- **Caller ID Status** - Available/Hidden/Any
- **Contact Status** - In contacts/Not in contacts/Any
- **Favorites Status** - In favorites/Not in favorites/Any
- **Days of Week** - Monday through Sunday selection
- **Time Range** - Specific hours (e.g., 22:00 - 07:00)
- **Specific Numbers** - Target specific phone numbers
- **Inverse Match** - Apply action when criteria DON'T match

## 🎯 Available Actions

- **Allow** - Let the call ring normally
- **Reject** - Send to voicemail immediately
- **Silence** - Ring silently (no sound/vibration)
- **Voicemail** - Send directly to voicemail



 BusyRN - User Guide

## 🚀 Quick Start

### Step 1: Install the App
```bash
flutter build apk
flutter install -d bdb1ca32
```

### Step 2: Launch and Grant Permissions
1. Open the **BusyRN** app
2. You'll see the **Permissions screen** automatically
3. Grant each permission:
   - ✅ **Phone Permission** - Tap "Grant Permission" button
   - ✅ **Contacts Permission** - Tap "Grant Permission" button
   - ✅ **Call Screening Role** - Tap "Grant Permission" button (this will open a system dialog)

### Step 3: Set as Default Call Screening App ⚠️ **CRITICAL**

**This is the most important step!** Without this, the app won't screen any calls.

#### Method 1: Via System Dialog (Easiest)
When you tap "Grant Permission" for Call Screening Role, Android will show a dialog asking you to set BusyRN as the default. **Tap "Set as default"**.

#### Method 2: Manual Setup (If dialog was missed)
1. Open **Android Settings**
2. Go to **Apps** → **Default apps**
3. Tap **Call screening app** (or **Phone app** → **Call screening**)
4. Select **BusyRN**
5. Confirm

#### Method 3: Via Permissions Screen
1. In BusyRN, tap **"Request Call Screening Role"** button
2. When system dialog appears, grant it

### Step 4: Verify Setup
1. Return to BusyRN app
2. Home screen should show:
   - 🟢 **"Protection Active"** status
   - Toggle should be ON and enabled
3. If you see 🟠 **"Protection Inactive"**, the Call Screening Role wasn't granted properly

### Step 5: Configure Rules
1. Tap **"Manage Rules"** on home screen
2. You'll see 4 default rules:
   - **Always Allow Favorites** (Priority 0) - ✅ Enabled
   - **Block Unknown at Night** (Priority 1) - ✅ Enabled  
   - **Block Hidden Numbers** (Priority 2) - ❌ Disabled
   - **Allow All Contacts** (Priority 3) - ✅ Enabled

3. Toggle rules ON/OFF, or create new rules

### Step 6: Test It!
1. Have someone call you from a number that's NOT in your favorites
2. If it's night time (22:00-07:00), the call should be rejected
3. Check **View Call Logs** to see the call and action taken

---

## 📊 Understanding Call Logs

The **Call Logs** screen shows every call that was screened:

- **Green check** = Allowed (rang normally)
- **Red block** = Rejected (sent to voicemail)
- **Orange mute** = Silenced (rang without sound)
- **Blue voicemail** = Sent to voicemail

Each log shows:
- Phone number (or "Unknown Number")
- Action taken
- Whether caller was in contacts/favorites
- Time of call

You can refresh logs or clear them using the buttons at the top.

---

## 🛡️ How Call Screening Works

### Priority Order
Rules are evaluated in priority order (0 = highest priority). **The first matching rule determines the action.**

### Default Rules Explained

1. **Always Allow Favorites** (Priority 0)
   - Condition: Caller is in your favorites (starred contacts)
   - Action: Allow
   - Why: Safety - never block important people

2. **Block Unknown at Night** (Priority 1)
   - Condition: No caller ID + Time is 22:00-07:00
   - Action: Reject
   - Why: Block spam during sleep hours

3. **Block Hidden Numbers** (Priority 2)  
   - Condition: Caller ID is hidden
   - Action: Reject
   - Status: ❌ Disabled by default (you can enable it)

4. **Allow All Contacts** (Priority 3)
   - Condition: Caller is in your contacts
   - Action: Allow
   - Why: Allow known people through

### Example: Non-Favorite Calls You

**Scenario:** Someone in your contacts (but not favorited) calls at 11 PM

**Evaluation:**
1. Rule 0: Is in favorites? ❌ No → Skip
2. Rule 1: No caller ID? ❌ No → Skip
3. Rule 2: Disabled → Skip
4. Rule 3: In contacts? ✅ Yes → **ALLOW**

**Result:** Call rings normally

---

## 🔧 Creating Custom Rules

### Rule to Block All Non-Favorites
1. Tap "Manage Rules" → "+" button
2. Name: "Block Non-Favorites"
3. Priority: 0 (make it highest)
4. Criteria:
   - Favorites Status: **Not in Favorites**
5. Action: **Reject**
6. Save

This will block ALL calls except from your favorite contacts!

### Rule for Business Hours Only
1. Name: "Allow Contacts During Business Hours"
2. Priority: 1
3. Criteria:
   - Contact Status: **In Contacts**
   - Days: Monday-Friday
   - Time: 09:00 - 17:00
4. Action: **Allow**

### Rule to Silence Unknown Callers
1. Name: "Silence Unknown"
2. Priority: 2
3. Criteria:
   - Contact Status: **Not in Contacts**
4. Action: **Silence**

---

## ❌ Troubleshooting

### Problem: Calls NOT Being Blocked

**Solution 1: Check Call Screening Role**
1. Open BusyRN
2. Look at home screen status
3. If it says "Protection Inactive", you need to set BusyRN as default
4. Go to Android Settings → Apps → Default apps → Call screening app → BusyRN

**Solution 2: Check Service Toggle**
1. On home screen, make sure the toggle is ON (green)
2. If it's grayed out, the Call Screening Role wasn't granted

**Solution 3: Check Rules**
1. Tap "Manage Rules"
2. Make sure at least one rule is enabled
3. Verify the rule matches your test scenario

**Solution 4: Check Permissions**
1. Tap "Permissions & Setup"
2. All 3 items should show "Granted"
3. If not, grant them

### Problem: Can't Find "Call Screening App" in Settings

Different Android versions have it in different places:

**Android 14:**
- Settings → Apps → Default apps → Call screening app

**Android 13:**
- Settings → Apps → Default apps → Phone app → Call screening

**Android 12:**
- Settings → Apps → Default apps → Call app

**Android 10-11:**
- Settings → System → Call settings → Call blocking

**Can't find it?** Search "screening" or "default apps" in Android Settings

### Problem: Logs Not Showing

**Cause:** The app might not be screening calls yet

**Solution:**
1. Verify BusyRN is set as default (see above)
2. Make a test call
3. Pull down to refresh on the Call Logs screen

### Problem: All Calls Being Blocked

**Cause:** You might have a rule that's too broad

**Solution:**
1. Go to "Manage Rules"
2. Check your rules - especially Priority 0 (first to run)
3. Temporarily disable rules one by one to find the culprit
4. Make sure "Always Allow Favorites" is Priority 0 and ENABLED

---

## 💡 Pro Tips

### Tip 1: Use Priorities Wisely
- Lower number = Higher priority
- Put safety rules (like "Allow Favorites") at Priority 0
- Put general blocking rules at lower priorities

### Tip 2: Test Before Relying
- Test with known numbers first
- Check call logs to verify actions
- Don't rely on untested rules for important calls

### Tip 3: Create a "Whitelist" Rule
- Create a rule to allow specific numbers
- Set it to Priority 1 (after favorites)
- Use "Specific Numbers" field

### Tip 4: Vacation Mode
- Create rules for different scenarios
- Enable/disable groups of rules as needed
- Example: Enable "Block All Non-Favorites" when on vacation

### Tip 5: Monitor the Logs
- Check logs regularly to see patterns
- Adjust rules based on what you see
- Clear logs periodically to keep it tidy

---

## 🔒 Privacy & Security

### All Processing is Local
- No data sent to servers
- All screening happens on your device
- Rules stored locally in app data

### Permissions Explained
- **Phone**: Detect incoming calls
- **Contacts**: Check if caller is in contacts/favorites
- **Call Screening Role**: Screen and filter calls (system permission)

### Data Storage
- Rules: Stored in Hive database (local)
- Call logs: Stored in SharedPreferences (local)
- Settings: Stored in Hive database (local)

---

## 📱 Features Overview

### Current Features
- ✅ Rule-based call screening
- ✅ Favorites always allowed
- ✅ Time-based blocking
- ✅ Contact filtering
- ✅ Call logging
- ✅ Modern glassmorphism UI
- ✅ Priority-based rule engine

### Coming Soon
- ⏳ Call statistics dashboard
- ⏳ Export/import rules
- ⏳ Whitelist/blacklist management
- ⏳ Spam database integration
- ⏳ Scheduled profiles
- ⏳ Widget for quick toggle

---

## ⚙️ Technical Details

### Minimum Requirements
- Android 10 (API 29) or higher
- USB Debugging enabled (for installation)
- At least one contact marked as favorite (recommended)

### How It Works
1. Android system calls `CallScreeningService.onScreenCall()` for EVERY incoming call
2. Service checks caller against your rules (in priority order)
3. First matching rule determines the action
4. Action is applied immediately
5. Call is logged with details

### Limitations
- Cannot auto-answer calls (Android 10+ restriction)
- Cannot make calls on behalf of user
- Can only: Allow, Reject, or Silence
- Requires being set as default call screening app

---

## 🆘 Need More Help?

### In-App Help
- Tap "Permissions & Setup" → "View Setup Guide"
- Check the call logs to see what's happening

### Common Questions

**Q: Do I need internet?**
A: No, BusyRN works completely offline.

**Q: Will it drain my battery?**
A: No, CallScreeningService is very lightweight and only runs when a call comes in.

**Q: Can I use my regular dialer app?**
A: Yes! BusyRN only screens calls, it doesn't replace your dialer.

**Q: What happens if I uninstall?**
A: Your calls will ring normally. Android will ask you to choose a new default call screening app.

**Q: Can I backup my rules?**
A: Currently no, but this feature is planned.

---

## 📝 Quick Reference

### Actions
- **Allow**: Call rings normally
- **Reject**: Send to voicemail immediately  
- **Silence**: Ring silently (no sound/vibration)
- **Voicemail**: Same as reject

### Criteria
- **Caller ID**: Available / Hidden / Any
- **Contact Status**: In Contacts / Not in Contacts / Any
- **Favorites**: In Favorites / Not in Favorites / Any
- **Days**: Monday through Sunday (multiple selection)
- **Time**: Start hour/minute to End hour/minute
- **Specific Numbers**: Comma-separated list

### Screens
- **Home**: Status, stats, quick actions
- **Manage Rules**: View, edit, reorder rules
- **Call Logs**: View screening history
- **Permissions**: Grant required permissions

---

**That's it! You're now a BusyRN expert!** 🛡️📞

For issues or questions, check the troubleshooting section or create an issue on GitHub.


Created By Gabor Lorincz, all rights reserved 2025
