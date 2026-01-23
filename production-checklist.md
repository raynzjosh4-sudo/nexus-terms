# Production Deployment Checklist

## Security
- [x] Created `.env.example` with placeholder credentials
- [x] Created `.gitignore` to exclude `env.js` from version control
- [ ] Verify Supabase Row Level Security (RLS) policies are enabled
- [ ] Review Supabase permissions for anon key (read-only recommended)
- [ ] Enable CORS on Supabase if needed

## Performance
- [ ] Enable Gzip compression on web server
- [ ] Configure CDN for static assets (icon/, images)
- [ ] Test page load times
- [ ] Minify CSS/JavaScript (optional - CDN already handles Tailwind)
- [ ] Optimize images in icon/ folder

## Configuration
- [ ] Deploy env.js to production environment
- [ ] Update domain in Supabase allowed origins
- [ ] Configure SSL certificate (HTTPS required)
- [ ] Test all links point to correct URLs

## Deployment Steps

### Option 1: Traditional Hosting (Vercel, Netlify, GitHub Pages)
1. Push to GitHub (without env.js)
2. Connect repository to Vercel/Netlify
3. Add environment variables in deployment platform
4. Set `env.js` through build script or environment variables

### Option 2: Manual Server Deployment
1. Upload files to server
2. Create env.js on server with production credentials
3. Configure web server (nginx/Apache)
4. Enable HTTPS

### Option 3: Environment Variables Approach
Replace hardcoded config in env.js with:
```javascript
const CONFIG = {
    SUPABASE_URL: import.meta.env.VITE_SUPABASE_URL || "fallback-url",
    SUPABASE_KEY: import.meta.env.VITE_SUPABASE_KEY || "fallback-key"
};
```

## Testing
- [ ] Test on mobile (iOS & Android)
- [ ] Test on desktop (Chrome, Firefox, Safari, Edge)
- [ ] Verify legal documents load correctly
- [ ] Test navigation and menu functionality
- [ ] Verify Play Store links work
- [ ] Test error handling (connection failures)

## Monitoring
- [ ] Set up error logging (Sentry, LogRocket)
- [ ] Monitor API usage in Supabase dashboard
- [ ] Set up uptime monitoring
- [ ] Configure analytics (Google Analytics, Plausible)

## Post-Launch
- [ ] Monitor error rates
- [ ] Track user analytics
- [ ] Set up alerts for failures
- [ ] Regular backups of Supabase database
