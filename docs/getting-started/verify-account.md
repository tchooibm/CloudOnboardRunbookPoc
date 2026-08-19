# Verifying Your Account

Once you've created your account, you need to verify your email address.

## Step 1: Check Your Email

Look for an email from `noreply@mycloud.example.com` with the subject:

```
Welcome to MyCloud - Verify Your Email Address
```

## Step 2: Click the Verification Link

The email contains a verification link. Click it or copy and paste the URL into your browser.

The link will be valid for **24 hours**.

## Step 3: Confirmation

You'll see a success message:

```
Email verified successfully!
Redirecting to dashboard...
```

You're now ready to set up your account.

## What If the Link Expired?

If the verification link has expired:

1. Go to [https://mycloud.example.com/login](https://mycloud.example.com/login)
2. Enter your email address
3. Click "Resend Verification Email"
4. Check your email for a new link

## Resend Verification Email

To manually request a new verification email:

```
POST /api/auth/resend-verification
Content-Type: application/json

{
  "email": "your-email@example.com"
}
```

## Next Steps

After verification, proceed to:

1. [Set Up Multi-Factor Authentication](mfa-setup.md)
2. [Configure Billing](../account-setup/billing.md)
3. [Create API Keys](../account-setup/api-keys.md)

---

**Tip:** Save your verification email in case you need to reference it.
