# How to Push This Project to GitHub

Follow these step-by-step instructions to upload your land cover classification project to GitHub.

## Prerequisites

1. **Install Git** (if not already installed)
   - Windows: Download from https://git-scm.com/download/win
   - Mac: Run `git --version` in terminal (macOS will prompt to install if needed)
   - Linux: `sudo apt-get install git` (Ubuntu/Debian) or `sudo yum install git` (CentOS/Fedora)

2. **Create a GitHub Account**
   - Go to https://github.com and sign up if you don't have an account

## Step 1: Configure Git (First Time Only)

Open terminal/command prompt and run:

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

## Step 2: Create a New Repository on GitHub

1. Go to https://github.com
2. Click the **"+"** icon in the top right corner
3. Select **"New repository"**
4. Fill in the details:
   - **Repository name**: `land-cover-classification` (or your preferred name)
   - **Description**: "Machine learning project for satellite image land cover classification"
   - **Visibility**: Choose Public or Private
   - **DO NOT** initialize with README, .gitignore, or license (we already have these)
5. Click **"Create repository"**

## Step 3: Prepare Your Local Project

Navigate to your project folder in terminal:

```bash
cd /path/to/your/project
```

## Step 4: Initialize Git Repository

```bash
git init
```

This creates a new Git repository in your current directory.

## Step 5: Add Your Files

```bash
# Add all project files
git add ml.ipynb README.md .gitignore

# Or add everything at once
git add .
```

## Step 6: Create Your First Commit

```bash
git commit -m "Initial commit: Land cover classification project"
```

## Step 7: Connect to GitHub Repository

Replace `yourusername` with your actual GitHub username:

```bash
git remote add origin https://github.com/yourusername/land-cover-classification.git
```

## Step 8: Rename Branch to 'main' (if needed)

```bash
git branch -M main
```

## Step 9: Push to GitHub

```bash
git push -u origin main
```

If prompted, enter your GitHub credentials:
- **Username**: Your GitHub username
- **Password**: Your Personal Access Token (see below if you don't have one)

### Creating a Personal Access Token (if needed)

GitHub no longer accepts passwords for Git operations. You need a Personal Access Token:

1. Go to https://github.com/settings/tokens
2. Click **"Generate new token"** → **"Generate new token (classic)"**
3. Give it a name (e.g., "Git Operations")
4. Select scopes: Check **"repo"** (full control of private repositories)
5. Click **"Generate token"**
6. **Copy the token immediately** (you won't see it again!)
7. Use this token as your password when pushing

## Step 10: Verify Upload

1. Go to your GitHub repository URL
2. Refresh the page
3. You should see your files uploaded!

## Common Issues & Solutions

### Issue: "Permission denied"
**Solution**: Check your credentials or create a Personal Access Token

### Issue: "Repository not found"
**Solution**: Verify the repository URL and ensure it exists on GitHub

### Issue: "Updates were rejected"
**Solution**: Pull first with `git pull origin main --rebase` then push again

### Issue: "Large files"
**Solution**: The .gitignore already excludes large files. If you need to track large files, consider Git LFS

## Making Future Updates

After making changes to your project:

```bash
# Check what changed
git status

# Add changed files
git add .

# Commit with a message
git commit -m "Description of changes"

# Push to GitHub
git push
```

## Useful Git Commands

```bash
# View commit history
git log

# Check status of files
git status

# View differences
git diff

# Create a new branch
git checkout -b feature-name

# Switch branches
git checkout main

# View remote repositories
git remote -v

# Pull latest changes
git pull origin main
```

## Best Practices

1. **Commit Often**: Make small, logical commits with clear messages
2. **Descriptive Messages**: Write meaningful commit messages
   - Good: "Add feature importance visualization"
   - Bad: "update", "fix", "changes"
3. **Use .gitignore**: Don't commit large datasets or model files
4. **Branch Strategy**: Use branches for new features
5. **README**: Keep your README updated with project changes

## Project Structure on GitHub

After pushing, your repository should look like:

```
land-cover-classification/
├── ml.ipynb          # Your Jupyter notebook
├── README.md         # Project documentation
└── .gitignore        # Files to ignore
```

## Adding a License (Optional)

1. Go to your repository on GitHub
2. Click **"Add file"** → **"Create new file"**
3. Type `LICENSE` as the filename
4. Click **"Choose a license template"**
5. Select MIT License (or your preference)
6. Commit the file

## Next Steps

- Add badges to your README (build status, license, etc.)
- Create Issues for future improvements
- Add a Contributing guide
- Set up GitHub Actions for CI/CD
- Add example outputs or screenshots
- Create a wiki for detailed documentation

## Need Help?

- GitHub Documentation: https://docs.github.com
- Git Documentation: https://git-scm.com/doc
- GitHub Support: https://support.github.com

---

**Congratulations!** 🎉 Your project is now on GitHub and ready to share with the world!
