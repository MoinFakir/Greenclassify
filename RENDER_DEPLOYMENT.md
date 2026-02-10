# Deploy to Render - Step by Step Guide

## Prerequisites
- GitHub account
- Render account (free tier available)
- Project code pushed to GitHub repository

## Deployment Steps

### 1. Prepare Your Repository

**Option A: If you don't have a Git repository yet:**
```bash
# Initialize git repository
git init

# Add all files
git add .

# Commit
git commit -m "Initial commit - Vegetable Classifier"

# Create a GitHub repository and push
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
git branch -M main
git push -u origin main
```

**Option B: If you already have a repository:**
```bash
# Add the new deployment files
git add requirements.txt render.yaml .python-version RENDER_DEPLOYMENT.md

# Commit changes
git commit -m "Add Render deployment configuration"

# Push to GitHub
git push
```

### 2. Deploy on Render

1. **Go to Render Dashboard**
   - Visit: https://render.com/
   - Sign up or log in with your GitHub account

2. **Create New Web Service**
   - Click "New +" button
   - Select "Web Service"
   - Connect your GitHub repository
   - Select your vegetable classifier repository

3. **Configure Service** (Auto-detected from render.yaml)
   - **Name**: vegetable-classifier (or your preferred name)
   - **Region**: Oregon (Free) or any region you prefer
   - **Branch**: main
   - **Runtime**: Python 3
   - **Build Command**: `pip install --upgrade pip && pip install -r requirements.txt`
   - **Start Command**: `gunicorn app:app`

4. **Environment Variables** (Optional)
   - Add any additional environment variables if needed
   - `FLASK_ENV=production` (already in render.yaml)

5. **Select Plan**
   - Choose **Free** tier to start (limitations apply)
   - Or select a paid plan for better performance

6. **Deploy**
   - Click "Create Web Service"
   - Wait for deployment (usually 5-10 minutes)
   - Render will install dependencies and start your app

### 3. Access Your Application

Once deployed, Render will provide you with a URL like:
```
https://vegetable-classifier.onrender.com
```

### 4. Important Notes

**Free Tier Limitations:**
- Service spins down after 15 minutes of inactivity
- First request after downtime may take 30-60 seconds (cold start)
- 750 hours/month of runtime
- Limited memory (512 MB)

**Model File Size:**
- Ensure `vegetable_model_best.keras` is included in your repository
- Large files (>100MB) may need Git LFS (Large File Storage)

**Add Git LFS for Large Files:**
```bash
# Install Git LFS
git lfs install

# Track Keras model files
git lfs track "*.keras"
git lfs track "*.h5"

# Add and commit
git add .gitattributes
git add vegetable_model_best.keras
git commit -m "Add model with Git LFS"
git push
```

### 5. Monitoring & Logs

- **View Logs**: Render Dashboard → Your Service → Logs
- **Monitor Health**: Visit `https://your-app.onrender.com/health`
- **Metrics**: Available in Render Dashboard

### 6. Custom Domain (Optional)

1. Go to Render Dashboard → Your Service → Settings
2. Scroll to "Custom Domain"
3. Add your domain and configure DNS settings

### 7. Troubleshooting

**If deployment fails:**
- Check logs in Render Dashboard
- Verify `requirements.txt` has all dependencies
- Ensure Python version is compatible (3.12)
- Check model file is present and accessible

**If app is slow:**
- Free tier has cold starts (expected behavior)
- Upgrade to paid plan for always-on service
- Optimize model loading and image preprocessing

**Memory issues:**
- TensorFlow models can be large
- Consider using a lite model or upgrading plan
- Monitor memory usage in Render metrics

## Alternative Deployment (Manual Configuration)

If `render.yaml` doesn't auto-configure:

1. **Build Command:**
   ```
   pip install --upgrade pip && pip install -r requirements.txt
   ```

2. **Start Command:**
   ```
   gunicorn app:app
   ```

3. **Environment Variables:**
   - `PYTHON_VERSION`: 3.12.0
   - `FLASK_ENV`: production

## Support

- Render Docs: https://render.com/docs
- Render Community: https://community.render.com/
- GitHub Issues: (Your repository issues page)

## Success Checklist

- [ ] Repository pushed to GitHub
- [ ] All files including model committed
- [ ] Render account created
- [ ] Web service created and connected
- [ ] Deployment successful (check logs)
- [ ] App accessible via Render URL
- [ ] Health endpoint working
- [ ] Test image upload and prediction

---

**Your vegetable classifier is now live on Render! 🎉**
