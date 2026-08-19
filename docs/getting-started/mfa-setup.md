# Setting Up Multi-Factor Authentication

Multi-factor authentication (MFA) adds an extra layer of security to your MyCloud account.

## Why MFA?

MFA requires something you know (password) + something you have (phone) to access your account, significantly reducing the risk of unauthorized access.

## Supported MFA Methods

1. **Authenticator App** - Use Google Authenticator, Microsoft Authenticator, or Authy (recommended)
2. **SMS Text Message** - Receive codes via text
3. **Email** - Receive codes via email

## Enable MFA via Authenticator App

### Prerequisites

Download one of these apps on your phone:

- Google Authenticator
- Microsoft Authenticator
- Authy
- 1Password

### Steps

1. Log in to your MyCloud account at [https://mycloud.example.com/dashboard](https://mycloud.example.com/dashboard)
2. Go to **Settings** → **Security** → **Multi-Factor Authentication**
3. Click **Enable MFA**
4. Select **Authenticator App**
5. Open your authenticator app on your phone
6. Scan the QR code displayed on screen
7. Enter the 6-digit code from your app
8. Click **Verify**

### Save Recovery Codes

Important! You'll receive 10 backup recovery codes. These allow you to access your account if you lose your phone.

- [ ] Write them down or take a screenshot
- [ ] Store them in a secure location (password manager, safe, etc.)
- [ ] Do NOT share them with anyone

## Enable MFA via SMS

1. Go to **Settings** → **Security** → **Multi-Factor Authentication**
2. Click **Enable MFA**
3. Select **SMS Text Message**
4. Enter your phone number
5. Click **Send Code**
6. Enter the 6-digit code received via SMS
7. Click **Verify**

## Testing MFA

To verify MFA is working:

1. Log out of your account
2. Log back in with your email and password
3. Enter the MFA code when prompted

## Disable or Change MFA

To change your MFA method:

1. Go to **Settings** → **Security** → **Multi-Factor Authentication**
2. Click **Disable MFA**
3. Verify your identity with your current MFA method
4. Follow the steps above to enable a new method

## Lost Your Phone?

If you lose access to your MFA device:

1. Use a recovery code to log in
2. Go to **Settings** → **Security** → **Multi-Factor Authentication**
3. Disable MFA
4. Enable MFA again with a new device

---

**Next:** [Configure Billing and Payment Methods](../account-setup/billing.md)

**Security Tip:** MFA is required for production accounts. We strongly recommend enabling it immediately.
