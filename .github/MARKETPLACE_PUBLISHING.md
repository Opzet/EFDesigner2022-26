# Publishing to Visual Studio Marketplace via GitHub Actions

This repository includes automated CI/CD workflows to build and publish the EF Designer VSIX extension to the Visual Studio Marketplace.

## Workflows

### 1. Build VSIX (`build.yml`)

**Triggers:**
- Push to main/master/develop branches
- Pull requests to main/master/develop branches
- Manual trigger via workflow_dispatch

**What it does:**
- Builds the VSIX extension from source
- Uploads the built VSIX as a GitHub Actions artifact
- Useful for testing and validation before publishing

### 2. Publish to VS Marketplace (`publish-marketplace.yml`)

**Triggers:**
- When a new GitHub release is published
- Manual trigger via workflow_dispatch

**What it does:**
- Builds the VSIX (if not provided)
- Publishes the extension to the Visual Studio Marketplace
- Updates the existing extension listing

## Setup Instructions

### Publisher Account - Already Configured! ✅

Your publisher account is already set up:
- **Publisher Name:** PWD
- **Account:** david@planworkdone.com
- **Status:** Active
- **Account Type:** Individual

See `.github/ACCOUNT_SETUP.md` for complete account details.

### What You Still Need to Do

#### 1. Create Personal Access Token (PAT)

**Important:** Create the PAT while signed in with david@planworkdone.com

Steps to create PAT:
     1. Sign in to https://dev.azure.com with david@planworkdone.com
     2. Click on your profile → Security → Personal Access Tokens
     3. Click "New Token"
     4. Name: `GitHub Actions VSIX Publisher`
     5. Organization: `All accessible organizations`
     6. Expiration: Choose appropriate duration (e.g., 90 days, 1 year)
     7. Scopes: Select **Marketplace** → Check **Acquire**, **Manage**, and **Publish**
     8. Click "Create"
     9. **Copy the token immediately** (you won't be able to see it again)

#### 2. Add PAT to GitHub Repository

   - Go to your repository → Settings → Secrets and variables → Actions
   - Click "New repository secret"
   - Name: `VS_MARKETPLACE_TOKEN`
   - Value: Paste your PAT
   - Click "Add secret"

#### 3. Update Publish Manifest (Optional)

   - The manifest is already configured with publisher "PWD"
   - Edit `.github/publish-manifest.json` if you need to change categories or other settings

### Publishing a New Version

#### Method 1: Automatic Publishing via GitHub Release

1. Update the version number in `src/DslPackage/source.extension.vsixmanifest`
2. Commit and push your changes
3. Create a new GitHub release:
   - Go to your repository → Releases → Draft a new release
   - Create a new tag (e.g., `v4.2.9`)
   - Add release notes
   - Click "Publish release"
4. The workflow will automatically build and publish to the marketplace

#### Method 2: Manual Publishing

1. Go to Actions → "Publish to VS Marketplace"
2. Click "Run workflow"
3. Choose the branch
4. (Optional) Specify a VSIX file path if you want to use a pre-built VSIX
5. Click "Run workflow"

## Workflow Files

- `.github/workflows/build.yml` - Builds the VSIX on every push/PR
- `.github/workflows/publish-marketplace.yml` - Publishes to marketplace
- `.github/publish-manifest.json` - Marketplace publishing configuration

## Troubleshooting

### Build Failures

- Ensure all NuGet packages can be restored
- Check that MSBuild can find all required SDKs
- Verify the solution file path is correct

### Publishing Failures

- **Authentication Error**: Check that your PAT is valid and has the correct permissions
- **Version Already Exists**: You cannot publish the same version twice. Increment the version number in the VSIX manifest
- **Manifest Errors**: Ensure the publish manifest JSON is valid and contains required fields

### Getting the PAT

If you need to regenerate the PAT:
1. Sign in to https://dev.azure.com with david@planworkdone.com
2. Profile → Security → Personal Access Tokens
3. Revoke the old token (if it exists)
4. Create a new token with Marketplace permissions
5. Update the GitHub secret

### Publisher Account Information

- **Microsoft Account:** david@planworkdone.com
- **Publisher Name:** The publisher name in the VSIX manifest (currently "Michael Sawczyn") can be kept as-is or updated
- **Publisher ID:** The internal publisher ID used in the marketplace (e.g., "michaelsawczyn" or create a new one)
- **Note:** The publisher account owner (david@planworkdone.com) controls who can publish updates to the extension

## Security Notes

- **Never commit your PAT** to the repository
- Store the PAT only in GitHub Secrets
- Rotate your PAT periodically for security
- Use the minimum required permissions (Marketplace: Acquire, Manage, Publish)

## References

- [Visual Studio Marketplace Publisher Portal](https://marketplace.visualstudio.com/manage)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [VSIX Publisher Action](https://github.com/cezarypiatek/VsixPublisherAction)
