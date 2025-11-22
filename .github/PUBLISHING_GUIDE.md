# Understanding Visual Studio Marketplace Publishing Requirements

## IMPORTANT: You're in the WRONG Portal! ⚠️

If you're seeing information about:
- ❌ "Microsoft Marketplace account in Partner Center"
- ❌ "Enroll in Microsoft Marketplace program"  
- ❌ "Symantec ID"
- ❌ Windows publisher IDs like "CN=65F68A02-..."
- ❌ "Create commercial offers"

**You are in Partner Center (partner.microsoft.com), which is NOT needed for Visual Studio extensions!**

## The Confusion Explained

There are **TWO completely different Microsoft portals** with similar names:

### 1. Visual Studio Marketplace (What You Need) ✅
- **URL:** https://marketplace.visualstudio.com/manage
- **Purpose:** Publishing Visual Studio extensions (VSIX files)
- **Simple Process:** Create publisher account, upload VSIX
- **No enrollment or verification needed**
- **This is the CORRECT portal for this project**

### 2. Microsoft Partner Center (NOT Needed) ❌
- **URL:** https://partner.microsoft.com/dashboard
- **Purpose:** Commercial SaaS apps, Azure Marketplace, paid software
- **Complex Process:** Requires enrollment, business validation, tax setup
- **Shows Windows publisher IDs, Symantec IDs, etc.**
- **NOT required for Visual Studio extensions**

## Your Existing Account Information

You've already completed the Partner Center enrollment (which you didn't actually need). Here's what you have:

### Partner Center IDs (Not Used for VSIX Publishing)
- Windows publisher ID: `CN=65F68A02-BF88-44FB-85D4-D43E48BC8A99`
- Windows phone publisher ID: `9811ce19-bc53-4ee5-adfa-d95d0dcf9a7f`
- Publisher name: PWD
- Seller ID: 89221360

**Note:** These IDs are for Windows Store apps and commercial marketplace offers, NOT for Visual Studio extensions.

### What You Actually Use for VSIX Publishing
- Just your Microsoft account: david@planworkdone.com
- Simple publisher profile at marketplace.visualstudio.com
- No special IDs or enrollment needed

## What You Actually Need to Do

### Step 1: Go to the CORRECT Portal
1. **Close Partner Center** - you don't need it
2. Go to: **https://marketplace.visualstudio.com/manage**
3. Sign in with: **david@planworkdone.com**

### Step 2: Create or Access Publisher Profile (Simple!)
**Option A - If Publisher Profile Already Exists:**
- You may already have a publisher profile from the Partner Center setup
- Look for "PWD" or similar in the publisher list
- If you see it, you're done with this step!
  
**Option B - Create New Publisher Profile:**
- Click "Create new publisher"
- Fill in:
  - **Publisher Name:** PWD (or any name you want)
  - **Publisher ID:** pwd (lowercase, for URLs)
  - **Email:** david@planworkdone.com
  - **Description:** Optional
- Click "Create"
- **That's it! No enrollment, no verification, no waiting**

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

❌ Microsoft Partner Center account (you already have one but won't use it)
❌ Partner Agreement or enrollment  
❌ Business verification  
❌ Azure AD tenant setup (unless using advanced features)  
❌ Commercial marketplace enrollment  
❌ Windows publisher ID (CN=65F68A02-...)
❌ Symantec ID
❌ Seller ID (89221360)

These are all for Windows Store apps and commercial marketplace offers, NOT for Visual Studio extensions!

## Summary: What You DO Need

✅ Microsoft account (david@planworkdone.com) ← You already have this!
✅ Visual Studio Marketplace publisher profile ← Simple, 2-minute setup
✅ Personal Access Token from Azure DevOps ← For automation only
✅ GitHub secret with the PAT ← For automation only  

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
