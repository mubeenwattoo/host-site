# Contentsquare (Hotjar) Implementation Guide

## What is Contentsquare/Hotjar?

**Contentsquare** (formerly Hotjar) is a digital experience analytics platform that helps you understand how users interact with your website. It provides:

### Key Features:
1. **Heatmaps** - Visual representation of where users click, move, and scroll
2. **Session Recordings** - Watch actual user sessions to see how people navigate your site
3. **User Behavior Analytics** - Understand user journeys and identify pain points
4. **Conversion Funnels** - Track where users drop off in your survey flow
5. **Form Analytics** - See where users struggle with form fields
6. **Feedback Polls** - Collect user feedback directly on your site

## Why Your Client Wants This

For your survey flow, Contentsquare will help:
- **See where users get stuck** in the 3-page survey
- **Identify confusing fields** or buttons
- **Track conversion rates** from page 1 → page 2 → page 3 → pricing page
- **Watch recordings** of users completing the survey
- **Optimize the user experience** based on real data

## Implementation Process

### ⏱️ Time Required: **5-10 minutes** (Very Quick!)

### Step 1: Get Your Contentsquare Account

1. **Sign up** at [www.contentsquare.com](https://www.contentsquare.com)
2. **Create an account** (or use existing Hotjar account)
3. **Add your website** to the account
4. **Get your Site ID** - This is a unique number (like `1234567`)

### Step 2: Get Your Tracking Code

1. **Log in** to Contentsquare dashboard
2. **Go to Settings** → **Installation** or **Tracking Code**
3. **Copy the tracking code** - It will look like this:

```html
<!-- Hotjar Tracking Code -->
<script>
    (function(h,o,t,j,a,r){
        h.hj=h.hj||function(){(h.hj.q=h.hj.q||[]).push(arguments)};
        h._hjSettings={hjid:YOUR_SITE_ID,hjsv:6};
        a=o.getElementsByTagName('head')[0];
        r=o.createElement('script');r.async=1;
        r.src=t+h._hjSettings.hjid+j+h._hjSettings.hjsv;
        a.appendChild(r);
    })(window,document,'https://static.hotjar.com/c/hotjar-','.js?sv=');
</script>
```

**OR** for Contentsquare (newer version):

```html
<script>
(function(c,s,q,i,o){c[o]=c[o]||function(){(c[o].a=c[o].a||[]).push(arguments)};
var h=s.getElementsByTagName('head')[0];var e=s.createElement('script');
e.async=1;e.src='https://'+i+'.contentsquare.net/cs/contentsquare.min.js';
h.appendChild(e);})(window,document,'script','YOUR_SITE_ID','csq');
</script>
```

### Step 3: Add to Your HTML Files

You need to add the tracking code to **ALL** your HTML pages:
- `index.html`
- `survey-page-1.html`
- `survey-page-2.html`
- `survey-page-3.html`
- `host-pricing-page.html`
- `send.html`

**Place it in the `<head>` section**, right before the closing `</head>` tag.

### Step 4: Verify Installation

1. **Visit your website** in a browser
2. **Check Contentsquare dashboard** - Should show "Tracking Active" within a few minutes
3. **Test by navigating** through your survey - Data should start appearing

## Important Notes

### Privacy & GDPR Compliance
- **Inform users** about data collection (add to privacy policy)
- **Get consent** if required by your jurisdiction
- Contentsquare has built-in privacy features

### Performance Impact
- **Minimal impact** - Script loads asynchronously
- **Doesn't slow down** your website
- **No visible changes** to users

### Data Collection
- **Starts immediately** after installation
- **Takes 24-48 hours** to see meaningful data
- **Session recordings** available in dashboard

## What You'll See in Contentsquare

After implementation, you can:

1. **View Heatmaps**:
   - Click heatmaps (where users click)
   - Move heatmaps (mouse movement)
   - Scroll heatmaps (how far users scroll)

2. **Watch Recordings**:
   - See actual user sessions
   - Filter by page, device, country
   - See where users struggle

3. **Analyze Funnels**:
   - Track survey completion rate
   - See drop-off points
   - Identify problematic pages

4. **Form Analytics**:
   - See which fields cause issues
   - Track form completion time
   - Identify validation problems

## Next Steps After Implementation

1. **Wait 24-48 hours** for data to accumulate
2. **Review heatmaps** to see user behavior
3. **Watch recordings** of survey completions
4. **Identify issues** and optimize based on data
5. **Set up conversion funnels** to track survey flow

## Support

- **Contentsquare Help**: [help.contentsquare.com](https://help.contentsquare.com)
- **Hotjar Help** (if using Hotjar): [help.hotjar.com](https://help.hotjar.com)

---

**Implementation is quick and easy!** Just add the script tag to your HTML files and you're done! 🚀

