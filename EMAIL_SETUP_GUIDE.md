# Email Configuration Setup Guide

This guide will help you set up email functionality for the contact form to send emails to vendyfashions@gmail.com.

## EmailJS Setup

The contact form uses EmailJS service to send emails directly from the browser. Follow these steps to configure it:

### Step 1: Create EmailJS Account

1. Go to [EmailJS.com](https://www.emailjs.com/)
2. Sign up for a free account
3. Verify your email address

### Step 2: Add Email Service

1. In your EmailJS dashboard, go to "Email Services"
2. Click "Add New Service"
3. Choose your email provider (Gmail recommended)
4. For Gmail:
   - Service ID: Create a unique name (e.g., "gmail_service")
   - User ID: vendyfashions@gmail.com
   - Follow the authentication process

### Step 3: Create Email Template

1. Go to "Email Templates" in your dashboard
2. Click "Create New Template"
3. Template ID: Create a unique name (e.g., "contact_form")
4. Use this template content:

```
Subject: New Contact Form Message - {{subject}}

From: {{from_name}} <{{from_email}}>
Phone: {{phone}}
Subject: {{subject}}

Message:
{{message}}

---
This message was sent from the VENDY Fashion contact form.
```

### Step 4: Get Your Keys

1. Go to "Account" > "General"
2. Copy your "Public Key"
3. Note your "Service ID" and "Template ID"

### Step 5: Update the Code

In `pages/contact.html`, replace the following placeholders:

1. Replace `YOUR_PUBLIC_KEY` with your actual public key
2. Replace `YOUR_SERVICE_ID` with your service ID
3. Replace `YOUR_TEMPLATE_ID` with your template ID

Example:
```javascript
emailjs.init({
    publicKey: "abcd1234efgh5678", // Your actual public key
});

// In the send function:
emailjs.send('gmail_service', 'contact_form', templateParams)
```

### Step 6: Test the Form

1. Open the contact page
2. Fill out the form
3. Click "Send Message"
4. Check vendyfashions@gmail.com for the email

## Alternative: Server-Side Solution

If you prefer a server-side solution, you can:

1. Set up a backend server (Node.js, PHP, Python, etc.)
2. Use server-side email libraries (Nodemailer, PHPMailer, etc.)
3. Update the form to submit to your server endpoint

## Security Notes

- EmailJS public keys are safe to use in client-side code
- The service is rate-limited to prevent abuse
- For production use, consider implementing additional validation
- Monitor your EmailJS usage to stay within free tier limits

## Troubleshooting

- **Form not sending**: Check browser console for errors
- **Emails not received**: Verify EmailJS service configuration
- **Rate limiting**: EmailJS free tier has monthly limits
- **Spam folder**: Check if emails are going to spam

## Support

For EmailJS specific issues, visit their [documentation](https://www.emailjs.com/docs/) or contact their support.