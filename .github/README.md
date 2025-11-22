# GitHub Actions & Publishing Configuration

This directory contains the GitHub Actions workflows and configuration files for automated building and publishing of the EF Designer VSIX extension to the Visual Studio Marketplace.

## Quick Start

### For First-Time Setup
1. Read **[PUBLISHING_GUIDE.md](PUBLISHING_GUIDE.md)** - Clears up confusion about Partner Center vs. Marketplace
2. Read **[ACCOUNT_SETUP.md](ACCOUNT_SETUP.md)** - Your verified publisher account details
3. Follow **[MARKETPLACE_PUBLISHING.md](MARKETPLACE_PUBLISHING.md)** - Complete setup instructions

### Already Set Up?
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
