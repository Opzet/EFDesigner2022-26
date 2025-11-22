# Quick Start: Publishing Your First VSIX

## Stop! Are you in the right place?

### ❌ WRONG - You're in Partner Center if you see:
```
partner.microsoft.com/dashboard
- Account settings
- Legal info  
- Identifiers
- Windows publisher ID: CN=65F68A02-...
- Symantec ID
- Enroll in Microsoft Marketplace program
```
**→ Close this and go to Step 1 below**

### ✅ CORRECT - You're in the right place if you see:
```
marketplace.visualstudio.com/manage
- Publish extensions
- Publisher profiles
- Extensions list
- Upload new extension
```
**→ Continue with Step 2 below**

---

## Step-by-Step Guide

### Step 1: Go to Visual Studio Marketplace
```
1. Open browser
2. Go to: https://marketplace.visualstudio.com/manage
3. Sign in with: david@planworkdone.com
4. You should see "Publish extensions" button
```

### Step 2: Create Publisher Profile (if needed)
```
1. Look for existing publisher profiles
2. If "PWD" exists → Skip to Step 3
3. If no publisher exists:
   - Click "Create publisher"
   - Publisher name: PWD
   - Publisher ID: pwd
   - Email: david@planworkdone.com
   - Click "Create"
```

### Step 3: Get Your Personal Access Token (PAT)
```
1. Go to: https://dev.azure.com
2. Sign in with: david@planworkdone.com
3. Click your profile icon (top right)
4. Click "Personal access tokens"
5. Click "+ New Token"
6. Settings:
   Name: GitHub Actions VSIX Publisher
   Organization: All accessible organizations
   Expiration: 90 days (or custom)
   Scopes: 
     ☐ Full access (NO - uncheck this)
     ☑ Marketplace → Acquire
     ☑ Marketplace → Manage
     ☑ Marketplace → Publish
7. Click "Create"
8. COPY THE TOKEN NOW! (You won't see it again)
```

### Step 4: Add Token to GitHub
```
1. Go to: https://github.com/Opzet/EFDesigner2022-26/settings/secrets/actions
2. Click "New repository secret"
3. Name: VS_MARKETPLACE_TOKEN
4. Value: [paste the token you copied]
5. Click "Add secret"
```

### Step 5: Test the Setup
```
Option A - Manual Upload (Test immediately):
1. Go to https://marketplace.visualstudio.com/manage
2. Click your publisher (PWD)
3. Click "New extension" → Visual Studio
4. Upload: dist/Sawczyn.EFDesigner.EFModel.DslPackage.vsix
5. Fill in details and publish

Option B - Automated via GitHub (Test workflow):
1. Go to: https://github.com/Opzet/EFDesigner2022-26/actions
2. Click "Publish to VS Marketplace"
3. Click "Run workflow"
4. Select branch: copilot/publish-vsix-to-marketplace
5. Click "Run workflow"
6. Wait for completion
7. Check marketplace.visualstudio.com/manage
```

---

## Troubleshooting

### "I don't see Publish extensions button"
→ You're probably in Partner Center. Go to https://marketplace.visualstudio.com/manage

### "It's asking me to enroll in a program"
→ You're in Partner Center. Go to https://marketplace.visualstudio.com/manage

### "I see Symantec ID and Windows publisher ID"
→ You're in Partner Center. Go to https://marketplace.visualstudio.com/manage

### "Personal access token not working"
→ Make sure you selected Marketplace scopes (Acquire, Manage, Publish)

### "Extension already exists"
→ Either update the existing extension or create a new one with different ID

---

## Success Checklist

- [ ] Signed in to marketplace.visualstudio.com (NOT partner.microsoft.com)
- [ ] Created or found publisher profile "PWD"
- [ ] Created Personal Access Token with Marketplace permissions
- [ ] Added token to GitHub secrets as VS_MARKETPLACE_TOKEN
- [ ] Tested manual upload OR automated workflow
- [ ] Extension appears on marketplace

---

## What Each Portal Does

| Feature | Partner Center | VS Marketplace |
|---------|---------------|----------------|
| **URL** | partner.microsoft.com | marketplace.visualstudio.com |
| **For** | Commercial apps, SaaS | VS extensions (VSIX) |
| **Setup** | Complex, enrollment needed | Simple, instant |
| **Cost** | May require fees | Free |
| **IDs** | Windows ID, Symantec ID, Seller ID | Just publisher name |
| **Use for VSIX?** | ❌ NO | ✅ YES |

---

## Summary

1. **Ignore Partner Center** (partner.microsoft.com) - you don't need it
2. **Use VS Marketplace** (marketplace.visualstudio.com/manage)
3. **Simple process:** Sign in → Create publisher → Upload VSIX
4. **That's it!** No enrollment, no verification, no waiting
