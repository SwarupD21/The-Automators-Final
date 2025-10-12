# Google OAuth 2.0 Authentication Setup Guide

## Overview
This application includes Google OAuth 2.0 authentication using Google Identity Services (GSI). The implementation includes security measures, token validation, and a demo mode for testing.

## Setup Instructions

### 1. Create Google OAuth 2.0 Credentials

1. Go to the [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select an existing one
3. Enable the required APIs:
   - Go to "APIs & Services" > "Library"
   - Search for and enable "Google+ API" or "People API"
   - Enable "Google Identity Services API"
4. Create OAuth 2.0 Client ID:
   - Go to "APIs & Services" > "Credentials"
   - Click "Create Credentials" > "OAuth 2.0 Client IDs"
   - Choose "Web application" as the application type
   - Add authorized JavaScript origins:
     - `http://localhost:8000` (for local development)
     - `https://yourdomain.com` (for production)
   - Add authorized redirect URIs:
     - `http://localhost:8000` (for local development)
     - `https://yourdomain.com` (for production)

### 2. Configure the Application

1. Copy your Google OAuth Client ID from the Google Cloud Console
2. Open `script.js` file
3. Replace `YOUR_GOOGLE_CLIENT_ID_HERE` with your actual client ID:

```javascript
const GOOGLE_CLIENT_ID = 'your-client-id.apps.googleusercontent.com';
```

### 3. Security Features Implemented

- **Token Validation**: Validates JWT tokens for expiration and issuer
- **Session Management**: Secure session handling with automatic cleanup
- **CSRF Protection**: Content Security Policy headers
- **XSS Protection**: Security headers to prevent cross-site scripting
- **Secure Logout**: Proper token revocation and cleanup

### 4. Demo Mode

If Google services fail to load or no client ID is configured, the application automatically falls back to demo mode. This allows you to test the authentication flow without setting up Google OAuth.

### 5. Testing

1. **With Google OAuth**:
   - Click "Continue with Google"
   - Complete the Google authentication flow
   - User information will be securely stored

2. **Demo Mode**:
   - Click "Continue with Google (Demo Mode)"
   - Uses mock user data for testing

3. **Guest Mode**:
   - Click "Continue as Guest"
   - No authentication required

## Security Considerations

### Current Security Measures:
- JWT token validation
- Session expiration handling
- Secure token storage
- Content Security Policy
- XSS protection headers
- CSRF protection

### Additional Recommendations:
- Use HTTPS in production
- Implement server-side token validation
- Add rate limiting
- Implement proper logging
- Regular security audits

## Troubleshooting

### Common Issues:

1. **"400 Bad Request" error**:
   - Verify your OAuth client ID is correct
   - Check that your domain is added to authorized origins
   - Ensure the client ID is properly formatted

2. **"This app isn't verified" warning**:
   - This is normal for development
   - Click "Advanced" > "Go to [app name] (unsafe)" to proceed

3. **Authentication not working**:
   - Check browser console for errors
   - Verify Google services are loading
   - Check network connectivity
   - Ensure OAuth client ID is properly configured

### Browser Compatibility:
- Chrome 80+
- Firefox 75+
- Safari 13+
- Edge 80+

## File Structure

```
├── index.html          # Main HTML file with Google Sign-In button
├── script.js           # JavaScript with OAuth implementation
├── style.css          # CSS styles
└── GOOGLE_AUTH_SETUP.md # This setup guide
```

## Support

For issues with Google OAuth setup, refer to:
- [Google Identity Services Documentation](https://developers.google.com/identity/gsi/web)
- [Google OAuth 2.0 Documentation](https://developers.google.com/identity/protocols/oauth2)
- [Google Cloud Console](https://console.cloud.google.com/)

For application-specific issues, check the browser console for error messages.
