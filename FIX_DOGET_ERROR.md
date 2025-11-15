# Fix "Script function not found: doGet" Error

## The Problem
When you visit your Google Apps Script URL directly, you see:
```
Script function not found: doGet
```

This happens because your Google Apps Script doesn't have the `doGet` function yet.

## The Solution - 3 Simple Steps

### Step 1: Open Your Google Apps Script Editor

1. Go to [Google Apps Script](https://script.google.com)
2. Find and open the project that created your web app URL
3. You should see the code editor

### Step 2: Copy and Paste the Complete Script

**Delete ALL existing code** in the editor, then copy and paste this ENTIRE script:

```javascript
// Test function - allows you to verify the script is working by visiting the URL
function doGet(e) {
  return ContentService
    .createTextOutput(JSON.stringify({ 
      'status': 'success', 
      'message': 'Google Apps Script is working! Ready to receive POST requests.',
      'instructions': 'This script accepts POST requests with form data. Use it from your website form submission.'
    }))
    .setMimeType(ContentService.MimeType.JSON);
}

function doPost(e) {
  try {
    // Get or create the active spreadsheet
    const sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
    
    // Check if headers exist, if not create them
    const firstCell = sheet.getRange(1, 1).getValue();
    if (!firstCell || firstCell !== 'Timestamp') {
      const headers = [
        'Timestamp',
        'Services',
        'Duration',
        'Work Time',
        'Gender Preference',
        'Hours Per Week',
        'Food Arrangement',
        'Household Members',
        'Head of Household Age',
        'Bedroom Count',
        'Zip Code',
        'Address',
        'First Name',
        'Email',
        'Selected Plan'
      ];
      const headerRow = sheet.getRange(1, 1, 1, headers.length);
      headerRow.setValues([headers]);
      headerRow.setFontWeight('bold');
      headerRow.setBackground('#5B7B5A');
      headerRow.setFontColor('#FFFFFF');
    }
    
    // Get the form data
    const formData = e.parameter;
    
    // Prepare the row data in the correct sequence
    const rowData = [
      formData.timestamp || new Date().toISOString(),
      formData.services || '',
      formData.duration || '',
      formData.workTime || '',
      formData.genderPreference || '',
      formData.hoursPerWeek || '',
      formData.foodArrangement || '',
      formData.householdMembers || '',
      formData.headOfHouseholdAge || '',
      formData.bedroomCount || '',
      formData.zipCode || '',
      formData.address || '',
      formData.firstName || '',
      formData.email || '',
      formData.selectedPlan || ''
    ];
    
    // Append the row to the sheet
    sheet.appendRow(rowData);
    
    // Return success response
    return ContentService
      .createTextOutput(JSON.stringify({ 'result': 'success', 'row': sheet.getLastRow() }))
      .setMimeType(ContentService.MimeType.JSON);
      
  } catch (error) {
    // Return error response
    return ContentService
      .createTextOutput(JSON.stringify({ 'result': 'error', 'error': error.toString() }))
      .setMimeType(ContentService.MimeType.JSON);
  }
}
```

**OR** you can copy it from the `google-apps-script.js` file in your project folder.

### Step 3: Save and Redeploy

1. Click the **Save** icon (💾) or press `Ctrl+S` (Windows) / `Cmd+S` (Mac)
2. Click **Deploy** → **Manage deployments**
3. Click the **pencil icon** ✏️ next to your existing deployment
4. Click **New version** (this creates a new version with your updated code)
5. Click **Deploy**
6. **IMPORTANT**: Make sure "Who has access" is set to **"Anyone"**
7. The URL should remain the same: `https://script.google.com/macros/s/AKfycbytgLUmFFaCI7SVRptxOHCY7f5aP9dNiRMhf-KuYqrkPc-ehKqv1SJp3HAmLsbSFYK6/exec`

## Test It Works

1. Visit your URL: https://script.google.com/macros/s/AKfycbytgLUmFFaCI7SVRptxOHCY7f5aP9dNiRMhf-KuYqrkPc-ehKqv1SJp3HAmLsbSFYK6/exec

2. You should now see a JSON response like:
```json
{
  "status": "success",
  "message": "Google Apps Script is working! Ready to receive POST requests.",
  "instructions": "This script accepts POST requests with form data. Use it from your website form submission."
}
```

If you see this, **it's working!** ✅

## Your Website is Already Configured

Your `host-pricing-page.html` file has already been updated with your new URL, so once you fix the Google Apps Script, everything will work automatically!

## Next Steps

1. Complete the 3 steps above
2. Test the URL to verify it works
3. Test your full survey flow on your website
4. Check your Google Sheet - data should appear automatically!

## Still Having Issues?

- Make sure you're editing the **correct** Apps Script project (the one that created your web app URL)
- Make sure you clicked **"New version"** before deploying (not just "Deploy")
- Check that "Who has access" is set to **"Anyone"**
- Make sure your Google Sheet is open and accessible

