# Setup Instructions for ampscm/setup-subversion

## Repository Structure

Your GitHub repository should have this structure:

```
ampscm/setup-subversion/
├── action.yml          # Main action definition
├── README.md           # Documentation
├── LICENSE             # MIT License
└── .github/
    └── workflows/
        └── test.yml    # Test workflow
```

## Steps to Create the Repository

1. **Create a new repository on GitHub**
   - Go to https://github.com/ampscm
   - Click "New repository"
   - Name it `setup-subversion`
   - Make it public (required for GitHub Actions marketplace)
   - Don't initialize with README (we have our own files)

2. **Initialize and push your code**

```bash
# Clone the empty repository
git clone https://github.com/ampscm/setup-subversion.git
cd setup-subversion

# Copy the files from this guide
# (action.yml, README.md, LICENSE, and .github/workflows/test.yml)

# Add all files
git add .

# Commit
git commit -m "Initial commit: Setup Subversion action"

# Push to GitHub
git push origin main
```

3. **Create a release/tag**

```bash
# Tag version 1
git tag -a v1 -m "Version 1"
git push origin v1

# Also create v1.0.0 for semantic versioning
git tag -a v1.0.0 -m "Version 1.0.0"
git push origin v1.0.0
```

4. **Test the action**

The test workflow will automatically run on push. Check the Actions tab in your repository to see if it passes on all platforms.

## Using in Other Repositories

Once published, use it in any workflow:

```yaml
steps:
  - uses: ampscm/setup-subversion@v1
```

## Publishing to GitHub Marketplace (Optional)

1. Go to your repository on GitHub
2. Click on "Releases" → "Create a new release"
3. Choose tag `v1`
4. Check "Publish this Action to the GitHub Marketplace"
5. Fill in the required fields
6. Publish release

## Maintenance Tips

- Always test on all three platforms (Linux, macOS, Windows) before releasing
- Use semantic versioning for releases (v1.0.0, v1.1.0, etc.)
- Keep the major version tag (v1) updated to point to latest v1.x.x release
- Update README with any new features or breaking changes
