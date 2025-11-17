# How to Find Your Contentsquare Tracking Code

## Step-by-Step Instructions

### Method 1: Through Analysis Setup (Easiest)

1. **Look at the left navigation menu** in your Contentsquare dashboard
2. **Click on "Analysis setup"** (the one with the settings/gear icon) at the bottom of the menu
3. **Look for "Installation"** or **"Tracking Code"** section
4. **You'll see your Site ID** and the tracking code there

### Method 2: Through Settings Menu

1. **Click on your profile icon** in the top right (the circle with "jp" or your initials)
2. **Look for "Settings"** or **"Account Settings"** in the dropdown
3. **Navigate to "Installation"** or **"Tracking Code"** section
4. **Copy your Site ID** (it will be a number like `1234567`)

### Method 3: Through Get Started

1. **Click on "Get started"** at the top of the left navigation (rocket icon)
2. **Follow the setup wizard** - it should guide you to the installation step
3. **The tracking code/Site ID will be shown** during the setup process

### Method 4: Direct URL

If you can't find it in the menu, try going directly to:
- **Settings → Installation**
- Or look for a section called **"Installation"**, **"Tracking Code"**, or **"Implementation"**

## What You're Looking For

You need to find:
- **Site ID**: A number (like `1234567` or `abc123`)
- **Tracking Code**: The JavaScript snippet that contains your Site ID

## Once You Find It

1. **Copy your Site ID** (the unique identifier)
2. **Go back to your HTML files**
3. **Find `YOUR_SITE_ID`** in the tracking code I added
4. **Replace it** with your actual Site ID

For example, if your Site ID is `1234567`, change:
```javascript
e.src='https://'+i+'.contentsquare.net/cs/contentsquare.min.js';
h.appendChild(e);})(window,document,'script','YOUR_SITE_ID','csq');
```

To:
```javascript
e.src='https://'+i+'.contentsquare.net/cs/contentsquare.min.js';
h.appendChild(e);})(window,document,'script','1234567','csq');
```

## Quick Tips

- The Site ID is usually a **number** or **alphanumeric string**
- It might be labeled as **"Site ID"**, **"Project ID"**, or **"Container ID"**
- The tracking code section might also show you the **full JavaScript code** - you can use that too, but the code I added should work with just the Site ID

## Still Can't Find It?

If you can't locate the tracking code:
1. **Check the "Get started" section** - it often guides you through setup
2. **Look for a "Help" or "Support" button** (question mark icon in top right)
3. **Contact Contentsquare support** - they can guide you to the right section
4. **Check your email** - Contentsquare might have sent setup instructions with your Site ID

## After You Get Your Site ID

1. Replace `YOUR_SITE_ID` in all 6 HTML files:
   - `index.html`
   - `survey-page-1.html`
   - `survey-page-2.html`
   - `survey-page-3.html`
   - `host-pricing-page.html`
   - `send.html`

2. **Save all files**

3. **Visit your website** - Contentsquare will start tracking immediately

4. **Check your dashboard** - Data should appear within a few minutes to 24 hours

