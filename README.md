# demog280-fa2025

This repo has the syllabus for Demog 280.

It uses Github Actions to update my personal website with a copy of the latest version of the syllabus every time an update is pushed to this repo.  It does this by running quarto to render the syllabus, and then copying all of the resulting files to `docs/teaching/2025fa_demog280/` in my personal website repo. It also copies the files to `/teaching/2025fa_demog280/`, which ensures that any rebuild of my personal website will still include the files from this syllabus.

 You can see the configuration file for the github action in <.github/workflows/deploy-to-main-site.yml>. 

### Adding a personal access token

In order to add my personal access token to this repository, I followed these instructions (from Claude Sonnet 4):

> Here's the detailed step-by-step setup:
> Step 1: Create a Personal Access Token (PAT)
> 
> Go to GitHub.com and click your profile picture → Settings
> Scroll down to Developer settings (bottom of left sidebar)
> Click "Personal access tokens" → "Tokens (classic)"
> Click "Generate new token" → "Generate new token (classic)"
> Configure the token:
> 
> Note: Something like "Course website deployment"
> Expiration: I recommend "No expiration" for simplicity, or 1 year
> Scopes: Check the repo box (this gives full repository access)
> 
> Click "Generate token"
> Copy the token immediately - you won't be able to see it again!
> 
> Step 2: Add the Token as a Secret in Your Class Repository
> 
> Go to your class repository on GitHub
> Click the "Settings" tab (in the repository, not your profile)
> In the left sidebar, click "Secrets and variables" → "Actions"
> Click "New repository secret"
> Fill in:
> 
> Name: PERSONAL_ACCESS_TOKEN (exactly as shown)
> Secret: Paste the token you copied from Step 1
> 
> Click "Add secret"




