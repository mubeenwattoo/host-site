# Google Sheets Integration Setup Guide

This guide will help you set up Google Sheets to automatically collect survey data from your website.

## Step-by-Step Setup

### 1. Create a Google Sheet
- Go to [Google Sheets](https://sheets.google.com)
- Create a new spreadsheet
- Name it something like "NestHelpers Survey Data"

### 2. Create the Google Apps Script
- In your Google Sheet, go to **Extensions** → **Apps Script**
- Delete any default code
- Copy the entire contents of `google-apps-script.js` file
- Paste it into the Apps Script editor
- Click the **Save** icon (💾) and name your project (e.g., "Survey Data Collector")

### 3. Deploy as Web App
- Click **Deploy** → **New deployment**
- Click the gear icon ⚙️ next to "Select type" and choose **"Web app"**
- Configure the deployment:
  - **Description**: "Survey Data Collector"
  - **Execute as**: "Me"
  - **Who has access**: "Anyone" (this allows your website to submit data)
- Click **"Deploy"**
- **IMPORTANT**: Copy the **Web App URL** that appears (it will look like: `https://script.google.com/macros/s/...`)

### 4. Update Your Website
- Open `host-pricing-page.html`
- Find the line: `const GOOGLE_SCRIPT_URL = scriptTag ? scriptTag.getAttribute('data-google-script-url') : 'YOUR_GOOGLE_APPS_SCRIPT_URL';`
- Replace `'YOUR_GOOGLE_APPS_SCRIPT_URL'` with your actual Web App URL from step 3

**OR** add this script tag in the `<head>` section of `host-pricing-page.html`:
```html
<script data-google-script-url="YOUR_WEB_APP_URL_HERE"></script>
```

### 5. Test the Integration
1. Fill out the survey on your website
2. Select a pricing plan
3. Check your Google Sheet - you should see a new row with all the data

## Data Columns

The script will automatically create these columns in your Google Sheet:
1. Timestamp
2. Services
3. Duration
4. Work Time
5. Gender Preference
6. Hours Per Week
7. Food Arrangement
8. Household Members
9. Head of Household Age
10. Bedroom Count
11. Zip Code
12. Address
13. First Name
14. Email
15. Selected Plan

## Troubleshooting

### Data not appearing in the sheet?
- Check the browser console (F12) for any error messages
- Verify the Web App URL is correct in your HTML file
- Make sure the Apps Script deployment has "Anyone" access
- Check the Apps Script execution log: **View** → **Execution log** in Apps Script editor

### Permission errors?
- Make sure you've authorized the script when prompted
- Check that the deployment is set to "Execute as: Me"

### Need to update the script?
- After making changes to the script, you need to create a **new deployment** or **update** the existing one
- The Web App URL will remain the same if you update the existing deployment

## Security Note

The current setup allows anyone to submit data to your sheet. If you need to restrict access, you can:
1. Add authentication to your Apps Script
2. Use a secret key/token system
3. Implement rate limiting

For most use cases, the current setup is sufficient as it only allows data submission, not data reading or modification.

