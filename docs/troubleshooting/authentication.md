# Authentication Troubleshooting

Resolve account access and authentication issues.

## Can't Log In

### Error: Invalid Credentials

**Cause:** Incorrect email or password

**Solution:**

1. Verify email address spelling
2. Check CAPS LOCK is off
3. Try "Forgot Password" to reset

### Error: Account Not Activated

**Cause:** Email not verified

**Solution:**

1. Go to [https://mycloud.example.com/login](https://mycloud.example.com/login)
2. Click "Resend Verification Email"
3. Check your email (including spam folder)
4. Click the verification link

### Error: Account Locked

**Cause:** Too many failed login attempts

**Solution:**

Your account is locked for 30 minutes after 5 failed attempts.

1. Wait 30 minutes
2. Try logging in again
3. If problem persists, use "Forgot Password"

## Forgot Password

To reset your password:

1. Go to [https://mycloud.example.com/login](https://mycloud.example.com/login)
2. Click **Forgot Password**
3. Enter your email address
4. Check your email for reset link
5. Click link and enter new password
6. Try logging in with new password

The password reset link expires after **24 hours**.

## MFA Not Working

### Problem: Can't Receive MFA Codes

**Check:**

1. Is SMS enabled?
2. Is your phone number correct?
3. Is your device in airplane mode?
4. Do you have signal/data?

**Solutions:**

1. Try using an authenticator app instead
2. Request a new SMS code (10 second wait)
3. Use a backup code if you have one

### Problem: Authenticator App Shows Wrong Code

**Cause:** Device clock is out of sync

**Solution:**

1. Check phone time settings
2. Go to Settings → Date & Time → Automatic
3. Wait for time to sync (can take a few minutes)

### Problem: Lost Access to MFA Device

**If you have a backup code:**

1. Click "Use Backup Code" on the MFA prompt
2. Enter one of your 10 backup codes
3. After logging in, update your MFA method

**If you don't have a backup code:**

1. Go to [https://mycloud.example.com/support](https://mycloud.example.com/support)
2. Submit a support ticket with proof of identity
3. MyCloud support will help you regain access

## Account Locked

### Account Suspended

Your account may be suspended due to:

- Suspicious activity
- Billing issues
- Policy violation
- Admin action

**Resolution:**

1. Check email from MyCloud for reason
2. Follow instructions in email
3. Contact support if you need assistance

### Two-Factor Authentication Errors

**Error: Expired MFA code**

- MFA codes expire after 30 seconds
- Request a new code immediately
- Don't wait to enter the code

**Error: Invalid MFA code format**

- Ensure you're entering exactly 6 digits
- Don't include spaces or dashes
- Copy-paste to avoid typos

## Session Timeout

Your session may expire due to:

- Inactivity (15 minutes by default)
- Manual logout
- Security session revocation
- Password change

**Solution:**

Simply log in again. Your data is not affected.

## API Authentication Issues

### Error: Invalid API Key

**Causes:**

- Key is expired
- Key was revoked
- Key format is incorrect

**Solution:**

1. Go to **Settings** → **API Keys**
2. Create a new API key
3. Update your application to use the new key

### Error: Insufficient Permissions

**Cause:** Your API key doesn't have required permissions

**Solution:**

1. Go to **Settings** → **API Keys**
2. Click the key name
3. Check "Permissions" section
4. Verify all required scopes are enabled

### Error: Rate Limit Exceeded

**Cause:** Too many API requests in short period

**Solution:**

- Implement exponential backoff retry logic
- Reduce request rate
- Contact support for rate limit increase

## Still Having Issues?

If none of these solutions work:

1. Clear your browser cache and cookies
2. Try a different browser
3. Try from a different network
4. Contact support with error messages

---

**Contact Support:**

- **Email:** support@mycloud.example.com
- **Live Chat:** Available in console
- **Emergency:** +1-800-MYCLOUD-911
