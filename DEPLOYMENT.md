# Netlify Deployment Guide

## Quick Deploy

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/your-username/legalrag)

## Manual Deployment Steps

### 1. Prepare Repository
- Fork or clone this repository to your GitHub account
- Ensure all files are committed and pushed

### 2. Connect to Netlify
1. Log in to [Netlify](https://app.netlify.com)
2. Click "New site from Git"
3. Choose GitHub and select your repository
4. Netlify will auto-detect the configuration from `netlify.toml`

### 3. Configure Environment Variables
In your Netlify site settings, add:
```
GROQ_API_KEY=your_groq_api_key_here
```

### 4. Deploy
- Click "Deploy site"
- Netlify will automatically build and deploy your application
- Your app will be available at: `https://your-site-name.netlify.app`

## Build Verification

The build process includes:
1. **Frontend Build**: `vite build` - Creates optimized React app
2. **Function Build**: `esbuild` - Bundles serverless API function
3. **Output Verification**: 
   - Frontend: `dist/` directory with static assets
   - Backend: `netlify/functions/api.mjs` serverless function

## Post-Deployment Testing

After deployment, test these endpoints:
- `https://your-site.netlify.app/` - Frontend application
- `https://your-site.netlify.app/api/health` - API health check
- Upload a DOCX document to test full functionality

## Troubleshooting

### Build Failures
- Check build logs in Netlify dashboard
- Verify all dependencies are in `package.json`
- Ensure `GROQ_API_KEY` is set correctly

### Function Errors
- Check function logs in Netlify dashboard
- Verify serverless function is properly bundled
- Test API endpoints individually

### CORS Issues
- Headers are configured in `_headers` file
- Additional CORS settings in function code
- Verify redirect rules in `netlify.toml`

## Performance Considerations

- **Cold Starts**: First function invocation may be slower
- **Memory**: Functions use in-memory storage (data resets between invocations)
- **File Size**: 10MB upload limit per document
- **Rate Limits**: Subject to Groq API limits

## Scaling Recommendations

For production use:
1. **Database**: Upgrade to PostgreSQL (Neon, Supabase, etc.)
2. **File Storage**: Use Cloudinary or AWS S3
3. **PDF Processing**: Integrate Adobe PDF Services API
4. **Caching**: Add Redis for document caching
5. **Rate Limiting**: Implement per-user rate limits

## Security Notes

- API keys stored securely in Netlify environment
- CORS properly configured for cross-origin requests
- Security headers added via `_headers` file
- No sensitive data exposed in client-side code