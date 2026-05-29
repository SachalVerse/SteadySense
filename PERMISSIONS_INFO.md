# Permissions Information - SteadySense v1.0.0

Detailed explanation of all app permissions, why they're needed, and how to manage them.

---

## 📋 Permission Overview

SteadySense requests several Android permissions to provide its core features. All permissions are necessary for proper functionality.

| Permission | Category | Required | Status |
|-----------|----------|----------|--------|
| ACCESS_FINE_LOCATION | Location | Yes | Critical |
| ACCESS_COARSE_LOCATION | Location | Yes | Critical |
| ACCESS_BACKGROUND_LOCATION | Location | Yes | Critical |
| ACTIVITY_RECOGNITION | Motion | Yes | Important |
| RECORD_AUDIO | Media | Yes | Important |
| POST_NOTIFICATIONS | System | Yes | Important |
| FOREGROUND_SERVICE | System | Yes | Critical |
| INTERNET | Network | Yes | Critical |

---

## 🗺️ Location Permissions

### ACCESS_FINE_LOCATION
**Purpose**: Precise GPS location tracking
**Why Needed**: 
- Emergency location sharing during falls
- Exact coordinates for caretaker map display
- SOS alert location accuracy
**Data Used For**:
- Real-time position on map
- Emergency services dispatch
- Family member notifications

**Accuracy**: ±5-20 meters

---

### ACCESS_COARSE_LOCATION
**Purpose**: Approximate location via WiFi/cellular networks
**Why Needed**:
- Backup location if GPS unavailable
- Faster initial location acquisition
- Battery efficiency
**Data Used For**:
- Approximate position when GPS fails
- Quick location updates

**Accuracy**: ±100-500 meters

---

### ACCESS_BACKGROUND_LOCATION
**Purpose**: Continue tracking location while app is minimized
**Why Needed**:
- Continuous monitoring even when app is closed
- Emergency detection at any time
- Fall alerts even if app isn't active
**Data Used For**:
- 24/7 monitoring capability
- Background emergency detection
- Location history

**Important**: Enabling this allows continuous background activity

---

## 🏃 Activity & Motion Permissions

### ACTIVITY_RECOGNITION
**Purpose**: Detect movement patterns and physical activities
**Why Needed**:
- Fall detection algorithm uses motion sensors
- Step counting for activity monitoring
- Movement pattern analysis
- Distinguishes falling from normal movement

**Data Collected**:
- Accelerometer data (X, Y, Z axes)
- Gyroscope readings
- Movement velocity & acceleration
- Impact detection

**Technical Details**:
- Uses device sensors, NOT camera
- No video or visual recording
- Only mathematical motion patterns
- Privacy-focused analysis

---

## 🎤 Audio & Voice Permissions

### RECORD_AUDIO
**Purpose**: Capture voice commands for AI assistant
**Why Needed**:
- Voice-activated emergency calls
- AI assistant voice commands
- Voice-to-text for easier interaction
- Hands-free operation

**Data Usage**:
- Real-time audio processing
- NOT stored as recordings
- Converted to text immediately
- Sent to Google Gemini API for processing

**Privacy Notes**:
- Audio NOT stored permanently
- No recording files created
- Processed instantly then deleted
- Optional feature - can be disabled

---

## 🔔 Notification Permissions

### POST_NOTIFICATIONS
**Purpose**: Send alerts and emergency notifications
**Why Needed** (Android 13+):
- Emergency SOS alerts to caretakers
- Fall detection notifications
- System alerts
- Health reminders
- Update notifications

**Types of Notifications**:
- 🚨 Emergency alerts (HIGH priority)
- 📍 Location updates
- ⚠️ System warnings
- 📢 Reminders
- 🔔 Status updates

**Customization**:
- Enable/disable in Settings
- Choose notification sound
- Set vibration pattern
- Customize alert priority

---

## 🔧 System & Service Permissions

### FOREGROUND_SERVICE
**Purpose**: Run service continuously without being killed
**Why Needed**:
- Keep monitoring active 24/7
- Prevent app from being closed by system
- Maintain fall detection capability
- Continuous location tracking

**Technical Details**:
- Shows notification icon in status bar
- Allocates minimum resources
- Allows background execution
- Critical for emergency response

**What It Does**:
- Keeps motion sensors active
- Maintains GPS connection
- Monitors for falls continuously
- Processes real-time data

---

### INTERNET
**Purpose**: Connect to cloud services and APIs
**Why Needed**:
- Firebase authentication
- Cloud database synchronization
- Location data uploading
- Push notification delivery
- AI API calls (Google Gemini)
- Map data streaming

**Data Transmitted**:
- Location coordinates (encrypted)
- User activity data
- Fall detection alerts
- Medical information
- User profile data

**Encryption**: All data encrypted in transit using SSL/TLS

---

## 🛡️ Privacy & Security

### Data Protection Measures

**Encryption**:
- All transmitted data encrypted
- SSL/TLS secure connections
- Database encryption at rest
- User passwords hashed

**Access Control**:
- Only authorized users can view data
- Caretakers only see linked elders
- Elders can revoke caretaker access
- Admin access logs maintained

**Data Retention**:
- Location history: 90 days default
- Activity data: 1 year
- Alert history: Indefinite
- User can delete anytime

---

## 📱 How to Grant Permissions

### First Launch Permission Prompt
1. App will show permission request dialog
2. Read the permission description
3. Tap `Allow` to grant
4. Tap `Deny` to skip (may limit features)
5. Can be changed later in Settings

### Manual Permission Management

**For Android 6.0+**:
```
Settings
  ↓
Apps
  ↓
SteadySense
  ↓
Permissions
  ↓
Select permission to enable/disable
```

**Individual Permission Toggle**:
- Each permission has ON/OFF switch
- Changes take effect immediately
- No app restart required
- Can change anytime

---

## ⚙️ Recommended Permission Settings

### For Full Functionality:
```
✅ Location (Fine & Coarse & Background) - ALLOW
✅ Activity Recognition - ALLOW
✅ Microphone - ALLOW
✅ Notifications - ALLOW
✅ Contacts - ALLOW (optional)
✅ Photos/Media - ALLOW (optional)
```

### For Privacy-Conscious Users:
```
✅ Location (Fine & Background) - ALLOW (required)
✅ Activity Recognition - ALLOW (fall detection)
✅ Microphone - DENY (manual calling only)
✅ Notifications - ALLOW (alerts)
- Phone calls will not work without microphone
```

### For Battery Conservation:
```
⚠️ Background Location - LIMITED (battery drain warning)
✅ Activity Recognition - ALLOW (uses minimal battery)
✅ Others - As needed
```

---

## 🔐 Sensitive Data Handling

### What Data We Collect:
- **Location**: GPS coordinates, WiFi location
- **Motion**: Accelerometer/gyroscope data
- **Medical**: Health conditions (if provided)
- **Activity**: Movement patterns, step count
- **Audio**: Voice commands (processed real-time)

### What Data We DON'T Collect:
- ❌ Contacts without permission
- ❌ Messages or call logs
- ❌ Photos or videos
- ❌ Browser history
- ❌ App usage patterns
- ❌ Call recordings

### Data Sharing:
- Data NOT shared with third parties
- Only shared between linked users
- Firebase backend only
- No ads or marketing use

---

## 🚨 Emergency Access

### During Emergency (Fall Detected):
App may access:
- Exact location (high accuracy)
- Continuous updates (1 second)
- Device orientation data
- Impact force measurements
- Medical information (if available)

### For Emergency Contact:
Caretaker receives:
- Exact coordinates
- Maps view
- Nearest hospitals info
- Emergency contact details

---

## 🎯 Permissions Troubleshooting

### Permission Not Appearing in First Launch?
**Solution**:
- Go to Settings → Apps → SteadySense
- Tap "Permissions"
- Toggle the needed permission ON
- Launch app again

### Permission Keeps Being Denied?
**Solution**:
- Check if device has parental controls
- Ensure you're device owner
- Disable any security apps temporarily
- Try granting individually

### "Permission Not Available" on Older Android?
**Solution**:
- Some permissions only available on Android 6.0+
- Automatic location services will be used
- Fall detection uses all available sensors
- Contact support for Android 5.0 and below

### Permission Revoked by System?
**Solution**:
- Battery optimization may restrict permissions
- Go to Settings → Battery → Optimization
- Select "SteadySense" → "Don't Optimize"
- Re-enable permissions

---

## 📊 Permission Impact on Features

| Feature | Required Permissions | Impact if Denied |
|---------|-------------------|-----------------|
| Fall Detection | ACTIVITY_RECOGNITION | Feature disabled |
| Emergency Alerts | INTERNET, POST_NOTIFICATIONS | Alerts won't send |
| Location Tracking | ACCESS_FINE_LOCATION | No map display |
| Background Monitoring | ACCESS_BACKGROUND_LOCATION, FOREGROUND_SERVICE | Only when app active |
| Voice Commands | RECORD_AUDIO | Manual input only |
| SOS Sharing | INTERNET, LOCATION | Can't send location |

---

## 🔄 Permission Changes Over Time

### When App Updates:
- New permissions may be requested
- You'll see permission prompts
- Can choose allow or deny
- Existing permissions remain unchanged

### When System Updates:
- Android system may reset some permissions
- Security updates may affect access
- You may need to re-grant permissions
- Default to most secure setting

---

## 📞 Permission-Related Support

### Questions About a Permission?
1. Tap permission in this document
2. Read detailed explanation
3. Check if it's marked "Optional"
4. Decide to allow or deny

### Concerned About Privacy?
1. Visit Privacy Policy: https://delicate-froyo-10153b.netlify.app/
2. Review data practices
3. Contact: infosachalsultan@gmail.com
4. Report concerns on GitHub Issues

### Need to Restrict a Permission?
1. Go to App Settings
2. Find permission to disable
3. Toggle OFF
4. Some features may not work
5. Re-enable anytime if needed

---

## ✅ Permission Checklist

Before using SteadySense, ensure:

- [ ] Location permissions enabled (both fine & coarse)
- [ ] Background location allowed
- [ ] Activity recognition permitted
- [ ] Microphone access granted
- [ ] Notifications enabled
- [ ] Internet connection available
- [ ] Device has 50MB free storage
- [ ] Battery optimization disabled for app

---

## 📖 Quick Reference

**Critical Permissions** (App won't work without):
- ACCESS_FINE_LOCATION
- ACTIVITY_RECOGNITION
- FOREGROUND_SERVICE
- INTERNET

**Important Permissions** (Most features need):
- ACCESS_BACKGROUND_LOCATION
- POST_NOTIFICATIONS
- RECORD_AUDIO

**Optional Permissions** (Enhance experience):
- READ_CONTACTS
- READ_CALENDAR

---

**Version**: 1.0.0  
**Last Updated**: 2026-05-29  
**Status**: Stable Release

*For more information, visit the [Privacy Policy](https://delicate-froyo-10153b.netlify.app/)*
