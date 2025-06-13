# GitLab Pages Deployment Instructions

## Quick Deploy

1. Create a new GitLab project named "VIM"
2. Extract this bundle to your local machine
3. Initialize git and push to GitLab:

```bash
cd gitlab-pages
git init
git add .
git commit -m "Initial VIM deployment"
git remote add origin https://gitlab.com/YOUR_USERNAME/VIM.git
git push -u origin main
```

4. Enable GitLab Pages:
   - Go to Settings → Pages
   - Set deployment source to "GitLab CI/CD"
   
5. Create `.gitlab-ci.yml` file with this content:

```yaml
pages:
  stage: deploy
  script:
    - mkdir .public
    - cp -r * .public
    - mv .public public
  artifacts:
    paths:
      - public
  only:
    - main
```

6. Commit and push:

```bash
git add .gitlab-ci.yml
git commit -m "Add GitLab CI configuration"
git push
```

7. Your site will be available at: `https://YOUR_USERNAME.gitlab.io/VIM/`

## Features

- ✅ 100% offline capable
- ✅ No external dependencies
- ✅ Full VIM experience with vim.wasm
- ✅ Automatic fallback to Monaco editor if needed
- ✅ All assets self-contained

## Browser Support

The application works in all modern browsers. Check the console logs to see which editor mode is active.

For best experience with vim.wasm, enable SharedArrayBuffer in your browser if prompted.
