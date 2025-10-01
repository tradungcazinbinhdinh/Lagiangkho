# Deploy site to GitHub Pages

This repository contains a static site under the `template/` folder. The included GitHub Actions workflow publishes `template/` to GitHub Pages whenever you push to the `main` branch.

Quick steps (PowerShell / pwsh on Windows):

1. Initialize git (if you haven't already) and make the first commit:

```powershell
cd 'F:\tradungcazinbinhdinh'
git init
git checkout -b main
git add .
git commit -m "Initial commit"
```

2. Create a GitHub repository (on github.com) and copy the repository URL, then push:

```powershell
git remote add origin https://github.com/<your-username>/<your-repo>.git
git push -u origin main
```

3. Wait for GitHub Actions to run. The workflow will publish the `template/` folder to the `gh-pages` branch and enable Pages.

4. Check Pages status: go to your repository Settings -> Pages. The site should be published at `https://<your-username>.github.io/<your-repo>/`.

Notes:
- The Actions workflow runs on every push to `main`.
- If you want to publish from a different branch, edit `.github/workflows/deploy.yml`.

If your Pages site will be served at a repository subpath (for example `https://<your-username>.github.io/<your-repo>/`), you usually don't need to change anything because this project uses relative paths for assets. If you prefer an explicit base tag, add this inside the `<head>` of `template/index.html` and replace `<your-repo>`:

```html
<base href="/ <your-username> / <your-repo> /">
```

But keep the spaces removed and ensure the trailing slash is present, e.g. `/alice/my-site/`.
