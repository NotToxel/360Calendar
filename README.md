# Smart Calendar Redirector

This is a **single-page HTML website** designed to redirect users to the correct calendar subscription link based on their **device or browser**.  
It solves the common problem where a single `webcal://` or `https://` link does not provide a good experience across all platforms (**iOS**, **Android**, **macOS**, and **Windows/Linux**).

---

## 🧩 The Problem

- **iOS (iPhone/iPad):** Works best with `webcal://` to open the native Apple Calendar.  
- **macOS:** Safari works well with `webcal://`, but Chrome/Firefox on Mac do not.  
- **Android:** `webcal://` is not reliably supported. `https://` links open the browser, not the native Google Calendar app. The best method is to use a specific `intent://` URL.  
- **Desktop (Windows, Linux, other browsers):** The standard `https://` web calendar link is the most reliable option.  

---

## ⚙️ How It Works

The `index.html` file contains a simple JavaScript snippet that runs when the page loads.  
It checks the browser’s **user agent string** to detect the user's operating system and browser.

Based on the detection, it performs the following logic:

1. **If iOS or macOS Safari:**  
   Redirect to **`appSubscribeUrl`** (the `webcal://` link).  

2. **If Android:**  
   Redirect to **`androidIntentUrl`** (the `intent://` link), which attempts to open the native Google Calendar app and falls back to the web calendar if the app isn’t installed.  

3. **Everyone Else (Windows, Linux, Chrome/Firefox on Mac):**  
   Redirect to **`googleCalWebUrl`** (the standard `https://` web link).  

---

## 🌟 Features

- **Smart Redirect:** Directs users to the best link for their platform.  
- **Rich Link Previews:** Includes `<meta>` and Open Graph (`og:`) tags in the `<head>` so that when you share the link on apps like WhatsApp, X (Twitter), or iMessage, it displays a clean title and description.  
- **No User Click Needed:** The redirect is automatic on page load for all platforms.  
- **Static Site:** No server-side logic required. Can be hosted for free on any static hosting service (e.g., GitHub Pages, Netlify, or Vercel).  

---

## 🛠️ How to Use

1. **Customize URLs**  
   Open `index.html` and find the `<script>` section.  
   Modify the following three constants with your own calendar links:

   - `appSubscribeUrl`: Your `webcal://` link for Apple devices.  
   - `googleCalWebUrl`: Your standard `https://` web calendar link.  
   - `androidIntentUrl`: Your Android-specific `intent://` link.  
     Make sure to update the `cid=` and `S.browser_fallback_url=` parts.  

2. **Customize Meta Tags**  
   In the `<head>`, change the `<title>`, `<meta name="description">`, and `og:` tags to match your calendar’s name and description.  

3. **Deploy**  
   Upload the `index.html` file to your static hosting provider.  

---

This project is created for 360 Fellowship 
linktr.ee/360Fellowship
@360fellowship
