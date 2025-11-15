# Quick Setup Guide - Your Google Sheets Integration

## ✅ Step 1: Update Your Google Apps Script

1. Go back to your Google Apps Script editor (where you created the web app)
2. **Replace the entire script** with the updated code from `google-apps-script.js`
3. Click **Save** (💾)
4. **IMPORTANT**: You need to create a **NEW DEPLOYMENT** or **UPDATE** the existing one:
   - Click **Deploy** → **Manage deployments**
   - Click the pencil icon ✏️ next to your deployment
   - Click **New version**
   - Click **Deploy**
   - **Copy the new URL** (it should be the same, but verify it matches your URL)

## ✅ Step 2: Verify Your HTML is Updated

Your `host-pricing-page.html` has already been updated with your Google Apps Script URL:
```html
<script data-google-script-url="https://script.google.com/macros/s/AKfycby7iP4xcVWPe2asw6f9lBwtQiAyY4aljKUeHyDG5ZMT9SRgLjxhGAl824O4tt--7C6t/exec"></script>
```

## ✅ Step 3: Test the Integration

### Test 1: Verify Script is Working
Visit your URL directly in a browser:
```
https://script.google.com/macros/s/AKfycby7iP4xcVWPe2asw6f9lBwtQiAyY4aljKUeHyDG5ZMT9SRgLjxhGAl824O4tt--7C6t/exec
```

You should see a JSON response like:
```json
{
  "status": "success",
  "message": "Google Apps Script is working! Ready to receive POST requests.",
  "instructions": "This script accepts POST requests with form data. Use it from your website form submission."
}
```

### Test 2: Test Full Survey Flow
1. Open your website
2. Go through the complete survey:
   - Fill out **survey-page-1.html** (select services and duration)
   - Fill out **survey-page-2.html** (select preferences)
   - Fill out **survey-page-3.html** (enter household details)
   - Go to **host-pricing-page.html** and select a plan
3. Check your Google Sheet - you should see a new row with all the data!

## 📊 What Data Will Be Collected?

Your Google Sheet will automatically create these columns (in order):

| Column | Description |
|--------|-------------|
| Timestamp | When the form was submitted |
| Services | Selected services (e.g., "Cooking, Cleaning") |
| Duration | How long help is needed |
| Work Time | When helper should work (Daytime/Evening/Flexible) |
| Gender Preference | Male/Female/Either |
| Hours Per Week | 10 hours or less / More than 10 hours |
| Food Arrangement | Provide food or $100/week allowance |
| Household Members | Number of household members |
| Head of Household Age | Age range |
| Bedroom Count | Number of bedrooms |
| Zip Code | Location zip code |
| Address | Full address |
| First Name | User's first name |
| Email | User's email address |
| Selected Plan | Basic / Premium / Concierge |

## 🔧 Troubleshooting

### Problem: Data not appearing in Google Sheet

**Solution 1**: Check browser console (F12 → Console tab) for errors

**Solution 2**: Verify the script is deployed correctly
- Go to Apps Script → Deploy → Manage deployments
- Make sure "Who has access" is set to **"Anyone"**

**Solution 3**: Check the execution log
- In Apps Script editor, go to **View** → **Execution log**
- Look for any error messages

**Solution 4**: Verify the spreadsheet is correct
- Make sure you're checking the correct Google Sheet
- The script uses the **active sheet** (the first sheet in your spreadsheet)

### Problem: "Script function not found: doGet" error

**Solution**: Make sure you've updated your Google Apps Script with the latest code from `google-apps-script.js` that includes the `doGet` function.

### Problem: CORS errors in browser console

**Solution**: This is normal - the script uses `no-cors` mode. The data should still be submitted successfully. Check your Google Sheet to verify.

## 🎉 You're All Set!

Once you've updated the Google Apps Script and tested it, your survey data will automatically be collected in your Google Sheet every time someone completes the survey and selects a pricing plan!

