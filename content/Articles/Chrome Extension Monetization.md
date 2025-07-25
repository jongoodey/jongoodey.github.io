---
title: How to Monetise Your Chrome Extension Using ExtPay.js
description: A complete guide to monetizing Chrome extensions with ExtPay.js without needing a backend server
---

If you've built a Chrome extension and are wondering how to turn it into a source of revenue, look no further than [ExtPay.js](https://github.com/glench/ExtPay) — a lightweight JavaScript library by [ExtensionPay.com](https://extensionpay.com/) that makes it simple to accept payments and manage subscriptions directly within your extension, all **without needing a server**.

In this guide, we'll walk you through:

- What ExtPay.js is
- How to install and configure it
- How to check a user's subscription status
- How to trigger payment and trial pages
- Best practices for implementation

---

## 🔧 What is ExtPay.js?

ExtPay.js is a front-end library that integrates with ExtensionPay.com — a payments platform built specifically for browser extensions. It lets developers:

- Accept one-time or subscription payments
    
- Detect if a user is paid or unpaid
    
- Trigger payment/trial upgrade flows
    
- Do all of the above **without needing a backend**
    

It’s ideal for indie developers or small teams who want to offer premium features within their Chrome (or other Chromium-based) extensions.

---

## ✅ Step-by-Step Setup

### 1. Install the ExtPay.js library

Include ExtPay in your extension’s content script or popup:

```html
<script src="https://extensionpay.com/extpay.js"></script>
```

You can also install it via npm if you're using a bundler:

```bash
npm install extpay
```

---

### 2. Configure Your Extension on ExtensionPay.com

Head to [ExtensionPay.com](https://extensionpay.com/) and create your project. You’ll receive a `publicKey` that you’ll need to use in your extension.

---

### 3. Initialise ExtPay

Add the following to your popup or background script:

```js
const ExtPay = require('extpay')('your-extension-name'); 
const extpay = ExtPay.init();
```

Replace `'your-extension-name'` with the slug from your ExtensionPay dashboard.

---

### 4. Check a User's Subscription Status

You can check if a user is paid like this:

```js
extpay.getUser().then(user => {
  if (user.paid) {
    // Show premium content
  } else {
    // Show upgrade prompt
  }
});
```

The `user` object also includes `trialStartedAt`, `plan`, `licensed` and more, making it easy to personalise the UX.

---

### 5. Trigger the Subscription Payment Page

To let users upgrade to a paid plan:

```js
extpay.openPaymentPage();
```

This will open a secure payment window provided by ExtensionPay.

---

### 6. Offer a Free Trial

To open a trial prompt instead:

```js
extpay.openTrialPage();
```

This is helpful if you want to offer a time-limited free trial before requiring payment.

---

### 7. React to Trial/Paid Events

Use event listeners to track when users go from free to trial to paid:

```js
extpay.onPaid.addListener(() => {
  // Enable premium features
});
```

This ensures your extension responds in real-time when a user's subscription changes.

---

## 📦 Example Use Case

Let’s say you’ve built a Chrome extension for managing Gmail inboxes. You want to keep basic features free but charge for premium features like multi-account support or advanced filters.

Using ExtPay, you could:

- Check if the user is paid using `extpay.getUser()`
    
- If not, prompt them to upgrade via `extpay.openPaymentPage()`
    
- Give new users a free 7-day trial using `extpay.openTrialPage()`
    
- Automatically unlock features once payment is confirmed using `onPaid`
    

---

## ⚠️ Key Notes and Best Practices

- You **must** include `https://extensionpay.com` in your `content_security_policy` in the manifest.
    
- Payment windows open in a new tab or popup, so ensure your extension permissions allow it.
    
- You can include additional metadata or plan identifiers when opening the payment page for finer control.
    
- ExtensionPay handles all Stripe integration on your behalf — you only deal with the frontend.
    

---

## 🔚 Final Thoughts

ExtPay.js is a simple, elegant solution for developers who want to monetise their Chrome extension without the hassle of building a billing backend. Whether you're charging once or offering subscriptions, this library handles it seamlessly and securely.

If you’re serious about turning your Chrome extension into a product, **ExtPay should be part of your monetisation stack**.

---

## 🔗 Resources

- [ExtPay GitHub Repo](https://github.com/glench/ExtPay)
    
- [ExtensionPay Dashboard](https://extensionpay.com/)
    
- [Chrome Extension Developer Docs](https://developer.chrome.com/docs/extensions/)
    

---

Would you like me to turn this into a blog post or LinkedIn article format next? Or embed it into your Notion or CMS setup?