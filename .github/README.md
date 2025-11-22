# GitHub Actions & Publishing Configuration

This directory contains the GitHub Actions workflows and configuration files for automated building and publishing of the EF Designer VSIX extension to the Visual Studio Marketplace.

## ⚠️ IMPORTANT: Are You in Partner Center Right Now?

**If you're seeing pages about:**
- Payee profiles / Payment setup
- Tax forms
- Payout accounts  
- Windows publisher IDs like "CN=65F68A02-..."
- Symantec IDs
- Account enrollment

👉 **[READ THIS NOW: STOP_PARTNER_CENTER.md](STOP_PARTNER_CENTER.md)** 👈

**You're in the wrong portal! Partner Center is NOT needed for Visual Studio extensions!**

---

## 🚀 Quick Start

### **NEW TO VSIX PUBLISHING? START HERE:**
👉 **[QUICK_START.md](QUICK_START.md)** - Simple step-by-step guide (5 minutes)

### Confused about Partner Center vs. Marketplace?
👉 **[PUBLISHING_GUIDE.md](PUBLISHING_GUIDE.md)** - Clears up the confusion  
👉 **[STOP_PARTNER_CENTER.md](STOP_PARTNER_CENTER.md)** - Get out of Partner Center!

### Need Your Account Details?
👉 **[ACCOUNT_SETUP.md](ACCOUNT_SETUP.md)** - Your verified publisher information

### Ready for Detailed Instructions?
👉 **[MARKETPLACE_PUBLISHING.md](MARKETPLACE_PUBLISHING.md)** - Complete documentation

---

## For First-Time Setup
1. **FIRST:** Make sure you're at marketplace.visualstudio.com (NOT partner.microsoft.com)
2. Read **[QUICK_START.md](QUICK_START.md)** (most important - avoids confusion!)
3. Follow the 5 simple steps
4. Done! 

## Already Set Up?
Just create a GitHub release and the extension will automatically publish to the marketplace!

## Files in This Directory

### Workflows
- **`workflows/build.yml`** - Builds VSIX on every push/PR for validation
- **`workflows/publish-marketplace.yml`** - Publishes VSIX to VS Marketplace on releases

### Configuration
- **`publish-manifest.json`** - Marketplace publishing configuration (publisher: PWD)

### Documentation
- **`PUBLISHING_GUIDE.md`** - Explains the difference between Partner Center and Marketplace (read this first!)
- **`ACCOUNT_SETUP.md`** - Your verified publisher account information
- **`MARKETPLACE_PUBLISHING.md`** - Detailed setup and usage instructions

## Current Status

✅ **Workflows Created**
- Build workflow configured and tested
- Publish workflow configured and ready

✅ **Publisher Configured**
- Publisher: PWD
- Account: david@planworkdone.com
- Status: Active

⏳ **Pending Action Required**
- Create Personal Access Token (PAT) at https://dev.azure.com
- Add PAT to GitHub repository secrets as `VS_MARKETPLACE_TOKEN`

## How to Publish a New Version

### Method 1: Automatic (Recommended)
1. Update version number in `src/DslPackage/source.extension.vsixmanifest`
2. Commit and push changes
3. Create a new GitHub release (e.g., tag `v4.2.9`)
4. Workflow automatically builds and publishes to marketplace

### Method 2: Manual Trigger
1. Go to Actions → "Publish to VS Marketplace"
2. Click "Run workflow"
3. Select branch and click "Run workflow"

## Troubleshooting

See [MARKETPLACE_PUBLISHING.md](MARKETPLACE_PUBLISHING.md) for common issues and solutions.

## Security Notes

- Never commit the Personal Access Token to the repository
- Token is stored securely in GitHub Secrets
- Rotate the token periodically (every 90 days recommended)
