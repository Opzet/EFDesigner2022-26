# Understanding Visual Studio Marketplace Publishing Requirements

## The Confusion Explained

There are **TWO different Microsoft portals** that can be confusing when publishing Visual Studio extensions:

### 1. Visual Studio Marketplace (What You Need) ✅
- **URL:** https://marketplace.visualstudio.com/manage
- **Purpose:** Publishing Visual Studio extensions (VSIX files)
- **Simple Process:** Create publisher account, upload VSIX
- **This is the CORRECT portal for this project**

### 2. Microsoft Partner Center (NOT Needed) ❌
- **URL:** https://partner.microsoft.com/dashboard
- **Purpose:** Commercial apps, SaaS offerings, Azure Marketplace solutions
- **Complex Process:** Requires Partner Agreement, business validation, etc.
- **NOT required for simple Visual Studio extensions**

## What You Actually Need to Do

### Step 1: Sign in to Visual Studio Marketplace
1. Go to: https://marketplace.visualstudio.com/manage
2. Sign in with: **david@planworkdone.com**
3. You should see "Publish extensions" option

### Step 2: Create or Access Publisher Account
**Option A - If Publisher Already Exists:**
- If "michaelsawczyn" publisher already exists and you have access:
  - You can manage it if you're already an owner/contributor
  - Or you need the current owner to add david@planworkdone.com as a member
  
**Option B - Create New Publisher:**
- Click "Create new publisher"
- Fill in:
  - **Publisher Name:** (e.g., "Plan Work Done" or keep "Michael Sawczyn")
  - **Publisher ID:** (e.g., "planworkdone" - this goes in URLs)
  - **Description:** Optional
  - **Logo:** Optional
- Click "Create"

### Step 3: Get Personal Access Token (PAT)
1. Go to: https://dev.azure.com
2. Sign in with: **david@planworkdone.com**
3. Click your profile icon (top right) → Personal access tokens
4. Click "+ New Token"
5. Configure:
   - **Name:** GitHub Actions VSIX Publisher
   - **Organization:** All accessible organizations
   - **Expiration:** 90 days or custom
   - **Scopes:** Click "Show all scopes" → Check "Marketplace" → Select:
     - ✅ Acquire
     - ✅ Manage  
     - ✅ Publish
6. Click "Create"
7. **IMPORTANT:** Copy the token immediately (you won't see it again!)

### Step 4: Add Token to GitHub
1. Go to: https://github.com/Opzet/EFDesigner2022-26/settings/secrets/actions
2. Click "New repository secret"
3. Name: `VS_MARKETPLACE_TOKEN`
4. Value: Paste the PAT you copied
5. Click "Add secret"

## Publishing Options

### Option 1: Manual Upload (Simplest)
1. Build the VSIX locally
2. Go to https://marketplace.visualstudio.com/manage
3. Click your publisher
4. Click "New extension" → Visual Studio
5. Upload the VSIX file
6. Done!

### Option 2: Automated via GitHub Actions (Recommended)
Once you've completed Steps 1-4 above, the GitHub Actions workflow will:
- Build the VSIX automatically on releases
- Publish to marketplace automatically
- No manual upload needed

## Common Issues and Solutions

### Issue: "You don't have permission to publish"
**Solution:** Make sure david@planworkdone.com is an owner/contributor of the publisher account

### Issue: "Publisher not found"
**Solution:** Create a new publisher account at https://marketplace.visualstudio.com/manage

### Issue: "Extension already exists"
**Solutions:**
- If you own it: Update the existing extension
- If someone else owns it: Either get access or create a new extension with different ID

### Issue: Partner Center is asking for business verification
**Solution:** You're in the wrong portal! Use https://marketplace.visualstudio.com/manage instead

## Quick Decision Tree

```
Do you want to publish a Visual Studio extension (VSIX)?
├─ YES → Use Visual Studio Marketplace (marketplace.visualstudio.com)
│        ✅ Simple, quick, free
│        ✅ Just need Microsoft account
│        ✅ No business verification needed
│
└─ NO → Are you selling commercial SaaS/apps?
         └─ YES → Use Partner Center (partner.microsoft.com)
                  ⚠️ Complex setup
                  ⚠️ Business verification required
                  ⚠️ Not needed for VSIX extensions
```

## Summary: What You Don't Need

❌ Microsoft Partner Center account  
❌ Partner Agreement  
❌ Business verification  
❌ Azure AD tenant setup (unless using advanced features)  
❌ Commercial marketplace enrollment  

## Summary: What You DO Need

✅ Microsoft account (david@planworkdone.com)  
✅ Visual Studio Marketplace publisher account  
✅ Personal Access Token from Azure DevOps  
✅ GitHub secret with the PAT  

## Next Steps

1. **Verify Access:** Go to https://marketplace.visualstudio.com/manage and sign in
2. **Check Publisher:** See if you can access existing publisher or need to create new one
3. **Create PAT:** Follow Step 3 above
4. **Add to GitHub:** Follow Step 4 above
5. **Test:** Run the GitHub Actions workflow manually

## Need Help?

If you're still seeing the Partner Center and not the Marketplace manage page:
- Clear browser cache and cookies
- Try incognito/private browsing mode
- Go directly to: https://marketplace.visualstudio.com/manage/createpublisher
- Make sure you're signed in with david@planworkdone.com
