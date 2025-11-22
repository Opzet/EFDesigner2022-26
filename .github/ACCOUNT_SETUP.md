# Publisher Account Details

## Verified Account Information

Your Visual Studio Marketplace publisher account is already set up with the following details:

### Account Information
- **Account Type:** Individual
- **Account Status:** Active ✅
- **Microsoft Account:** david@planworkdone.com

### Publisher IDs
- **Publisher Name:** PWD
- **Windows Publisher ID:** PWD
- **Seller ID:** 89221360
- **Windows Phone Publisher ID:** 9811ce19-bc53-4ee5-adfa-d95d0dcf9a7f

### Contact Information
- **Name:** David Veerman
- **Email:** david@planworkdone.com
- **Phone:** +61 0 0402349503
- **Address:** 1 Bell Street, Canning Vale, Western Australia, 6155, Australia

## What This Means for Publishing

### ✅ Good News
Your publisher account is **already active and ready** to publish Visual Studio extensions!

### Configuration Summary
The GitHub Actions workflows have been configured to use:
- **Publisher ID:** `PWD`
- **Repository:** https://github.com/Opzet/EFDesigner2022-26

## Next Steps to Enable Automated Publishing

### 1. Create Personal Access Token (PAT)
Since your account is active, you just need to create a PAT for automated publishing:

1. Go to: https://dev.azure.com
2. Sign in with: **david@planworkdone.com**
3. Click your profile icon (top right) → **Personal access tokens**
4. Click **"+ New Token"**
5. Configure the token:
   - **Name:** `GitHub Actions VSIX Publisher`
   - **Organization:** All accessible organizations
   - **Expiration:** Choose duration (recommended: 90 days or custom)
   - **Scopes:** Click "Show all scopes" and find **Marketplace**
     - ✅ Check **Acquire**
     - ✅ Check **Manage**
     - ✅ Check **Publish**
6. Click **"Create"**
7. **CRITICAL:** Copy the token immediately! You won't be able to see it again.

### 2. Add PAT to GitHub Repository
1. Go to: https://github.com/Opzet/EFDesigner2022-26/settings/secrets/actions
2. Click **"New repository secret"**
3. Enter:
   - **Name:** `VS_MARKETPLACE_TOKEN`
   - **Secret:** Paste the PAT you just copied
4. Click **"Add secret"**

### 3. Test the Workflow
Once the secret is added, you can test the publishing workflow:

**Option A - Manual Test:**
1. Go to: https://github.com/Opzet/EFDesigner2022-26/actions/workflows/publish-marketplace.yml
2. Click **"Run workflow"**
3. Select branch and click **"Run workflow"**

**Option B - Create a Release:**
1. Update version in `src/DslPackage/source.extension.vsixmanifest`
2. Commit and push changes
3. Create a GitHub release with a new tag (e.g., `v4.2.9`)
4. The workflow will automatically build and publish

## Publishing Options

### Option 1: Publish as New Extension
If you want to publish this as a **new extension** (separate from the original):
- The extension will appear under publisher "PWD"
- You'll need a unique extension ID
- Users will see it as a different extension

### Option 2: Take Over Existing Extension
If you want to **update the existing extension** (currently under "Michael Sawczyn"):
- You need to either:
  - Get access to the "michaelsawczyn" publisher account, OR
  - Have the current owner transfer the extension to your "PWD" publisher

### Recommendation
For a **fresh start** with your own branding, publish as a new extension under "PWD". The workflows are already configured for this.

## Files Updated

The following files have been configured with your publisher information:

- `.github/publish-manifest.json` - Publisher set to "PWD"
- `.github/workflows/publish-marketplace.yml` - Automated publishing workflow
- `.github/workflows/build.yml` - Automated build workflow

## Important Notes

### VSIX Manifest Publisher
The VSIX manifest file currently has:
```xml
Publisher="Michael Sawczyn"
```

**Decision Required:**
- **Keep it:** The extension shows "Michael Sawczyn" as author in VS
- **Change it:** Update to "PWD" or "David Veerman" for your branding

To change, edit: `src/DslPackage/source.extension.vsixmanifest` line 4

### Extension Identity
Current extension ID in VSIX manifest:
```xml
Id="dd1c2ec0-b732-4b74-a591-4d78684bb231"
```

**Decision Required:**
- **Keep it:** If taking over the existing extension
- **Change it:** If creating a new extension (generate new GUID)

## Security Checklist

- ✅ Account is active and verified
- ✅ Publisher ID (PWD) is configured in workflows
- ⏳ Need to create PAT with Marketplace permissions
- ⏳ Need to add PAT to GitHub secrets as `VS_MARKETPLACE_TOKEN`
- ⏳ Decide on extension identity (new vs. takeover)
- ⏳ Update VSIX manifest if needed

## Support

If you encounter any issues:
1. Verify your account at: https://marketplace.visualstudio.com/manage
2. Check your publisher "PWD" is listed
3. Ensure PAT has correct Marketplace permissions
4. Verify GitHub secret is named exactly `VS_MARKETPLACE_TOKEN`

## Current Status

✅ Publisher account exists and is active  
✅ GitHub workflows created and configured  
✅ Publisher manifest updated with your details  
⏳ Waiting for PAT to be created and added to GitHub  
⏳ Waiting for decision on extension identity  
