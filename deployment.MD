# 🚀 Deployment Guide - NutriScan Pro

This guide covers multiple deployment options for NutriScan Pro, from simple GitHub Pages to advanced cloud platforms.

## 📋 Table of Contents

- [Quick Deployment (GitHub Pages)](#github-pages-recommended)
- [Netlify Deployment](#netlify)
- [Vercel Deployment](#vercel)
- [Firebase Hosting](#firebase-hosting)
- [AWS S3 + CloudFront](#aws-s3--cloudfront)
- [Custom Domain Setup](#custom-domain-setup)
- [Environment-Specific Configurations](#environment-specific-configurations)

---

## 🌟 GitHub Pages (Recommended)

**Best for:** Quick deployment, free hosting, automatic HTTPS

### Step-by-Step Guide

1. **Fork the Repository**
   ```bash
   # Go to: https://github.com/your-username/nutriscan-pro
   # Click "Fork" button
   ```

2. **Enable GitHub Pages**
   - Go to repository **Settings**
   - Navigate to **Pages** (left sidebar)
   - Under "Source":
     - Branch: `main`
     - Folder: `/ (root)`
   - Click **Save**

3. **Wait for Deployment**
   - GitHub will build and deploy (2-5 minutes)
   - Green checkmark appears when ready

4. **Access Your App**
   ```
   https://your-username.github.io/nutriscan-pro/
   ```

5. **Update README**
   ```markdown
   # In README.md, replace:
   🔗 **[Live Demo](https://your-username.github.io/nutriscan-pro/)**
   ```

### Custom Domain (Optional)

1. **Add Custom Domain**
   - Settings → Pages → Custom domain
   - Enter: `nutriscan.yourdomain.com`
   - Click Save

2. **Configure DNS**
   ```
   Type: CNAME
   Name: nutriscan
   Value: your-username.github.io
   ```

3. **Enable HTTPS**
   - Checkbox: "Enforce HTTPS"
   - Wait for SSL certificate (few minutes)

### Troubleshooting

**404 Error:**
- Check branch is `main`
- Ensure `index.html` is in root
- Clear browser cache

**Not Updating:**
- Force rebuild: Make a commit
- Check Actions tab for build errors

---

## 🎨 Netlify

**Best for:** Custom domains, continuous deployment, advanced features

### One-Click Deploy

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start)

### Manual Deployment

1. **Sign Up**
   - Go to [netlify.com](https://www.netlify.com/)
   - Sign up with GitHub

2. **New Site from Git**
   - Click "New site from Git"
   - Choose GitHub
   - Select `nutriscan-pro` repository
   - Click "Deploy site"

3. **Configure Build Settings**
   ```
   Build command: (leave empty)
   Publish directory: /
   ```

4. **Deploy**
   - Click "Deploy site"
   - Wait 2-3 minutes
   - Get URL: `random-name.netlify.app`

### Custom Domain on Netlify

1. **Add Domain**
   - Site settings → Domain management
   - Add custom domain
   - Follow DNS configuration steps

2. **Enable HTTPS**
   - Automatic with Let's Encrypt
   - Free SSL certificate

### Environment Variables

```
Site settings → Build & deploy → Environment
Add variables if needed (currently none required)
```

### Continuous Deployment

- Auto-deploys on every push to `main`
- Preview deployments for pull requests
- Rollback to previous versions

---

## ⚡ Vercel

**Best for:** Fast global CDN, instant deployments, great DX

### One-Click Deploy

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new)

### Manual Deployment

1. **Install Vercel CLI** (optional)
   ```bash
   npm i -g vercel
   ```

2. **Deploy via Web Interface**
   - Go to [vercel.com](https://vercel.com/)
   - Click "Import Project"
   - Connect GitHub account
   - Select `nutriscan-pro` repository
   - Click "Deploy"

3. **Configuration**
   ```json
   {
     "name": "nutriscan-pro",
     "version": 2,
     "builds": [
       {
         "src": "index.html",
         "use": "@vercel/static"
       }
     ]
   }
   ```

### CLI Deployment

```bash
# From project directory
cd nutriscan-pro
vercel

# Production deployment
vercel --prod
```

### Custom Domain

1. **Add Domain**
   - Project settings → Domains
   - Add domain
   - Update DNS records

2. **DNS Configuration**
   ```
   Type: A
   Name: @
   Value: 76.76.21.21

   Type: CNAME
   Name: www
   Value: cname.vercel-dns.com
   ```

---

## 🔥 Firebase Hosting

**Best for:** Google Cloud integration, real-time features

### Setup

1. **Install Firebase CLI**
   ```bash
   npm install -g firebase-tools
   ```

2. **Login to Firebase**
   ```bash
   firebase login
   ```

3. **Initialize Project**
   ```bash
   firebase init hosting
   ```

4. **Configuration**
   ```
   ? What do you want to use as your public directory? .
   ? Configure as a single-page app? No
   ? Set up automatic builds? No
   ```

5. **Deploy**
   ```bash
   firebase deploy
   ```

### firebase.json

```json
{
  "hosting": {
    "public": ".",
    "ignore": [
      "firebase.json",
      "**/.*",
      "**/node_modules/**"
    ],
    "headers": [
      {
        "source": "**",
        "headers": [
          {
            "key": "Cache-Control",
            "value": "max-age=3600"
          }
        ]
      }
    ]
  }
}
```

### Custom Domain

```bash
firebase hosting:channel:deploy production
firebase hosting:site:list
```

---

## ☁️ AWS S3 + CloudFront

**Best for:** Enterprise, full AWS integration, scalability

### S3 Bucket Setup

1. **Create Bucket**
   ```bash
   aws s3 mb s3://nutriscan-pro
   ```

2. **Upload Files**
   ```bash
   aws s3 sync . s3://nutriscan-pro --exclude ".git/*"
   ```

3. **Enable Static Hosting**
   ```bash
   aws s3 website s3://nutriscan-pro \
     --index-document index.html \
     --error-document index.html
   ```

4. **Set Bucket Policy**
   ```json
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Sid": "PublicReadGetObject",
         "Effect": "Allow",
         "Principal": "*",
         "Action": "s3:GetObject",
         "Resource": "arn:aws:s3:::nutriscan-pro/*"
       }
     ]
   }
   ```

### CloudFront Distribution

1. **Create Distribution**
   - Origin: S3 bucket endpoint
   - Viewer Protocol Policy: Redirect HTTP to HTTPS
   - Compress Objects: Yes

2. **SSL Certificate**
   - AWS Certificate Manager
   - Request certificate for your domain
   - Add to CloudFront distribution

3. **Update DNS**
   ```
   Type: CNAME
   Name: nutriscan
   Value: d111111abcdef8.cloudfront.net
   ```

---

## 🌐 Custom Domain Setup

### General Steps

1. **Purchase Domain**
   - Namecheap, GoDaddy, Google Domains, etc.

2. **DNS Configuration**
   
   **For GitHub Pages:**
   ```
   Type: A
   Name: @
   Value: 185.199.108.153
   Value: 185.199.109.153
   Value: 185.199.110.153
   Value: 185.199.111.153

   Type: CNAME
   Name: www
   Value: your-username.github.io
   ```

   **For Netlify:**
   ```
   Type: CNAME
   Name: @
   Value: your-site.netlify.app
   ```

   **For Vercel:**
   ```
   Type: A
   Name: @
   Value: 76.76.21.21

   Type: CNAME
   Name: www
   Value: cname.vercel-dns.com
   ```

3. **Enable HTTPS**
   - Most platforms auto-provision SSL
   - Let's Encrypt (free)
   - Wait 10-30 minutes for propagation

### DNS Verification

```bash
# Check DNS propagation
dig nutriscan.yourdomain.com

# Check SSL certificate
curl -vI https://nutriscan.yourdomain.com
```

---

## ⚙️ Environment-Specific Configurations

### Production Optimizations

1. **Enable Compression**
   ```html
   <!-- Already optimized - single HTML file -->
   ```

2. **CDN Configuration**
   ```
   Cache-Control: public, max-age=31536000
   ```

3. **Analytics** (optional)
   ```html
   <!-- Add Google Analytics or Plausible -->
   <script async src="https://www.googletagmanager.com/gtag/js?id=GA_ID"></script>
   ```

### Security Headers

Add to hosting platform:

```
X-Content-Type-Options: nosniff
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block
Referrer-Policy: strict-origin-when-cross-origin
Permissions-Policy: camera=(), microphone=(), geolocation=()
```

### Performance Monitoring

**Lighthouse Score:**
```bash
# Install Lighthouse
npm install -g lighthouse

# Run audit
lighthouse https://your-site.com --view
```

**Target Scores:**
- Performance: 90+
- Accessibility: 95+
- Best Practices: 95+
- SEO: 100

---

## 🔍 Deployment Checklist

Before deploying to production:

- [ ] Test all features (AI scan, barcode, manual)
- [ ] Verify HTTPS is enabled
- [ ] Check mobile responsiveness
- [ ] Test in multiple browsers
- [ ] Validate all links in README
- [ ] Update live demo URL
- [ ] Add analytics (optional)
- [ ] Set up error monitoring (optional)
- [ ] Configure custom domain (optional)
- [ ] Enable caching headers
- [ ] Test loading speed
- [ ] Verify API calls work

---

## 📊 Monitoring & Analytics

### Google Analytics (Optional)

```html
<!-- Add before </head> -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_MEASUREMENT_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'GA_MEASUREMENT_ID');
</script>
```

### Plausible Analytics (Privacy-Friendly)

```html
<script defer data-domain="yourdomain.com" src="https://plausible.io/js/script.js"></script>
```

---

## 🐛 Common Deployment Issues

### Issue: API Not Working

**Solution:**
- Ensure HTTPS is enabled
- Check browser console for errors
- Verify API endpoint is accessible

### Issue: Camera Not Working

**Solution:**
- Must use HTTPS (not HTTP)
- Check camera permissions
- Test on different browsers

### Issue: Slow Loading

**Solution:**
- Enable CDN
- Use caching headers
- Compress assets

### Issue: 404 on Refresh

**Solution:**
- Configure single-page app routing
- Add fallback to index.html

---

## 🎯 Best Practices

1. **Always use HTTPS** - Required for camera access
2. **Enable CDN** - Faster global loading
3. **Monitor performance** - Use Lighthouse
4. **Set up alerts** - Uptime monitoring
5. **Regular updates** - Keep dependencies current
6. **Backup regularly** - Git commits
7. **Test before deploy** - Staging environment

---

## 🔗 Useful Links

- [GitHub Pages Docs](https://docs.github.com/en/pages)
- [Netlify Docs](https://docs.netlify.com/)
- [Vercel Docs](https://vercel.com/docs)
- [Firebase Hosting](https://firebase.google.com/docs/hosting)
- [AWS S3 Static Hosting](https://docs.aws.amazon.com/AmazonS3/latest/userguide/WebsiteHosting.html)

---

**Need help?** Open an issue on GitHub or check Discussions!

**Happy Deploying! 🚀**
